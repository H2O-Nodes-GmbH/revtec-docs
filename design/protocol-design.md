# Protocol Design

## Summary

* RevTec turns staking yield into two liquid staking tokens: **revSOL**, which earns Solana’s real economic value (transaction fees and tips), and **issSOL**, which earns issuance (newly minted SOL). Each token’s **fair value** is the SOL that backs it divided by how many tokens exist, and that fair value rises as rewards accrue — the same pattern as other liquid staking tokens on Solana.
* The yield described on this page applies to SOL you deposit **through the RevTec protocol**. Staking SOL directly with the RevTec validator without minting these tokens does **not** increase revSOL or issSOL backing.
* Inside the protocol pool, all of that pool’s fee-and-tip rewards go to revSOL’s backing, and all of its issuance rewards go to issSOL’s backing. Because of that concentration, each token’s yield can differ a lot from ordinary staking.
* Deposits and withdrawals both use the **current backing mix** (rev backing ÷ total backing). You receive both tokens when you deposit, and you must burn both in that same live mix when you withdraw. The mix drifts over time as the two yield sources accrue at different rates. Withdrawals pay SOL at fair value.
* If you want only revSOL or only issSOL, you use a market (or the app’s Advanced options). Market price can differ from fair value — see [Fair Value, Market Price & APY](fair-value-market-price-and-apy.md).
* Yield figures in the app are fair-value APY in the Jito style: each Solana epoch’s growth in SOL per token is annualized on its own, then averaged over the last **10 epochs**.

## The Objective

Normal Solana staking mixes two yields: **issuance** (new SOL) and **real economic value (REV)** (priority fees and tips). RevTec separates them into two liquid staking tokens — **issSOL** and **revSOL** — so you can choose which stream to hold, with more capital efficiency than holding blended staking yield alone.

These tokens follow the usual liquid-staking pattern on Solana: they start near 1:1 with SOL at launch and gain value as yield accrues. Your token **balance** can stay constant while each token becomes redeemable for more SOL over time. That familiar model makes DeFi integrations straightforward.

