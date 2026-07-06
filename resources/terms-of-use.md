---
description: Last updated May 5th, 2026
---

# Terms of Use

## I. Introduction

These Terms of Use ("Terms of Use") set out the terms and conditions under which you, whether personally or on behalf of an entity ("you" or "your"), are permitted to use, interact with, or otherwise access the Interfaces or Features provided by RevTec (together with its affiliates, "RevTec," "we," "us," or "our"). These Terms of Use, together with any documents and additional terms or policies appended hereto or that expressly incorporate these Terms of Use by reference, as well as our Privacy Policy (collectively, the "Terms"), constitute a binding agreement between you and us.

These Terms apply to (i) all content, functionality, and features (the "Content Features") available on any website or graphical user interface hosted by RevTec to which the Terms are posted (each, an "Interface"), and (ii) software that RevTec operates or hosts, or makes available via an Interface (the "Technology Features" and, together with the Content Features, the "Features").

NOTICE: PLEASE REVIEW THESE TERMS CAREFULLY. BY ACCESSING, INTERACTING WITH, OR USING ANY INTERFACE OR FEATURE, YOU AGREE THAT YOU HAVE READ, UNDERSTOOD, AND AGREE TO BE BOUND BY THESE TERMS, INCLUDING THE BINDING ARBITRATION AGREEMENT AND CLASS ACTION WAIVER BELOW. IF YOU DO NOT AGREE TO ALL OF THE TERMS, YOU ARE NOT AUTHORISED TO INTERACT WITH, ACCESS, OR USE ANY INTERFACE OR FEATURE.

## II. The Interfaces and Features

### A. Overview of the Protocol

RevTec is a dual-token liquid staking pool built on the Solana blockchain. The protocol separates the two distinct components of Solana staking yield — Real Economic Value ("REV") and issuance yield — and directs them to two separate liquid staking tokens:

* revSOL — a liquid staking token that accrues REV, comprising priority fees and Jito tips paid by Solana users for transaction inclusion. revSOL appreciates in value relative to SOL as REV accumulates. Because the entire pool's REV rewards flow to the revSOL backing, holders of revSOL earn a concentrated exposure to REV yield.
* issSOL — a liquid staking token that accrues issuance yield, comprising newly minted SOL tokens distributed according to Solana's inflation schedule. issSOL appreciates at a more predictable rate that gradually decreases over time in line with Solana's declining inflation schedule.

Both tokens are valued 1:1 with SOL at protocol launch and gain value over time as yield accumulates. Token holders maintain a constant balance of revSOL or issSOL, and become entitled to a greater amount of underlying SOL the longer they hold.

### B. Minting and Redemption

When you deposit SOL into the RevTec protocol, you receive both revSOL and issSOL simultaneously, minted at the current protocol ratio (the "REV/Issuance Ratio"). This ratio reflects the relative proportion of cumulative REV and issuance rewards earned by the protocol since inception and shifts over time as the two yield sources accrue at different rates.

You may only mint or redeem revSOL and issSOL together, at the current protocol ratio. You cannot deposit SOL in exchange for only one token, nor redeem only one token for SOL directly through the protocol. If you wish to hold only revSOL or only issSOL, you must sell the unwanted token on a decentralised exchange ("DEX"). The RevTec application interface provides tooling (including "advanced mode") to automate this process on your behalf, but you acknowledge that such DEX transactions are subject to market conditions, slippage, and liquidity constraints entirely outside RevTec's control.

When redeeming, you may receive your SOL immediately if the protocol's buffer is sufficient to match inflows with outflows. Otherwise, you must wait for the stake to be unstaked at the end of the relevant Solana epoch, followed by a cooldown period of approximately one additional epoch, before claiming your SOL.

### C. Validator and REV Distribution

At launch, all SOL deposited into the RevTec protocol is staked with the RevTec validator, operated by H2O Nodes. The RevTec validator is currently the only Solana validator sharing 100% of priority fees and Jito tips with its stakers via the Jito Tip Router infrastructure.

REV yield (priority fees and Jito tips) is routed by the Jito Tip Router into RevTec's yield treasury account each epoch. Issuance yield is automatically compounded within the validator's stake account by Solana's native stake program. The RevTec protocol takes a snapshot each epoch to calculate the respective yield rates for revSOL and issSOL.

