# Staking Yield Components

Stakers who don't use RevTec receive a default staking yield, which consists of newly minted SOL tokens (aka inflation), tips collected by the [Jito](https://www.jito.wtf/) client, and priority fees (aka block rewards). These are combined and passed onto the staker, minus the validator operator's commission fees. The combination of Jito tips and priority fees are commonly referred to as "real economic value", or REV. They both serve the same purpose, which is to increase the likelihood that a transaction is included by a validator in a block. RevTec will combine these two yield sources and pass them onto holders of revSOL.&#x20;

Starting in 2024, as shown below, increasing on-chain activity on Solana led to the generation and capture of a significant amount of fees for stakers and validators. This new source of yield more than compensated for the ever-decreasing issuance yield, but also had the effect of increasing the volatility of the default staking yield.&#x20;

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

## Jito Tips

Jito Tips are a fee-paying mechanism via Jito’s bundling infrastructure. Especially useful for arbitrage traders, who can submit bundles of transactions to be executed together. Validators can determine how much gets passed back to the staker via Jito’s Tip Router. Jito tips are sometimes referred to as “MEV tips” or “MEV yield”.

In more detail: Unsophisticated trading behavior or time-sensitive liquidity imbalances cause inefficiencies or arbitrage opportunities in on-chain markets. Arbitrageurs (known as MEV searchers) detect these opportunities and submit bundles of prioritized transactions through Jito’s infrastructure. To ensure inclusion of their bundles in a block, they attach tips (paid in SOL) to their bundles. These tips are received by validators running the Jito-Solana client. Validators then take a commission rewards before distributing the remaining tips to their stakers.

As on-chain activity spikes (e.g. during mints, airdrops, liquidations, or major DEX trades), the number and value of arbitrage opportunities increase—leading to higher cumulative tips and thus greater REV for validators and stakers. As shown below, the amount of REV generated on Solana is highly correlated with the on-chain trading volume.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>Source: <a href="https://blockworks.co/analytics/solana">Blockworks</a></p></figcaption></figure>

## Priority Fees

Priority fees are Solana’s native fee mechanism, allowing users to pay extra for their transactions to be prioritized over others. Also referred to as “block rewards”, these fees are kept by the validator by default, but can be shared via custom logic or LSTs, Jito’s upgraded Tip Router, or the upcoming SIMD-123 implementation.

In more detail: During periods of high network congestion—when many transactions are competing for block space—users often raise their fee levels to increase the likelihood of inclusion. This is especially true for traders and MEV searchers, who are willing to pay high fees to ensure the timely execution of arbitrage or other profitable strategies.

Originally, Solana’s protocol design specified that 50% of transaction fees were burned (permanently removed from supply), while the remaining 50% went to validators. However, in May 2024, the passing of [SIMD-96](https://forum.solana.com/t/proposal-for-enabling-the-reward-full-priority-fee-to-validator-on-solana-mainnet-beta/1456) changed this, allowing validators to retain 100% of transaction fees, significantly increasing their potential earnings during periods of elevated activity.

Some validators began experimenting with off-chain solutions to redistribute a portion of these block rewards (transaction fees and MEV) to their stakers. These systems allowed them to advertise higher APYs than competitors, but the reward-sharing mechanisms were not enforced or verifiable on-chain, creating trust and transparency issues.

In July 2025, the implementation of [JIP-16](https://www.jito.network/blog/tiprouter-upgrade-facilitating-priority-fees/) enabled validators to share block rewards with stakers via the Jito Tip Router - the same Jito infrastructure used to distribute MEV tips to stakers. **This is the infrastructure that will be used by RevTec, at least until SIMD-123 is implemented on mainnet.**&#x20;

In March 2025, [SIMD-123](https://forum.solana.com/t/proposal-for-an-in-protocol-distribution-of-block-rewards-to-stakers/3295) was passed, introducing a protocol-level mechanism that allows validators to share block rewards directly with their stakers in a transparent and verifiable way. Once SIMD-123 is implemented on mainnet (perhaps Q1 or Q2 2026?), RevTec will use this mechanism to distribute priority fees to revSOL holders, instead of the Jito Tip Router, which charges a small fee of 1.5% on distributed rewards.&#x20;

## Issuance Yield

Issuance refers to newly created SOL tokens distributed in accordance with [Solana’s inflation schedule](https://docs.anza.xyz/implemented-proposals/ed_overview/ed_validation_client_economics/ed_vce_state_validation_protocol_based_rewards). Validators earn these tokens by participating in consensus—specifically by submitting _vote transactions_ that attest to the correctness of blocks. Each successful vote earns _vote credits_, which determine how much issuance reward a validator receives. These rewards are then shared with the validator’s stakers, after deducting the validator’s commission.

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption><p>March 2020 is year "0". Source: <a href="https://docs.anza.xyz/implemented-proposals/ed_overview/ed_validation_client_economics/ed_vce_state_validation_protocol_based_rewards">Anza docs</a></p></figcaption></figure>

Newly issued SOL tokens are distributed as rewards to stakers. However, since not all SOL in circulation is staked—currently around 66%—the inflation is distributed across a smaller subset of token holders. As a result, the staking yield from issuance is higher than the network-wide inflation rate, because the same amount of newly minted tokens is shared among fewer participants.

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption><p>March 2020 is year "0". </p></figcaption></figure>

Therefore, in addition to the steady decline in issuance due to Solana’s decreasing inflation schedule, the percentage of SOL that is staked also plays a key role in determining the staking APY from issuance. However, this staking rate has historically remained relatively stable, hovering around 66%, which has helped keep issuance-based staking yields fairly predictable over time.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption><p>Source: <a href="https://dune.com/21co/staking-dashboard">Dune</a></p></figcaption></figure>

In March 2025, a proposal known as [SIMD-228](https://forum.solana.com/t/proposal-for-introducing-a-programmatic-market-based-emission-mechanism-based-on-staking-participation-rate/3294) argued that Solana’s issuance was too high and recommended adjusting the inflation schedule to reduce the rate at which new SOL is minted. The proposal did not pass governance and was ultimately not adopted. However, many in the community expect a similar proposal to be made and passed at some point in the future.