> **Mainnet (v2):** Program ID `59k5msuGtD4oCnkYStGSF7kjeBVynQLNtmYjfg79P7V6` · revSOL `HgEWmCePuhRwrTQMnV7Z4oHiNfjbVZHFXA9XfT9DN3FV` · issSOL `2AvFj4iGTpZnrRo7vLuTMoNNfE7VKAK4SpiJfTnu6Nmq`. Full address list: [Official Links & Mainnet Addresses](../resources/official-links-and-addresses.md#mainnet-addresses-v2).

### Scope: protocol pool vs validator stake

> **Important:** RevTec separates REV and issuance for SOL deposited **through the protocol** (the liquid staking pool). Stake delegated **directly** to the [RevTec validator](https://stakewiz.com/validator/B1rsc6jv3RsFpkak8qvJN3PfGYSg9E3Uw1joaV1EoiFj) — without minting revSOL or issSOL — earns normal validator rewards on its own. That stake does **not** increase revSOL or issSOL backing.
>
> **Concentration (within the pool):** All REV earned on **protocol stake** goes to revSOL’s backing; all issuance earned on protocol stake goes to issSOL’s backing. So revSOL holders earn fees from the **entire protocol stake base**, concentrated onto the smaller rev portion — not split pro-rata like a normal liquid staking token. When network REV is high, revSOL’s annualized yield can exceed ordinary staking by a wide margin (see Simple Example).
>
> **Pilot note:** revSOL’s yield can look low in quiet markets because REV is a small share of total staking yield today, and protocol deposits may be small relative to total stake on the validator. That reflects network conditions and scale, not a broken design.

## Rewards & Fees

RevTec is an accounting system that tracks two yield types on **protocol stake**:

| Yield type | Token | Source | On-chain update |
|------------|-------|--------|-----------------|
| **Issuance** (inflation) | issSOL | Native staking rewards in validator stake accounts | `process_iss_yield` (permissionless update, per epoch) |
| **REV** (priority fees + Jito tips) | revSOL | Tips claimed via [Jito Tip Router](https://www.jito.network/blog/tiprouter-upgrade-facilitating-priority-fees/), swept to `rev_yield_treasury` | `sweep_jito_tips_from_stake` / `collect_jito_tips`, then `process_rev_yield` |

At launch, the [RevTec validator](https://stakewiz.com/validator/B1rsc6jv3RsFpkak8qvJN3PfGYSg9E3Uw1joaV1EoiFj) shares priority fees and Jito tips with delegators via the Tip Router ([solsharing](https://www.solsharing.com/)). **All SOL deposited through RevTec** is staked with this validator.

#### Issuance (issSOL)

Issuance rewards accrue inside the validator’s stake accounts each epoch (Solana native staking). The protocol records the increase by comparing the stake account balance to the last recorded balance, then increases `iss_backing_lamports`. Fair value of issSOL is:

`iss_fair = iss_backing_lamports / iss_supply`

**Ordering:** Jito tips that land in a stake account must be **swept to the REV treasury before** issuance yield is processed for that epoch, so tips are not mis-counted as issuance.

#### REV (revSOL)

REV (priority fees and Jito tips on **protocol stake**) is swept into `rev_yield_treasury`. A permissionless **`process_rev_yield`** update then increases `rev_backing_lamports` (the exchange-rate step-up). SOL remains in the treasury; only the backing counter changes — the same pattern other liquid staking tokens use to track accrued yield.

Fair value of revSOL is:

`rev_fair = rev_backing_lamports / rev_supply`

REV does **not** auto-compound silently: these on-chain updates (often called cranks) must run (anyone can run them). In practice, bots or the team run them regularly.

#### Protocol vs validator fees

The RevTec **program** charges no deposit/withdraw fees beyond Solana transaction costs (`rev_fee_bps` and `iss_fee_bps` are configurable; **currently 0% on mainnet**).

Fees that **do** apply:

| Layer | Fee | Notes |
|-------|-----|--------|
| RevTec validator | 10% commission on **issuance** | Funds ongoing development |
| Jito | 1.5% on shared priority fees; 3% on Jito tips | Standard Tip Router economics |

These validator and Jito fees may be revisited over time.

## Initializing the Protocol

Over time, cumulative REV and issuance rewards diverge; the protocol tracks both backing pools independently. **Before any backing exists**, a proportional split is undefined, so the **first** deposit seeds the pools from a configured starting mix (chosen to roughly match the then-current mix of network staking yield) — e.g. if staking is ~5% APY with ~1% from REV and ~4% from issuance, a **1:4 rev:iss** seed is a reasonable start.

**Live mainnet (example):** the first deposit was seeded at **10% rev / 90% iss**. The **1:4 (20/80) ratio in the Simple Example below is illustrative** — the math is the same; only the numbers change.

That first deposit mints revSOL / issSOL ~1:1 with SOL at fair value (exchange rate starts near 1.0 and grows as yield accrues). **Every deposit after that** ignores the seed config and splits incoming SOL by the **live backing mix** instead. As REV and issuance arrive at **different rates**, backing grows at different rates → the mix drifts and **rev and iss APY diverge**.

## Mints and redeems — one live backing mix

Deposits and withdrawals use the **same** rule: split by current backing.

| | **Backing mix** |
|---|-----------------|
| **What it is** | Share of SOL backing rev vs iss **right now** (`rev_backing / total_backing`) |
| **Used when** | `deposit`, `withdraw_instant`, and `withdraw_delayed` |
| **Drifts over time?** | **Yes** — as iss and rev accrue at different rates |
| **Mainnet example** | Starts near the seed (e.g. ~10% / ~90%) and tracks live backing thereafter |

#### Deposits

New SOL deposited via the protocol mints **both** revSOL and issSOL in proportion to the **current backing mix** (unless the user uses a market-only flow in the app — see [Use Cases](use-cases.md)).

Why both tokens? SOL in the pool will earn **both** yield types; accounting assigns issuance to iss backing and REV to rev backing.

Alternatively, you can buy the token you want on a market such as Raydium. (You’ll see these options in the app at [app.revtec.fi](https://app.revtec.fi).)

#### Withdrawals

To withdraw SOL from the protocol, users burn **both** tokens in proportion to that same **current backing mix**.

Example: if backing is 20% rev / 80% iss, withdrawing 10 SOL requires burning rev and iss tokens in that 20:80 proportion (see Simple Example, step 4). A fresh deposit at that moment would mint in the same 20:80 proportion.

Users who want **only revSOL** or **only issSOL** typically:

* **Buy or sell on a market** (Advanced → Via DEX in the app), or
* **Deposit both tokens**, then sell the one they don’t want (Advanced → Direct in the app).

#### Instant vs delayed exit

**Instant withdraw** pays SOL from the protocol **treasury buffer** if it holds enough liquid SOL (above the rent reserve). If the buffer is empty or too small, users must use **delayed withdraw**: deactivate stake at an epoch boundary, wait for the cooldown, then claim.

Check the app for current treasury capacity before assuming instant exit is available.

## Why Bother? Concentrated Rewards

What makes RevTec interesting: **by holding 1 revSOL, you earn the REV from multiple staked SOL.** That’s because RevTec’s entire pool of staked SOL is paying all of its REV rewards to the portion backing revSOL. The same is true for issuance, all of the issuance produced by the entire SOL pool flows to the issSOL backing.

<figure><img src="../.gitbook/assets/image (9).png" alt="" width="563"><figcaption></figcaption></figure>

Because we initialized the pool ratio in line with their reward rate, the APYs of revSOL and issSOL will be similar at launch. But, as time passes, **even small changes in the Solana network’s yield will cause large changes in the APY of revSOL and issSOL.**

#### What “concentrated” means in practice

* **Inside the protocol pool:** 100% of REV from protocol stake goes to revSOL’s backing; 100% of issuance from protocol stake goes to issSOL’s backing.
* **Not across the whole validator:** SOL staked to the RevTec validator **outside** the protocol (for example, direct delegation) does not flow into revSOL backing.
* **Yield figures in the app** use the same method as JitoSOL: each epoch’s fair-value growth (`backing / supply`) is annualized on its own, then smoothed with a trailing **10-epoch** average. revSOL can still look **flat or low** for stretches in calm markets, then rise when REV updates process a batch of tips — a single catch-up epoch is dampened by that average.

## Simple Example

> **Note:** The example uses a **1:4 rev:iss** starting mix for round numbers. Mainnet’s first deposit was seeded at **1:9 (10%/90%)**; afterward both deposits and withdrawals follow live backing. The logic is identical.

1\. Protocol is initialized:

* Let’s say the RevTec protocol is initialized on January 1st, 2026. At that moment, Solana staking is generating: 5% APY: 1% from REV and 4% from inflation.
* The RevTec protocol is manually initialized with this 1:4 starting mix (used only for the first deposit).
* An initial amount of 100 SOL is deposited into the protocol. The 1:4 mix determines how the SOL is allocated:
  * The REV bucket receives 20 SOL, and 20 revSOL are minted. revSOL has a fair value of 1 SOL.
  * The issuance bucket receives 80 SOL, and 80 issSOL are minted. issSOL has a fair value of 1 SOL.

2\. The user deposits:

* The protocol has been initialized; current backing is still 20% rev / 80% iss, so later deposits use that live mix (not a separate admin policy).
* A user deposits 10 SOL, wishing to hold revSOL only.
  * In **basic** mode (no Advanced options), the protocol mints 2 revSOL and 8 issSOL. To end up rev-only, the user must sell the 8 issSOL (for SOL or for more revSOL).
  * **Advanced → Direct** automates staking and selling issSOL several times, then uses remaining SOL to buy revSOL on a market.
  * **Advanced → Via DEX** spends the full 10 SOL buying revSOL on a market.

<figure><img src="../.gitbook/assets/image (40).png" alt="" width="563"><figcaption><p>The staking flow</p></figcaption></figure>

* The user’s 10 SOL deposit follows the live 1:4 backing mix, adding 2 SOL to the REV bucket and 8 SOL to the issuance bucket.
  * The REV bucket now has 20 + 2 = 22 SOL
  * The issuance bucket now has 80 + 8 = 88 SOL.

3\. Rewards are earned:

* During the following year, the REV reward rate is double the previous year, producing the equivalent of 2% APY for staked SOL instead of 1%.
  * The total 110 SOL inside the protocol produces 110 \* 2% = 2.2 SOL of REV rewards.
  * Distributed to the 22 SOL in the REV bucket, this results in a 2.2/22 = 10% increase in the value of revSOL
  * The REV bucket now has 22 + 2.2 = 24.2 SOL backing it.
* The issuance APY remains at 4%
  * The total 110 SOL inside the protocol produces 110 \* 4% = 4.4 SOL of rewards.
  * Distributed to the 88 SOL, this results in a 4.4/88 = 5% increase in the value of issSOL
  * The issuance bucket now has 88 + 4.4 = 92.4 SOL backing it.

> **On-chain updates:** In production, `process_iss_yield` and `process_rev_yield` are separate permissionless instructions. Yield appears in fair value after they run — not necessarily at the exact epoch boundary on a clock.

Over the course of the year, staking SOL outside RevTec would have earned 6% APY. Holding revSOL would have earned 10%, and holding issSOL would have earned 5%. Because REV yield rose while issuance stayed the same, the REV pool grew faster than the issuance pool and became a larger share of total staked SOL.

4\. User redeems: \
Now that the year is over, the user wants to redeem revSOL for SOL.

* The protocol now has 24.2 SOL in the REV portion and 92.4 SOL in the issuance portion, for a total of 114.6 SOL. The REV:issuance ratio is 1:3.82.
* In **basic** mode, the user must obtain issSOL in that 1:3.82 mix to redeem. To redeem 10 revSOL, they also need 38.2 issSOL.
* **Advanced → Direct** buys the missing token and redeems both for SOL through the protocol.
* **Advanced → Via DEX** sells the 10 revSOL for SOL on a market (no protocol redeem).

<figure><img src="../.gitbook/assets/image.png" alt="" width="536"><figcaption><p>The unstaking flow</p></figcaption></figure>

Which route is best depends on price and liquidity at the time. The app shows quotes so you can pick the more efficient path for your size.

## Wrapping Up

RevTec is a dual-token liquid staking design: **issSOL** for issuance-like yield, **revSOL** for REV (fee) exposure, with fair value tracked on-chain as backing per token. It is the first dual staking token design we’re aware of on Solana; that novelty means:

* **Market liquidity** matters for single-token positions.
* **Deposits and withdrawals share one live backing mix** — it drifts as yield accrues (only the very first deposit used a configured seed).
* **REV yield is volatile** — quiet networks produce quiet revSOL; activity spikes produce the concentrated upside described above.

The app simplifies routing (basic deposit, Advanced → Direct, Advanced → Via DEX). Choose the path that minimizes slippage and leftover tokens for your size.

For current parameters (backing mix, fair values, yield), use [app.revtec.fi](https://app.revtec.fi).