You acknowledge that the following fees currently apply at the validator level and are deducted before rewards are passed to token holders:

* Jito takes a fee of 1.5% on shared priority fees and 3% on Jito tips distributed via the Tip Router.
* The RevTec validator takes a 10% commission on issuance rewards, used to fund protocol development. This fee may be revised following mainnet launch.

RevTec reserves the right, at its sole discretion and with reasonable notice where practicable, to: (i) change validator delegation to include multiple external validators, including following the anticipated implementation of SIMD-123 on Solana mainnet; (ii) introduce protocol-level fees separate from validator-level fees; (iii) reduce or eliminate the validator commission; and (iv) migrate the REV distribution mechanism from the Jito Tip Router to a native on-chain mechanism once SIMD-123 is implemented. Any such changes will be disclosed via the Interfaces.

### D. DeFi Composability

revSOL and issSOL are freely composable with third-party DeFi protocols. The Interfaces may provide links or integrations to third-party protocols including, without limitation, Exponent Finance (for yield trading and fixed-yield strategies using revSOL) and Kamino (for leveraged yield strategies). Your use of any such third-party protocol is entirely at your own risk, subject to the terms of those protocols, and is not endorsed, supervised, or guaranteed by RevTec. RevTec has no control over, and accepts no responsibility for, any third-party protocol.

### E. Non-Custodial Nature; No RevTec Involvement in Transactions

None of the Interfaces allow RevTec to engage in any transaction with you, nor do the Interfaces facilitate your transactions. Even when the Interfaces appear to be dynamic, RevTec is not at any time taking action directed by you or on your behalf. If you connect your self-hosted cryptocurrency wallet ("Wallet") to an Interface, RevTec (i) is not involved in providing or transmitting information to blockchain networks, (ii) cannot transmit information to networks or otherwise assist in any transaction, (iii) never has access to and cannot control your Wallet, and (iv) has no authority over and does not take possession or custody of your cryptoassets at any time.

You are solely responsible for familiarising yourself with your Wallet and its security features, including any private keys and passwords. RevTec cannot access your private key, password, or cryptoassets, nor can it reverse any transactions you initiate. RevTec shall not be responsible or liable in any way for how you use your Wallet.

All transactions broadcast to the Solana network via your Wallet may require the payment of non-refundable network transaction fees, which shall be borne entirely by you.

### F. Your Acknowledgement Relating to Information on the Interfaces

All information provided in connection with your access and use of the Interfaces is intended for informational purposes only. RevTec strives to provide accurate information but does not guarantee that it is updated, complete, or timely. You acknowledge that you are not relying on any information on the Interfaces for any purpose and expressly disclaim any reliance on it.

None of the information on the Interfaces should be construed as professional, investment, tax, or financial advice. Nothing on the Interfaces constitutes an invitation or inducement to acquire, dispose of, underwrite, or convert any cryptoassets or digital assets.

## III. Modifications

We reserve the right, in our sole discretion, to modify the Terms at any time. Modified Terms will be posted on the Interface with an updated date and will become effective upon posting. By continuing to use any Interface or Feature after the effective date of any modification, you agree to be bound by the updated Terms.

We also reserve the right to modify, suspend, or discontinue the Interfaces, Features, or the protocol itself (including its smart contracts, validator delegation strategy, fee structure, and REV distribution mechanism) at any time, with or without notice. We owe you no obligation to continue providing any Interface or Feature under any circumstances.

## IV. Your Responsibilities and Representations

### A. Your Representations

The Interfaces and Features are intended only for users who are 18 years of age or older. If you are entering into the Terms on behalf of an entity, you represent that you have the legal authority to bind such entity.

You represent and warrant that you are not, and will not be during your use of the Interfaces and Features: (i) the subject of economic or trade sanctions administered or enforced by any governmental authority, or otherwise designated on any list of prohibited or restricted parties; (ii) in contravention of any laws pertaining to anti-money laundering or terrorist financing; (iii) included on the List of Specially Designated Nationals and Blocked Persons maintained by OFAC, or on any list pursuant to European Union (EU) and/or United Kingdom (UK) regulations; or (iv) operationally based or domiciled in a country or territory subject to sanctions imposed by the United Nations, OFAC, the EU, or the UK.

