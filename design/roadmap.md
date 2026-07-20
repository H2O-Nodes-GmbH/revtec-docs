# Roadmap

### Q2 2025: Design Scoping&#x20;

* **Research & Scoping**: As part of the [Colosseum Hackathon](https://www.colosseum.org/hackathon) in May 16, 2025, we completed initial design research & scoping.&#x20;
* **Regulatory**: Following engagement with research and law firms, we gained an understanding of the legal and regulatory implications of our yield token design, and whether any changes needed to be made.&#x20;

### Q3 2025: Protocol Development

* **Contract Development**: Buildout of the smart contracts.&#x20;
* **App Development**: Buildout of the application.&#x20;

### Q4 2025: Devnet MVP & Audit&#x20;

* **Devnet MVP**: Deployment and testing of an MVP allowing for "basic" and "advanced" staking and unstaking on devnet, with a simple frontend.&#x20;
* **Audit**: Completion of an audit by [Accretion](https://accretion.xyz/).
* **Validator Launch**: Launch of the [RevTec validator](https://stakewiz.com/validator/B1rsc6jv3RsFpkak8qvJN3PfGYSg9E3Uw1joaV1EoiFj).

### Q1–Q2 2026: Protocol V2, Audit & Mainnet

* **Protocol V2 rewrite:** Full rewrite of the smart contracts (v2 LSP), replacing the prior design.
* **V2 Audit:** Independent audit of the v2 contracts by [Accretion](https://accretion.xyz/) in April 2026 ([report](https://drive.google.com/file/d/1A36l5DbKSbVU74A800b909IGTrELBc2p/view)).
* **Mainnet deployment:** Deployment of v2 to mainnet, and initial testing by a small group of users.
* **Raydium Listings**: Listing of revSOL and issSOL tokens on Raydium, with initial bootstrapped liquidity.

### H2 2026: DeFi Integrations & Protocol Evolution

* **Exponent Integration**: Integration of revSOL into yield-trading platform [Exponent](https://exponent.finance/), allowing for farming and fixing of REV yield
* **Kamino Integration:** Integration of revSOL and PT-revSOL into Kamino, allows for leveraged looping yield strategy via "[Kamino Multiply](https://kamino.com/multiply)".&#x20;
* **Block Rewards via SIMD-123**: Once SIMD-123 is implemented on mainnet, we will share priority fees directly on-chain instead of via Jito's Tip Router.&#x20;
* **Multi-validator staking pool**: Assuming SIMD-123 causes stake pools and other validators to adjust their fees to share block rewards with stakers, we can expand our delegation to multiple validators, beyond just the RevTec validator. This may warrant charging a fee on the protocol itself and spinning down the RevTec validator, or lowering its fee.&#x20;
* **Validator Downtime Protection:** In order to reduce the risk of underperformance by the validator(s), we could implement a bond system similar to Marinade's protected staking reserve (PSR).

