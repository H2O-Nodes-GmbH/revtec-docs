# Protocol Design

## The Objective

The objective of the protocol is to give the staker a choice between earning the “real economic value” (REV) of Solana’s transaction fees, or the inflationary issuance of new SOL tokens. Standard staking yield combines both, and RevTec aims to separate them, and allow users to earn them with much higher capital efficiency. To achieve this, RevTec creates two liquid staking tokens (LSTs): revSOL earns REV from transaction fees, while issSOL earns the issuance of new SOL.&#x20;

RevTec LSTs closely mimic existing staking token designs. This means that the tokens are valued 1-to-1 with SOL at the protocol’s launch, and gain value over time as yield is accumulated. (As a user, you hold a constant balance of the token, and you’re entitled to more underlying SOL the longer you hold the token for.) This is the same well-understood user experience as other LSTs on Solana, and allows for simple DeFi integrations.

## Rewards & Fees

RevTec is basically an accounting system, tracking the staking yield earned from real economic value (REV) and issuance. At launch, the [RevTec validator](https://stakewiz.com/validator/B1rsc6jv3RsFpkak8qvJN3PfGYSg9E3Uw1joaV1EoiFj) is the [only validator](https://www.solsharing.com/) sharing all priority fees and Jito tips via the Jito Tip Router. As such, all stake flowing into the RevTec protocol will be staked with the RevTec validator.&#x20;

Issuance yield is automatically accumulated and compounded at the end of each epoch by Solana's native stake program, within the validator’s stake account. The RevTec protocol takes a snapshot, and compares with the previous epoch’s snapshot to calculate the issuance yield rate.&#x20;

REV yield (Jito tips and priority fees) is routed by the [Jito Tip Router](https://www.jito.network/blog/tiprouter-upgrade-facilitating-priority-fees/) into RevTec’s yield treasury account, where it is staked and tracked every epoch.&#x20;

The RevTec protocol incurs no fees beyond the standard Solana transaction fees. However, fees do apply at the validator level. Jito takes a fee of 1.5% on shared priority fees, and a 3% fee on Jito Tips. The RevTec validator takes a 10% fee on issuance rewards, in order to fund further development of the protocol. These fees may be revisited after mainnet launch.

## Initializing the Protocol

Over time, the cumulative REV and issuance rewards grow, and the ratio between them is tracked by the protocol. At the beginning of the protocol’s life, before any rewards have been produced, the ratio is manually initialized according to the breakdown of Solana’s average staking rewards at that moment in time. (For example, if standard staking yield is yielding 5% APY, of which 1% comes from REV and 4% comes from issuance, then we initialize the ratio as 1:4 of REV-to-issuance rewards.)

Using that ratio, an initial amount of staked SOL mints the initial supply or revSOL and issSOL, ensuring they are backed 1:1 with SOL. (For example, we might stake 100 SOL and mint 20 revSOL and 80 issSOL, using the 1:4 ratio) As the REV and issuance rewards come in, at different rates, the backing of the tokens increases at different rates, giving each a unique “APY”.&#x20;

## Mints and redeems, via the REV/Issuance Ratio

Once the protocol is live, users staking more SOL into the protocol, or withdrawing SOL from it, **can only mint or redeem revSOL and issSOL together, at the current protocol ratio.**&#x20;

Why? Because SOL deposited into the protocol will always generate both types of staking rewards, increasing the backing for both tokens. Users deposit stake into both portions, receive staking tokens representing both, and need to sell the undesired token in the marketplace.

Alternatively, the desired token can be purchased on a dex. (You’ll see these options in our staking application UI. Learn more [here](https://revtec.gitbook.io/revtec-docs/design/application-design).)&#x20;

When withdrawing from the protocol, it’s possible for the user to immediately receive their SOL if the protocol’s buffer is large enough. (It matches inflows with outflows, to prevent the delay of staking and unstaking SOL.) Otherwise, the user must wait for the stake to be unstaked at the end of the epoch, before a cool down period which takes another epoch. The user can then claim their SOL using the application UI. &#x20;

## Why Bother? Concentrated Rewards

What makes RevTec interesting: **by holding 1 revSOL, you earn the REV from multiple staked SOL.** That’s because RevTec’s entire pool of staked SOL is paying all of its REV rewards to the portion backing revSOL. The same is true for issuance, all of the issuance produced by the entire SOL pool flows to the issSOL backing.<br>

<figure><img src="../.gitbook/assets/image (9).png" alt="" width="563"><figcaption></figcaption></figure>

Because we initialized the pool ratio in line with their reward rate, the APYs of revSOL and issSOL will be the same at launch. But, as time passes, **even small changes in the Solana network’s yield will cause large changes in the APY of revSOL and issSOL.**

## Simple Example

1\. Protocol is initialized:&#x20;

* Let’s say the RevTec protocol is initialized on January 1st, 2026. At that moment, Solana staking is generating: 5% APY: 1% from REV and 4% from inflation.&#x20;
* The RevTec protocol is manually initialized with this 1:4 ratio.&#x20;
* An initial amount of 100 SOL is deposited into the protocol. The 1:4 ratio determines how the SOL is allocated:&#x20;
  * The REV bucket receives 20 SOL, and 20 revSOL are minted. revSOL has a fair value of 1 SOL.&#x20;
  * The issuance bucket receives 80 SOL, and 80 issSOL are minted. issSOL has a fair value of 1 SOL.&#x20;

2\. The user deposits:&#x20;

* The protocol has been initialized and is in operation with a 1:4 ratio.&#x20;
* A user deposits 10 SOL, wishing to acquire revSOL only.
  * If the user stakes via the **basic** mechanism (without selecting “advanced mode”) the protocol will mint for him 2 revSOL and 8 issSOL. He must then manually sell his 8 issSOL for SOL, and repeat the staking action, or directly sell the 8 issSOL for revSOL.&#x20;
  * If the user chooses **“advanced mode, direct**” the application will automate the action of staking and selling issSOL three times, before it stakes and uses the remaining SOL to purchase revSOL on a dex.&#x20;
  * If the user chooses **“advanced mode, via dex”** the user simply uses his entire 10 SOL deposit to purchase his desired revSOL via a dex.&#x20;

<figure><img src="../.gitbook/assets/image (40).png" alt="" width="563"><figcaption><p>The staking flow</p></figcaption></figure>

* Let’s assume the user’s 10 SOL deposit followed the 1:4 ratio, adding 2 SOL to the REV bucket and 8 SOL to the issuance bucket. &#x20;
  * The REV bucket now has 20 + 2 = 22 SOL
  * The issuance bucket now has 80 + 8 = 88 SOL.&#x20;

3\. Rewards are earned:&#x20;

* During the following year, the REV reward rate is double the previous year, producing the equivalent of 2% APY for staked SOL instead of 1%. &#x20;
  * The total 110 SOL inside the protocol produces 110 \* 2% = 2.2 SOL of REV rewards.&#x20;
  * Distributed to the 22 SOL in the REV bucket, this results in a 2.2/22 = 10% increase in the value of revSOL
  * The REV bucket now has 22 + 2.2 = 24.2 SOL backing it.&#x20;
* The issuance APY remains at 4%
  * The total 110 SOL inside the protocol produces 110 \* 4% = 4.4 SOL of rewards.&#x20;
  * Distributed to the 88 SOL, this results in a 4.4/88 = 5% increase in the value of issSOL
  * The issuance bucket now has 88 + 4.4 = 92.4 SOL backing it.&#x20;

Over the course of the year, staking SOL outside of revTec would have earned 6% APY. Holding revSOL would have earned 10%, and holding issSOL would have earned 5%. Because REV APY increased from the previous year, and issuance APY stayed the same, the size of the REV pool grew faster than the issuance pool, becoming a more dominant share of the total staked SOL, and increasing the ratio in favor of REV.&#x20;

4\. User redeems: \
Now that the year is over, the user wishes to redeem his revSOL for SOL.&#x20;

* The protocol now has 24.2 SOL in the REV portion and 92.4 SOL in the issuance portion, for a total of 114.6 SOL. The REV:issuance ratio is 1:3.82.&#x20;
* If the user stakes via the **basic** mechanism (without selecting “advanced mode”), he will need to acquire issSOL in the ratio of 1:3.82 to be able to deposit both tokens. To redeem his 10 revSOL, he also needs 38.2 issSOL to deposit into the protocol.
* If the user chooses **“advanced mode, direct”** the application will automate the action of buying the missing token and unstaking both the tokens for SOL.
* If the user chooses **“advanced mode, via dex”** the application will simply sell the 10revSOL for SOL via a dex.&#x20;

<figure><img src="../.gitbook/assets/image.png" alt="" width="536"><figcaption><p>The unstaking flow</p></figcaption></figure>

Generally, the choice of which staking and unstaking route to take will depend on which can yield a better result for the user. The application displays the token, allowing the user to choose the most price-efficient option for themselves.

## Wrapping Up

Hopefully this explanation has made sense to you. This is the first dual staking token protocol that we’re aware of. As such, it requires dex liquidity for users to achieve single-token positions, and creates a learning curve to become familiar with the functionality under the hood. We’ve built our application to simplify the user experience while preserving users’ choice.

<br>