You acknowledge and agree that you have the financial and technical sophistication to use and interact with the Interfaces and Features, and that you understand the inherent risks of blockchain technology. You understand that:

* Transacting in cryptoassets is risky and may subject you to cyberattack, loss of cryptoassets, smart contract exploits, liquidity risk, and other risks related to blockchain transactions.
* Transactions executed via smart contracts are generally not reversible and you may have no recourse in the event of a malicious, fraudulent, or inadvertent transaction.
* revSOL carries volatile yield exposure: because all REV rewards generated by the entire staked SOL pool are concentrated into the revSOL backing, even small changes in Solana's REV yield will produce amplified changes in revSOL's APY relative to standard staking.
* issSOL carries a gradually declining yield: issuance rewards decrease over time per Solana's inflation schedule and may be further affected by changes to the proportion of SOL that is staked network-wide.
* The REV/Issuance Ratio shifts over time as the two yield sources accumulate at different rates, which affects the terms on which you can mint and redeem tokens.
* Liquidity for revSOL and issSOL on DEXs is not guaranteed. Your ability to swap or exit positions efficiently depends on market depth, which RevTec does not control.
* The protocol's infrastructure — including its validator delegation, fee mechanisms, and REV distribution method — may change over time as described in Section II.C above.

### B. Prohibited Conduct

You agree to access and use the Interfaces and Features only in an authorised, proper, and lawful manner. You agree that you will not:

* Violate any applicable laws or regulations or these Terms.
* Exploit the Interfaces or Features for any unauthorised purpose.
* Harvest or collect information from the Interfaces or Features for any unauthorised purpose.
* Use the Interfaces or Features in any manner that could disable, overburden, damage, or impair them.
* Reverse engineer, disassemble, or decompile the Interfaces or Features, except to the extent expressly permitted by applicable law.
* Sublicense, sell, or otherwise distribute the Interfaces, Features, or any portion thereof.
* Use data mining tools, robots, crawlers, or similar tools to scrape data from the Interfaces or Features.
* Introduce any viruses, trojan horses, worms, logic bombs, or other malicious or technologically harmful material.
* Attempt to gain unauthorised access to, or interfere with, any parts of the Interfaces or Features, or any connected server or database.
* Attack the Interfaces or Features via a denial-of-service or distributed denial-of-service attack.

You acknowledge that interacting with the Interfaces or Features may result in tax consequences, including in connection with receiving, holding, swapping, or redeeming revSOL or issSOL. It is solely your responsibility to determine and comply with your applicable tax obligations. You are strongly encouraged to consult a local tax adviser.

### C. Feedback

You may provide feedback, questions, or inquiries through the Interfaces. We welcome feedback relating to the Interfaces or Features but are not obligated to review it or implement any suggestions. You agree that RevTec will own all right, title, and interest in and to any feedback you submit.

## V. Intellectual Property Rights

### A. Ownership and Licence

RevTec or its licensors own all right, title, and interest, including all intellectual property rights, in and to the Interfaces and Features. Subject to the Terms, RevTec grants you a personal, limited, revocable, non-exclusive, non-sublicensable, non-transferable licence to use the Interfaces and Features solely for the purpose of accessing and interacting with them.

### B. Reciprocal Licence

By using any Interface or Feature, you grant RevTec a limited, non-exclusive, sublicensable, worldwide, royalty-free licence to use, copy, modify, and display any content or feedback you provide solely for RevTec's business purposes, including providing the Interfaces and Features.

### C. RevTec Trademarks

RevTec graphics, logos, page headers, button icons, scripts, and service names are trademarks, registered trademarks, or trade dress of RevTec (the "RevTec Marks"). All other trademarks appearing on the Interfaces are the property of their respective owners. You may use RevTec Marks only in accordance with these Terms. You may link to the Interfaces provided you do so in a way that is fair and legal and does not damage our reputation, but you must not suggest any form of association, approval, or endorsement on our part without our express written consent.

## VI. Third Party Information or Services

