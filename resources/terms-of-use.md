---
description: Last updated July 6, 2026
---

# Terms of Use

## I. Introduction

These Terms of Use ("**Terms**") govern your access to and use of websites, applications, and related interfaces operated by **H2O Nodes GmbH** and its affiliates ("**RevTec**," "**we**," "**us**," or "**our**") that reference these Terms, including [app.revtec.fi](https://app.revtec.fi) and documentation at [revtec.gitbook.io](https://revtec.gitbook.io/revtec-docs) (each, an "**Interface**").

The RevTec **protocol** consists of open-source smart contracts deployed on the Solana blockchain. The protocol is **permissionless** — anyone can interact with it, with or without our Interfaces. These Terms apply to **our Interfaces and related services**, not to third-party software or the underlying blockchain.

These Terms, together with documents incorporated by reference (including our [Privacy Policy](privacy-policy.md)), form a binding agreement between you and H2O Nodes GmbH.

**NOTICE:** BY ACCESSING OR USING ANY INTERFACE, YOU CONFIRM THAT YOU HAVE READ, UNDERSTOOD, AND AGREE TO THESE TERMS, INCLUDING THE ARBITRATION AND CLASS-ACTION WAIVER IN SECTION IX. IF YOU DO NOT AGREE, DO NOT USE THE INTERFACES.

Nothing in these Terms creates a custodial relationship, brokerage, investment advisory, or fiduciary relationship between you and RevTec.

## II. The Interfaces and the Protocol

### A. Overview

RevTec is a **dual-token liquid staking** design on Solana. Staking yield is conceptually split into:

* **revSOL** — accrues **Real Economic Value ("REV")** (priority fees and Jito tips attributable to **protocol stake**), via increases in on-chain backing per token.
* **issSOL** — accrues **issuance (inflation) yield** attributable to **protocol stake**, via increases in on-chain backing per token.

Fair value of each token is determined on-chain as backing lamports divided by token supply. Your token **balance** may stay constant while each token becomes redeemable for **more SOL over time** if yield accrues — similar to other liquid staking tokens.

**Scope (important):** REV and issuance described above apply to SOL deposited **through the RevTec protocol** (the LSP pool). SOL staked **directly** to the RevTec validator (or any validator) **without** depositing through the protocol does **not** mint revSOL or issSOL and does **not** increase protocol backing. revSOL holders participate in REV earned on **protocol TVL**, concentrated on the rev leg — not necessarily in REV earned by all stake on the validator.

Within the pool, **100% of REV** processed by the protocol is allocated to rev backing and **100% of issuance** processed by the protocol is allocated to iss backing. That **concentration** can amplify revSOL APY when network REV is elevated, and can produce **low or volatile revSOL APY** when network activity is quiet.

The protocol may operate at **limited TVL** during pilot phases. Liquidity, cranks, and treasury capacity may be immature. Use only what you can afford to lose.

### B. Deposits, withdrawals, and ratios

**Deposits:** When you deposit SOL through the protocol (standard flow), you typically receive **both** revSOL and issSOL according to the configured **deposit split** (on mainnet, currently **10% rev / 90% iss** unless changed by governance). You cannot mint only one token through the standard on-chain deposit instruction.

**Withdrawals:** To withdraw SOL from the protocol, you must burn **both** revSOL and issSOL in proportion to the **current backing split** (rev backing ÷ total backing), which **drifts over time** as the two yield sources accrue at different rates. The backing split at exit may differ from the deposit split at entry.

**Single-token exposure:** If you want only revSOL or only issSOL, you may use DEX swaps or app tooling ("advanced" flows). Such routes involve **slippage, liquidity, and market price vs fair value** risks we do not control.

**Instant vs delayed exit:** Instant withdrawal depends on a liquid **treasury buffer**. If insufficient, you must use **delayed withdrawal** (epoch-bound unstaking and cooldown). Availability is shown in the Interface but is **not guaranteed**.

**Cranks:** Yield accrual in fair value generally requires **permissionless third-party or operator "crank" transactions** (e.g. processing issuance or REV yield). Cranks may be delayed; displayed APY may lag on-chain state.

### C. Validator, Jito, and fees

Protocol stake is delegated to the **RevTec validator** (operated by H2O Nodes). The validator participates in [Jito Tip Router](https://www.jito.network/blog/tiprouter-upgrade-facilitating-priority-fees/) fee-sharing arrangements; see [solsharing](https://www.solsharing.com/) for validator-level disclosure.

REV attributable to protocol stake is swept to the protocol **yield treasury** and reflected in revSOL backing after processing. Issuance accrues in stake accounts and is reflected in issSOL backing after processing.

**Fees (current, may change):**

| Layer | Fee |
|-------|-----|
| RevTec **protocol** | **0%** program fees on mainnet at launch (`rev_fee_bps` / `iss_fee_bps` configurable) |
| RevTec **validator** | **10%** commission on issuance rewards |
| **Jito** | **1.5%** on shared priority fees; **3%** on Jito tips (Tip Router economics) |

We may change validator delegation, fee parameters, or REV routing mechanisms (including in connection with Solana upgrades such as SIMD-123), with disclosure via Interfaces or public channels where practicable.

### D. DeFi composability

revSOL and issSOL may be used with third-party protocols (e.g. DEXs such as Raydium, yield trading such as Exponent, lending/multiply such as Kamino). Integrations or links in our Interfaces **do not** constitute endorsement, supervision, or guarantees. Third-party protocols have their own terms and risks.

### E. Non-custodial nature

Our Interfaces do **not** custody your assets. You connect a self-hosted wallet; you initiate on-chain transactions. We cannot access private keys, reverse transactions, or guarantee transaction success. You are responsible for wallet security and for all Solana network fees.

### F. Information only — no advice; no offer

Interface content (including APY, fair value, charts, and documentation) is for **informational** purposes only. It may be delayed, incomplete, or annualized over arbitrary windows. **We do not guarantee** accuracy.

Nothing on the Interfaces is **investment, tax, legal, or financial advice**, or an **offer to sell** or solicitation to buy any asset. RevTec has **not** issued a governance or protocol token in connection with these Terms. Past or displayed yield is not indicative of future results.

## III. Modifications

We may modify these Terms, Interfaces, or related services at any time. Updated Terms will be posted with a revised date. Continued use after the effective date constitutes acceptance.

We may modify, suspend, or discontinue any Interface without liability. We have no obligation to maintain any Interface or to continue operating any validator or market-making activity.

## IV. Your responsibilities

### A. Eligibility and representations

You must be **18+** and have legal capacity. If acting for an entity, you represent authority to bind it.

You represent that you are not subject to applicable **sanctions** (including OFAC, EU, UK, or UN lists) and will comply with **anti-money laundering** and applicable laws in your jurisdiction.

You understand and accept risks including:

* **Smart contract** bugs, exploits, or upgrades (see audit disclaimer below).
* **Irreversible** on-chain transactions.
* **Validator** performance, slashing (where applicable), and delegation changes.
* **REV volatility** — revSOL APY can be **much lower** than issSOL or vanilla staking for extended periods.
* **Issuance decline** per Solana’s inflation schedule.
* **Dual-token mechanics** — you may hold rev or iss without the paired amount needed to withdraw from the protocol; exiting may require **DEX purchases** at unfavourable prices.
* **Market vs fair value** — DEX prices may diverge from on-chain fair value; liquidity may be **thin**.
* **Treasury / instant exit** unavailability.
* **Regulatory** change affecting staking, LSTs, or DeFi in your jurisdiction.

### B. Prohibited conduct

You will not: violate law; attack or scrape Interfaces; introduce malware; attempt unauthorised access; misrepresent affiliation with RevTec; or use Interfaces for money laundering or sanctions evasion.

**Tax:** You alone are responsible for tax consequences of using revSOL, issSOL, and related DeFi activity. Consult a qualified adviser.

### C. Feedback

Feedback you provide may be used by us without obligation or compensation to you, subject to applicable law.

## V. Intellectual property

We own Interface IP and grant you a limited, revocable licence to use Interfaces for their intended purpose. RevTec names and logos are our trademarks; do not use them without permission except as allowed by law.

## VI. Third-party services

Interfaces may link to or integrate **Third Party Services** (wallets, RPC providers, DEXs, Jito, etc.). We do not control them and are **not liable** for them. Your use is at your own risk and subject to their terms.

## VII. Indemnification

To the extent permitted by law, you agree to indemnify H2O Nodes GmbH and its officers, directors, employees, contractors, and affiliates against claims arising from your use of Interfaces, violation of these Terms, violation of law, or disputes with third parties.

## VIII. Disclaimers and limitation of liability

### A. General

INTERFACES ARE PROVIDED "**AS IS**" AND "**AS AVAILABLE**." TO THE MAXIMUM EXTENT PERMITTED BY LAW, WE DISCLAIM ALL WARRANTIES, EXPRESS OR IMPLIED.

### B. Protocol-specific

Without limitation, we do **not** warrant:

* Future **yield, APY, or token value** of revSOL or issSOL.
* **DEX liquidity** or favourable swap prices.
* Continued operation of **Jito**, Solana, or any third-party infrastructure.
* **Validator** uptime or performance.
* **Security** of smart contracts. A **November 2025 audit by Accretion** does not guarantee absence of vulnerabilities.

### C. Liability cap

TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW, OUR AGGREGATE LIABILITY ARISING FROM THESE TERMS OR THE INTERFACES SHALL NOT EXCEED **€100**. WE ARE NOT LIABLE FOR INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, OR PUNITIVE DAMAGES, OR LOSS OF PROFITS, DATA, GOODWILL, OR CRYPTOASSETS, INCLUDING CHANGES IN VALUE OF REVSOL OR ISSSOL.

Some jurisdictions do not allow certain limitations; in those cases, our liability is limited to the fullest extent permitted by law.

## IX. Governing law and disputes

### A. Governing law

These Terms are governed by the **laws of Austria**, excluding conflict-of-law rules that would apply another jurisdiction’s law.

### B. Informal resolution

Before formal proceedings, the parties will attempt good-faith resolution. The complaining party must send written notice; the parties will confer within a reasonable period (e.g. 45 days).

### C. Arbitration

Disputes not resolved informally shall be resolved by **binding arbitration in Vienna, Austria**, under rules agreed by the parties or, failing agreement, rules of a recognised Austrian arbitration institution (e.g. VIAC), before **one arbitrator**, in **English** unless otherwise required by mandatory law.

### D. Class waiver

DISPUTES ARE ON AN **INDIVIDUAL BASIS ONLY**. NO CLASS, COLLECTIVE, OR REPRESENTATIVE ACTIONS.

### E. Courts

Either party may seek **interim or injunctive relief** from competent courts where necessary. Subject to the above, the courts of **Vienna, Austria** have non-exclusive jurisdiction.

## X. General

**Assignment:** You may not assign these Terms. We may assign them in connection with a reorganisation or sale.

**Entire agreement:** These Terms supersede prior understandings on this subject.

**No waiver:** Failure to enforce a provision is not a waiver.

**Severability:** If a provision is invalid, the remainder remains in effect.

**Contact:** For legal notices, use contact details published on [revtec.fi](https://www.revtec.fi) or the Interface.
