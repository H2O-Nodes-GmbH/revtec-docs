# Fair Value, Market Price & APY

## TL;DR

* **Fair value (FV)** = on-chain SOL backing per token. **Market price (M)** = DEX spot. They can diverge (premium or discount).
* App / protocol **APY** is fair-value growth from yield — not automatically what you earn from a Raydium entry price.
* Protocol redeem burns **both** tokens in the live backing ratio and pays SOL at fair value of that burn.
* Buying only one token, then later buying the other to redeem, tracks that token’s **market** path — it does **not** cancel an entry premium or guarantee fair-value APY.
* You get ~FV APY after a one-sided DEX buy mainly if that token’s premium/discount **% stays roughly constant** (or you mint/hold a full redeem basket from day one).

[Protocol Design](protocol-design.md) explains that each LST’s **fair value** is on-chain SOL backing per token, and that fair value rises as yield accrues. This page covers what that means when tokens also trade on a DEX — especially if you buy **one** token at a premium or discount and later redeem through the protocol.

## Two prices

| | **Fair value (FV)** | **Market price (M)** |
|---|---------------------|----------------------|
| **What it is** | SOL backing per token (on-chain exchange rate) | Spot price on Raydium / other DEXs |
| **How it’s set** | `backing_lamports / supply` after yield cranks | Supply and demand in the pool |
| **Used when** | Protocol mint / redeem (SOL paid for burned tokens) | Buying or selling a single token on a DEX |

For each token:

* `rev_fair = rev_backing_lamports / rev_supply`
* `iss_fair = iss_backing_lamports / iss_supply`

Live fair values and market prices are on [app.revtec.fi](https://app.revtec.fi). Raydium pool links are under [Official Links & Mainnet Addresses](../resources/official-links-and-addresses.md#raydium-clmm-pools).

**Market can diverge from fair value.** Thin liquidity, flow one way, or temporary dislocations can put either token at a **premium** (`M > FV`) or a **discount** (`M < FV`).

## Fair-value APY (what the app charts)

**Fair-value APY** (also called protocol / underlying APY) is how fast fair value grows from accrued yield:

* **revSOL** — REV (priority fees + Jito tips) credited to rev backing
* **issSOL** — issuance credited to iss backing

That is what holders earn **relative to fair value** — the growth of redeemable SOL per token. It is **not** automatically “what I earn if I bought on Raydium at today’s market price.”

Headline APY cards on the app are annualized from fair-value growth over a trailing window. They describe backing growth, not a guaranteed return from a DEX entry price.

## Buying on a DEX

If you buy at market:

* **Premium** (`M > FV`): you pay more SOL than the token’s current redeemable backing → if that premium later shrinks toward zero, your effective return is dragged below fair-value APY.
* **Discount** (`M < FV`): you pay less than redeemable backing → if the discount closes, you get a boost relative to fair-value APY.

> **Optional scenario (not a guarantee).** If you buy at market price `M`, fair value grows at protocol APY for one year, and you can exit at the grown fair value, then:
>
> `implied APY = (FV / M) × (1 + protocol APY) − 1`
>
> This is only honest if the premium/discount **closes** (or you otherwise exit at FV). It is a scenario for thinking about entry price — not a promise from the protocol.

## Redeem needs both tokens

Protocol withdraw burns **both** revSOL and issSOL in the **live backing ratio** (`rev_backing / total_backing`) and pays SOL for that burn at **fair value**. See [Protocol Design — Withdrawals](protocol-design.md#withdrawals).

If you hold only revSOL (or only issSOL):

* **Advanced → Direct** unstake buys the missing other token on the DEX (in the live ratio), then redeems both through the protocol.
* **Advanced → Via DEX** sells the token you hold for SOL on the market (no protocol redeem).

Buying the missing leg is what makes “I only hold one token” redeemable. It does **not** by itself erase an entry premium on the token you already held.

## The myth: “premium + discount cancel → I still get fair-value APY”

Common intuition: *“I bought revSOL at a premium; to redeem I buy issSOL at a discount; they cancel and I still earn fair-value APY.”*

**That is not generally true.**

Under a perfect market-maker that keeps the **redeem basket** at par — the combined market cost of a redeemable pair equals the combined fair value of that pair:

`M_rev · q_rev + M_iss · q_iss = FV_rev · q_rev + FV_iss · q_iss`

…a premium on one token implies a discount on the other (in the live redeem quantities `q_rev`, `q_iss`). That relationship is about the **basket**, not about refunding your entry price on a single token.

If you bought **only rev** at `t = 0` and at exit buy the missing iss then redeem, your net return (under that ideal MM assumption, ignoring fees) simplifies to roughly the **market-price path of the token you held** — something like `M_rev₁ / M_rev₀ − 1` — **not** automatic fair-value APY.

Buying the cheap other token at redeem is what makes “redeem” ≈ “exit at the market value of what you held.” It does **not** refund an entry premium.

When you *do* get ~fair-value APY after a DEX buy of one token:

* Roughly when that token’s premium/discount **percentage stays about constant** over the hold (market tracks FV growth one-for-one), or
* When you mint / hold a full redeem basket from day one and exit at protocol fair value.

If a premium **mean-reverts toward zero** over the year, you earn **less** than that token’s fair-value APY.

## Paths compared

| Path | Effective outcome (idealized) |
|------|-------------------------------|
| Mint / hold a **full redeem basket** from day one, redeem at protocol FV | ≈ blended fair-value APY of rev + iss |
| Buy **one** token on a DEX, later buy the other + redeem | ≈ that token’s **market** return path |
| Same, but the token’s **premium collapses** over the hold | Worse than that token’s fair-value APY |
| Sell on a DEX at the end (no redeem) | Also ≈ market price of what you hold |

Real markets add frictions: swap fees, slippage, imperfect market-making, and temporary dislocations where the basket itself trades off par. Always compare Direct vs Via DEX quotes in the app before exiting.

## How this shows up in the app

* **Dashboard / protocol APY cards** — fair-value (protocol) APY: growth of on-chain backing per token.
* **Fair value vs market** — the app already surfaces both so you can see premium or discount.
* **Any “market-implied” return framing** (now or later) should be treated as a **scenario** that depends on whether premium/discount closes — not as a guaranteed APY from a DEX purchase.

For mint/redeem mechanics and the live backing split, see [Protocol Design](protocol-design.md). For liquidity and market-vs-fair-value risk, see [Risks](risks.md).