The Interfaces and Features may integrate with or provide access to third-party applications, services, sites, technology, data, or resources (

"Third Party Services"). These include, without limitation, Exponent Finance, Kamino, Raydium, Jito, and other DeFi protocols with which revSOL or issSOL may be integrated.

We have no control over Third Party Services and accept no responsibility for them or for any loss or damage that may arise from your use of them. Your access to and use of Third Party Services is entirely at your own risk and subject to the terms of those services. The integration or inclusion of Third Party Services does not constitute an endorsement by RevTec.

## VII. Indemnification

### A. General

You agree to defend, indemnify, and hold harmless RevTec and its representatives, contributors, contractors, employees, supervisors, directors, and licensors (collectively, the "RevTec Parties") from and against all liability, damages, losses, fines, penalties, and reasonable attorney's fees arising out of or relating to: (i) your use of the Interfaces or Features; (ii) breach of the Terms or violation of applicable law by you; (iii) a dispute between you and any third party; (iv) your alleged or actual infringement of any third party's intellectual property or other rights; and (v) your feedback.

### B. Process

If you are obligated to indemnify RevTec, RevTec will have the right to control any action or proceeding and to determine whether to settle and on what terms, and you agree to cooperate fully in the defence or settlement of such claim.

## VIII. Disclaimers and Limitations of Liability

### A. Interfaces and Features

By accessing the Interfaces or Features, you acknowledge that RevTec cannot and does not guarantee their functionality, security, or availability. The technologies on which the Interfaces and Features rely may be subject to sudden changes. You assume all risks related thereto.

### B. No Representations or Warranties

THE INTERFACES AND FEATURES ARE PROVIDED "AS IS." EXCEPT TO THE EXTENT PROHIBITED BY LAW, NEITHER REVTEC NOR ANY OTHER REVTEC PARTY MAKES ANY REPRESENTATIONS OR WARRANTIES OF ANY KIND, WHETHER EXPRESS, IMPLIED, STATUTORY, OR OTHERWISE, AND REVTEC PARTIES EXPRESSLY DISCLAIM ALL WARRANTIES, INCLUDING ANY IMPLIED OR EXPRESS WARRANTIES (I) OF MERCHANTABILITY, SATISFACTORY QUALITY, FITNESS FOR A PARTICULAR PURPOSE, NON-INFRINGEMENT, OR QUIET ENJOYMENT, (II) ARISING OUT OF ANY COURSE OF DEALING OR TRADE USAGE, (III) THAT THE INTERFACES OR FEATURES WILL BE ACCURATE, UNINTERRUPTED, ERROR-FREE, OR FREE OF HARMFUL COMPONENTS, AND (IV) THAT ANY CONTENT OR ASSETS WILL BE SECURE OR NOT OTHERWISE LOST OR ALTERED.

### C. Protocol-Specific Disclaimers

Without limiting the generality of the foregoing, RevTec specifically does not warrant or guarantee:

* The future yield, APY, or value of revSOL or issSOL. REV yield is variable and depends on Solana network activity, which is inherently unpredictable. Issuance yield declines over time and may be subject to changes in Solana's inflation schedule, including as a result of future governance proposals.
* The availability of DEX liquidity for revSOL or issSOL at any time. You may not be able to swap or exit positions at a favourable price or at all.
* The continued operation of the Jito Tip Router or any other third-party infrastructure used to distribute REV. Changes to Jito's fee structure or the implementation of SIMD-123 or other Solana protocol upgrades may affect how REV is distributed.
* The performance of the RevTec validator or any future validators to which stake may be delegated. Validator underperformance may reduce the yield earned by revSOL and issSOL holders.
* The correctness or security of the RevTec smart contracts. Notwithstanding the protocol audit completed in November 2025 by Accretion, no audit can guarantee the absence of bugs, vulnerabilities, or exploits.

### D. Limitations of Liability

