# Mainnet Addresses

RevTec **v2** on Solana mainnet-beta. These addresses are public on-chain; integrators and partners can use them to build against the protocol without access to private repositories.

**App:** [app.revtec.fi](https://app.revtec.fi)

**Deployed:** 2026-06-02 (v2 LSP program)

---

## Program

| Item | Address |
|------|---------|
| **RevTec LSP program (v2)** | [`59k5msuGtD4oCnkYStGSF7kjeBVynQLNtmYjfg79P7V6`](https://solscan.io/account/59k5msuGtD4oCnkYStGSF7kjeBVynQLNtmYjfg79P7V6) |

---

## Liquid staking tokens (SPL mints)

| Token | Mint | Decimals |
|-------|------|----------|
| **revSOL** | [`HgEWmCePuhRwrTQMnV7Z4oHiNfjbVZHFXA9XfT9DN3FV`](https://solscan.io/token/HgEWmCePuhRwrTQMnV7Z4oHiNfjbVZHFXA9XfT9DN3FV) | 9 |
| **issSOL** | [`2AvFj4iGTpZnrRo7vLuTMoNNfE7VKAK4SpiJfTnu6Nmq`](https://solscan.io/token/2AvFj4iGTpZnrRo7vLuTMoNNfE7VKAK4SpiJfTnu6Nmq) | 9 |

Fair value (exchange rate vs SOL):

- `rev_fair = rev_backing_lamports / rev_supply`
- `iss_fair = iss_backing_lamports / iss_supply`

Live fair values are shown on [app.revtec.fi](https://app.revtec.fi) and via the protocol API.

---

## Core protocol accounts

| Account | Address |
|---------|---------|
| Global config | [`BtXxdzHbvefJocC5juZenj51oKEXUW5QiJazhneTMiEh`](https://solscan.io/account/BtXxdzHbvefJocC5juZenj51oKEXUW5QiJazhneTMiEh) |
| Validator pool | [`9E5eopr7uYKURFJMc2183mBewoXETFRPQhfAuVwBzaM`](https://solscan.io/account/9E5eopr7uYKURFJMc2183mBewoXETFRPQhfAuVwBzaM) |
| Withdraw treasury | [`3mhu3pYdzvh7UsKJvyJy7VhCoLapYF3SJaVj521BPkC2`](https://solscan.io/account/3mhu3pYdzvh7UsKJvyJy7VhCoLapYF3SJaVj521BPkC2) |
| REV yield treasury | [`28jQNoSxTHiDRWEZ17ezrXwcj4J2rdVrKmya7Kp8aKX3`](https://solscan.io/account/28jQNoSxTHiDRWEZ17ezrXwcj4J2rdVrKmya7Kp8aKX3) |

---

## Validator

All SOL deposited through RevTec is staked with the RevTec validator:

| Item | Address |
|------|---------|
| Vote account | [`B1rsc6jv3RsFpkak8qvJN3PfGYSg9E3Uw1joaV1EoiFj`](https://stakewiz.com/validator/B1rsc6jv3RsFpkak8qvJN3PfGYSg9E3Uw1joaV1EoiFj) |
| Validator PDA (program) | [`GXHFUt461HhNn3Co77ixQoFhTNeyPiueM6nmLM1RQN1E`](https://solscan.io/account/GXHFUt461HhNn3Co77ixQoFhTNeyPiueM6nmLM1RQN1E) |
| Primary stake account | [`3UFXnHhnRaYht3bTtR3zz4jVNqUYJnVyFCWDb2xUGb63`](https://solscan.io/account/3UFXnHhnRaYht3bTtR3zz4jVNqUYJnVyFCWDb2xUGb63) |

---

## Raydium CLMM pools (mainnet)

Secondary liquidity for revSOL and issSOL (not protocol-owned):

| Pair | Pool ID |
|------|---------|
| SOL / revSOL | [`9DPVxPpWxzHcFMbUNQnLi8QgeK9kQfR4KVqoZ5dYMkWg`](https://raydium.io/clmm/create-position/?pool_id=9DPVxPpWxzHcFMbUNQnLi8QgeK9kQfR4KVqoZ5dYMkWg) |
| SOL / issSOL | [`EF7uDWcA928i5zWMZUpRD3Vx3vuit3J1epC9xy2mnA5D`](https://raydium.io/clmm/create-position/?pool_id=EF7uDWcA928i5zWMZUpRD3Vx3vuit3J1epC9xy2mnA5D) |
| issSOL / revSOL | [`8GCN3a5aHVZw1d1zCtxb8NVyePH4yDjQFQLtgJqZGmiN`](https://raydium.io/clmm/create-position/?pool_id=8GCN3a5aHVZw1d1zCtxb8NVyePH4yDjQFQLtgJqZGmiN) |

---

## Integrators

For **Anchor IDL**, TypeScript client, or integration questions, contact the team via [Feedback & Contact](feedback-and-contact.md).

Protocol behavior (deposits, withdrawals, yield cranks, splits) is documented in [Protocol Design](../design/protocol-design.md).
