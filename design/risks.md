# Risks

Staking is often called crypto’s “benchmark rate” or “risk-free rate” because it is among the lowest-risk ways to earn yield. On Solana that is especially true: there are no slashing or downtime penalties, and staking is non-custodial — you keep control of your assets. Risk of loss from **native** staking alone is negligible.

RevTec adds smart contracts on top of that, which introduce risks you should understand before using the protocol.

**Security reviews:** The live mainnet protocol runs the **v2** smart contracts — a rewrite of the implementation (the product design is unchanged). Those contracts were independently audited by [Accretion](https://accretion.xyz/) in **April 2026** ([audit report](https://drive.google.com/file/d/1A36l5DbKSbVU74A800b909IGTrELBc2p/view)). An earlier Accretion audit (November 2025) covered the previous (v1) contracts and does **not** apply to what runs on mainnet today. Separately, a [protocol analysis report](https://abc-research.at/revtec-protocol-analysis/) discusses the RevTec design generally. Audits reduce risk; they do not eliminate it.

## Smart contract risk

RevTec uses custom smart contracts. Bugs or vulnerabilities could cause unintended behavior — for example unauthorized minting without enough staked SOL backing, or incorrect redemption.

➡️ The current **v2** contracts received an [independent audit by Accretion in April 2026](https://drive.google.com/file/d/1A36l5DbKSbVU74A800b909IGTrELBc2p/view). Mainnet program ID and related addresses are listed under [Official Links & Mainnet Addresses](../resources/official-links-and-addresses.md).

## Liquidity risk

Once issSOL and revSOL trade on markets, price and available liquidity are set by the market. If you stake SOL and sell one of the two tokens, getting back to SOL later usually means either:

* Selling the remaining token, or
* Buying back the one you sold (you can only redeem **both** tokens together for SOL through the protocol)

➡️ Thin liquidity can make exits expensive or slow. Check market depth before trading. See also [Fair Value, Market Price & APY](fair-value-market-price-and-apy.md).

## Yield volatility

Both issuance and REV yields change over time:

* REV depends on network activity and can swing sharply.
* Issuance declines gradually with Solana’s inflation schedule and also varies with how much SOL is staked network-wide.

➡️ Those moves affect both fair value growth and market prices of issSOL and revSOL. Understand how yield changes affect token value before participating.

## Tax and regulatory risk

Using RevTec may have different tax treatment than native staking.

* Claiming or selling yield tokens can be taxable events (for example income or capital gains).
* That may differ from ordinary staking, which some jurisdictions treat mainly as income.

➡️ Talk to a local tax advisor about your situation.