REVTEC PARTIES WILL NOT BE LIABLE TO YOU FOR ANY INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, OR EXEMPLARY DAMAGES (INCLUDING DAMAGES FOR LOSS OF PROFITS, REVENUES, CUSTOMERS, OPPORTUNITIES, GOODWILL, USE, DATA, OR OTHER ASSETS), EVEN IF REVTEC PARTIES HAVE BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES. NONE OF THE REVTEC PARTIES WILL BE RESPONSIBLE FOR ANY COMPENSATION, REIMBURSEMENT, OR DAMAGES ARISING IN CONNECTION WITH (I) YOUR INABILITY TO USE THE INTERFACES OR FEATURES; (II) THE COST OF SUBSTITUTE GOODS OR SERVICES; (III) ANY INVESTMENTS, EXPENDITURES, OR COMMITMENTS YOU MAKE IN CONNECTION WITH THE TERMS OR YOUR USE OF THE INTERFACES OR FEATURES; (IV) ANY UNAUTHORISED ACCESS TO, ALTERATION OF, OR DELETION, DESTRUCTION, DAMAGE, LOSS, OR FAILURE TO STORE ANY OF YOUR DATA; OR (V) ANY CHANGE IN VALUE OF ANY CRYPTOASSET, INCLUDING REVSOL OR ISSSOL. IN ANY CASE, REVTEC PARTIES' AGGREGATE LIABILITY UNDER THESE TERMS WILL NOT EXCEED €100. THE LIMITATIONS IN THIS SECTION APPLY TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW.

## IX. Governing Law, Dispute Resolution, and Class Action Waiver

### A. Governing Law

These Terms — and your use of the Interfaces and Features — are governed by the laws of Austria, without regard to conflict of laws rules. Any arbitration commenced against RevTec is subject to the Arbitration Rules of Austrian law, and the parties submit to the non-exclusive jurisdiction of the competent courts of Vienna, Austria, for any matters not subject to arbitration.

### B. Dispute Resolution

Prior to commencing any legal proceeding, you and RevTec agree to attempt to resolve any claim by engaging in good faith negotiations. The aggrieved party must provide written notice specifying the nature and details of the dispute. The receiving party has twenty days to respond. The parties shall meet and confer in good faith within forty-five days of such notice. If unresolved within ninety days, either party may submit the dispute to arbitration.

### C. Mandatory Arbitration

Any dispute, claim, or controversy arising out of or relating to these Terms, the Interfaces, or the Features — including the determination of the scope or applicability of this arbitration agreement — shall be determined by arbitration in Austria before one arbitrator. This clause does not preclude parties from seeking provisional remedies in aid of arbitration from a court of appropriate jurisdiction.

YOU UNDERSTAND THAT BY AGREEING TO THESE TERMS, YOU ARE EACH WAIVING THE RIGHT TO A TRIAL BY JURY OR TO PARTICIPATE IN A CLASS ACTION OR CLASS ARBITRATION.

### D. Waiver of Class Action

Any arbitration under these Terms will take place on an individual basis. Class arbitrations and class actions are not permitted. To the fullest extent permitted by applicable law, you agree that any proceeding to resolve any dispute will be brought and conducted only in your individual capacity and not as part of any class, consolidated, or representative proceeding.

### E. Survival of Arbitration Agreement

If you cease using the Interfaces or Features based on updates to the Terms, your agreement to arbitrate and your waiver of class action claims remain in full force and effect.

## X. No Relationship or Assignments

Nothing in these Terms shall be construed to create any relationship between you and RevTec other than as defined herein. Neither party is an agent of the other. You may not assign or transfer any of your rights or obligations under the Terms. RevTec may assign or transfer the Terms, in whole or in part, without restriction. Subject to the foregoing, the Terms shall be binding upon the parties and their respective permitted successors and assigns.

## XI. Entire Agreement

These Terms, including any policies that expressly incorporate them by reference, constitute the entire agreement between you and RevTec regarding their subject matter and supersede all prior representations, understandings, agreements, or communications between you and RevTec, whether written or verbal.

## XII. No Waiver

The failure by RevTec to enforce any provision of the Terms will not constitute a present or future waiver of such provision nor limit RevTec's right to enforce that provision at a later time. All waivers must be in writing to be effective.

## XIII. Severability

If any portion of the Terms is held to be invalid or unenforceable, the remaining portions will remain in full force and effect. Any invalid or unenforceable portion will be interpreted to effectuate the intent of the original portion. If such construction is not possible, the invalid or unenforceable portion will be severed from the Terms but the rest will remain in full force and effect.

<br>
