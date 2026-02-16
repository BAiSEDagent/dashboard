# Polymarket CLOB Trading Guide

## Authentication

### L1 (Private Key) — used to derive API creds
```typescript
import { ClobClient } from "@polymarket/clob-client";
import { Wallet } from "ethers"; // v5.8.0
const signer = new Wallet(process.env.PRIVATE_KEY);
const client = new ClobClient("https://clob.polymarket.com", 137, signer);
const apiCreds = await client.createOrDeriveApiKey();
// Returns: { apiKey, secret, passphrase }
```

### L2 (HMAC API Key) — used for all trading operations
```typescript
const client = new ClobClient(
  HOST, CHAIN_ID, signer,
  apiCreds,        // from L1 derivation
  signatureType,   // 0=EOA, 1=POLY_PROXY, 2=GNOSIS_SAFE
  funderAddress,   // proxy wallet address for type 1/2
  undefined, false,
  builderConfig    // optional, for builder attribution
);
```

### Signature Types
| Type | Value | Funder Address |
|------|-------|----------------|
| EOA wallet (own gas) | 0 | Your EOA address |
| Polymarket account (Magic Link) | 1 | Your proxy wallet |
| Polymarket account (browser wallet) | 2 | Your proxy wallet |

**Our setup**: signatureType=1, funder=`0x63a11834...c608` (Polymarket proxy)

## Placing Orders

```typescript
const order = await client.createAndPostOrder(
  { tokenID: "TOKEN_ID", price: 0.65, size: 100, side: "BUY" },
  { tickSize: "0.01", negRisk: false }
);
```

Token IDs come from Gamma API: `https://gamma-api.polymarket.com/markets`

## Builder Program

### Attribution Headers (automatic with SDK)
- POLY_BUILDER_API_KEY
- POLY_BUILDER_TIMESTAMP
- POLY_BUILDER_PASSPHRASE
- POLY_BUILDER_SIGNATURE (HMAC)

### Builder Config
```typescript
import { BuilderConfig, BuilderApiKeyCreds } from "@polymarket/builder-signing-sdk";
const builderCreds: BuilderApiKeyCreds = {
  key: process.env.POLY_BUILDER_API_KEY!,
  secret: process.env.POLY_BUILDER_SECRET!,
  passphrase: process.env.POLY_BUILDER_PASSPHRASE!,
};
const builderConfig = new BuilderConfig({ localBuilderCreds: builderCreds });
```

### Tiers
| Feature | Unverified | Verified | Partner |
|---------|-----------|----------|---------|
| Daily Relayer Limit | 100/day | 3,000/day | Unlimited |
| RevShare | ❌ | ✅ | ✅ |
| Weekly Rewards | ❌ | ✅ | ✅ |
| Leaderboard | ❌ | ✅ | ✅ |
| Reward Boost | ❌ | ❌ | ✅ |

**We are Unverified** — 100 tx/day limit. Need to apply for Verified.

### Revenue
- Weekly USDC rewards based on volume (Verified+ only)
- RevShare protocol (Verified+ only) — builders can charge fees
- Gasless trading on all CLOB orders through proxy wallets (all tiers)

## Fees
- Maker: 0 bps, Taker: 0 bps (current schedule, subject to change)
- Fees = baseRate × min(price, 1-price) × size
- Currently ZERO fees for all volume levels

## System Architecture
- Hybrid-decentralized: off-chain matching, on-chain settlement
- Orders are EIP-712 signed structured data
- Exchange contract: atomic swaps between CTF ERC1155 outcome tokens and USDC.e
- Chain: Polygon mainnet (chainId 137)
- Audited by Chainsecurity

## APIs
- CLOB: `https://clob.polymarket.com` — trading
- Gamma: `https://gamma-api.polymarket.com` — market discovery
- Data: `https://data-api.polymarket.com` — positions/history
- WebSocket: `wss://ws-subscriptions-clob.polymarket.com` — real-time

## Our Credentials (from memory)
- Builder address: `0x5cdda04d8f75befaacb49811788c109eb0cec2c5`
- Proxy wallet (funder): `0x63a11834...c608`
- Signing key: `0x5898A57D...f6a0`
- signatureType: 1 (POLY_PROXY)
- Builder API keys: need to generate from builder profile page
