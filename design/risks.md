# Risks

Staking is often referred to as crypto’s “benchmark rate” or “risk-free rate”, as it represents the lowest-risk method for earning yield. On Solana, this is particularly true: there are no slashing or downtime penalties, and staking is non-custodial, with users retaining full control over their assets. As a result, the risk of loss from native staking is negligible.

However, RevTec introduces an additional layer via smart contracts, which brings its own set of risks that users should carefully consider.

**Security reviews:** The live mainnet protocol runs the **v2** smart contracts — a rewrite of the implementation (the product design is unchanged). Those contracts were independently audited by [Accretion](https://accretion.xyz/) in **April 2026** ([audit report](https://drive.google.com/file/d/1A36l5DbKSbVU74A800b909IGTrELBc2p/view)). An earlier Accretion audit (November 2025) covered the previous (v1) contract codebase and does **not** apply to the contracts running on mainnet today. Separately, a [protocol analysis report](https://abc-research.at/revtec-protocol-analysis/) discusses the RevTec design generally. Audits reduce risk but do not eliminate it.

## **Smart contract risk**

RevTec is built on a set of custom smart contracts. While the protocol is designed with security in mind, bugs or vulnerabilities could lead to unintended behavior—such as unauthorized minting of tokens without staked SOL backing, or incorrect redemption of tokens.

➡️ The current **v2** contracts received an [independent audit by Accretion in April 2026](https://drive.google.com/file/d/1A36l5DbKSbVU74A800b909IGTrELBc2p/view). Mainnet program ID and related addresses are listed under [Official Links & Mainnet Addresses](../resources/official-links-and-addresses.md).

## **Liquidity risk**

Once issSOL and revSOL are listed on DEXs, market dynamics determine both their price and available liquidity. If you stake SOL and sell off one of the two yield tokens, reclaiming your original SOL later requires you to either:

* Sell the remaining token
* Buy back the one you previously sold (you can only redeem both tokens together for SOL)

➡️ Low liquidity could affect your ability to exit positions efficiently. Always assess market depth before trading.

## **Yield** Volatility

Both issuance and REV yields fluctuate over time:

* REV rewards depend on network activity and are inherently volatile.
* Issuance rewards decrease gradually per Solana’s inflation schedule and vary based on the total staked supply.

➡️ These fluctuations impact the market price of issSOL and revSOL tokens. Make sure you understand how changes in yield affect token value before participating.

## **Tax and Regulatory Risk**

Interacting with RevTec may have different tax implications than native staking.

* Claiming or selling yield tokens could constitute taxable events (e.g., income or capital gains),
* These may differ from standard staking, which is often treated as income-only in some jurisdictions.

➡️ Consult a local tax advisor to fully understand your obligations.
