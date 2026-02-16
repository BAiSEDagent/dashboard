# MEMORY.md - Long-Term Memory

## 2026-02-14 — Rebuild after update wipe

- Lost all memory and identity files after an update on Feb 13
- Adam provided the full BAiSED system prompt to rebuild from
- Identity restored: BAiSED — Base ecosystem Principal Engineer / DevRel oracle / AI agent
- Could not read back Telegram history (no fetch tool available) — memory is incomplete pre-Feb 14
- Rebuilt project knowledge by cloning and reviewing all 8 GitHub repos
- Adam sent RTF export of full Telegram chat history (Part 1) — ingested below

## Identity Core

- Name: BAiSED
- Role: Principal Engineer, DevRel oracle, autonomous AI agent for Base ecosystem
- Operator: Adam (@atescch)
- North star: Most trusted intelligence and developer guide in Base ecosystem; help Adam build real, valuable software

## Projects

### openclaw-skills (https://github.com/BAiSEDagent/openclaw-skills)
- My skill library — 79 skills across 26 commits
- Covers: Base ecosystem, smart contracts, Solidity, Foundry, Hardhat, security audits, x402 payments, ERC-8004, ERC-8128, DeFi, trading (spot/futures/leverage/market-making), CDP wallets, onchain analytics, DevRel/content, web scraping, Python, TypeScript, React Native, iOS, monitoring, webhooks, and more
- Compatible with OpenClaw and other agentic IDEs
- Cloned locally at /tmp/openclaw-skills

### Cogent (https://github.com/BAiSEDagent/cogent) — PRIVATE
- AI agent trading infrastructure for Polymarket prediction markets
- Multi-agent platform: provisions wallets, enforces risk limits, routes orders through Polymarket CLOB
- Dashboard: Arena view with leaderboard, live activity, portfolio chart, top markets sidebar
- 4 agent strategies built: Arbitrage Scanner, Whale Tracker, Contrarian (mean reversion), Sentiment (news/social)
- Risk engine: position limits (20%), drawdown breaker (30%), exposure caps, diversification rules
- Revenue model: builder fees (Polymarket), agent prizes, copy-trading vaults (Phase 2)
- Also has a Farcaster Mini App scaffold with security audit (7 findings, 3 fixed)
- Tech: TypeScript, Express, WebSocket, Next.js mini app

### AgentHQ / BAiSE / Pact (https://github.com/BAiSEDagent/agenthq) — PRIVATE
- Multi-agent coordination platform — "the OS for AI agent teams"
- Rebranded: AgentHQ → BAiSE
- Core loop: agents discover each other, negotiate tasks, execute, settle payment
- SDK: @baised/sdk v0.2.0 — register, discover, create tasks, bid, execute, settle
- x402 payment settlement integrated and live
- 3 rounds of security audits completed (36+ findings fixed)
- Roadmap: Phase 0 (foundation) → Phase 1 (arbitration escrow) → Phase 2 (staking & on-chain reputation)
- Escrow design: USDC locked on task assignment, arbitrator agent resolves disputes
- Tech: Node.js/Express, SDK with TypeScript definitions
- UI overhaul done: Dashboard, Payments page (Sankey chart, transaction table), Workflows (ReactFlow), Agent profiles
- Phase 1 (payments): agents table + walletAddress/basename/reputationScore, payment_events table, self-registration endpoint, chain config with Base Sepolia defaults
- Phase 2 (x402): x402 middleware wired in, payment webhook auto-records to DB, frontend Payments wired to real API
- Phase 3 (EAS reputation): Agent profile endpoint with EAS attestation queries, reputation scoring
- bcrypt → bcryptjs migration (native module issues on Render)
- esbuild bundling with native module externals
- Deployed/deploying on Render

### x402-sessions (https://github.com/BAiSEDagent/x402-sessions) — PRIVATE
- Session Gateway for x402 payments — "Stripe for agents, but permissionless"
- Sign wallet once, set spending limit, get JWT API key
- Built on Coinbase SpendPermissionManager (spend permissions)
- 3 lines of code to add USDC micropayments to any API
- Auto-settles USDC on Base after each response
- Optional EAS receipt attestations
- Package: @baised/x402-sessions

### x402-paywall-skill (https://github.com/BAiSEDagent/x402-paywall-skill) — PRIVATE
- x402 Paywall Skill for OpenClaw — HTTP 402 micropayments with USDC
- Full project: contracts, src, tests, Docker, audit, architecture docs
- Has SKILL.md for OpenClaw integration
- USDC Hackathon submission — Track 2 "Best OpenClaw Skill"
- **V1 (prototype):** Pay-onchain-then-verify-txHash pattern
  - Buyer agent built: two wallets, real USDC on Base Sepolia, end-to-end flow proven
  - Facilitator contract V1 deployed at 0x28a1217aB0919ABc071EA101108d8ad4BbE7913e
  - 18 integration tests passing
  - Demo server deployed on Render (live endpoints: /, /health, /premium returning 402)
  - Seller wallet: 0xf30FEA48Eb39d2b17409dae7160054999Cac61a5
  - Demo wallet: 0x55ea5a71f37f6E352b42Ec3da09F2172ae49d922
  - Real on-chain proof: approve → submit → settle → withdraw transactions confirmed
- **V2/V3 (TypeScript rewrite — EIP-712/EIP-3009):**
  - Full TypeScript rewrite with strict types
  - EIP-712 typed data signing (gasless for buyer — buyer signs, server settles atomically)
  - V2 contract (PaymentFacilitatorV2.sol): DOMAIN_SEPARATOR, PAYMENT_TYPEHASH, usedNonces, ReentrancyGuard
  - V2 contract deployed at 0x7b5228... (Base Sepolia)
  - Steps 1-7 completed: TS setup, types, EIP-712 signer (29 tests), Solidity contract, deploy, server verification, client
  - Steps 8-10 remaining: integration test, buyer agent update, EAS integration
  - Vitest test framework
  - npm pack produces 55.4kB clean package
- **Publisher (BAiSED Publisher / Twin.so):** Reviewed code 3 times, provided architecture spec, 10-step implementation plan, definition of done checklist

### x402.eco (https://github.com/BAiSEDagent/x402.eco) — PUBLIC FORK
- Fork of x402.org ecosystem site
- Added: AgentHQ listing, Skills tab, meta-skill section, ecosystem contributor guide
- Added Upstash Redis caching for Allium data, Plausible analytics
- Next.js app with Vercel deployment
- Working on branch: add-agenthq

### base-developer-toolkit (https://github.com/BAiSEDagent/base-developer-toolkit) — PUBLIC
- USDC Hackathon Submission — "Best OpenClaw Skill" track
- 4 skills bundled: base-technical, basenames, x402, smart-wallet
- Focus: USDC-native applications on Base L2
- Covers: ERC-8004 identity, x402 micropayments, basenames (.base), ERC-4337 smart wallets

### skills (https://github.com/BAiSEDagent/skills) — PUBLIC
- Older/original SMP skill library (pre-openclaw-skills)
- 11 skills: base-docs, base-ecosystem, base-technical, circle-wallet, content-strategy, engagement-targets, onchainkit, twitter, x402, plus a skills subfolder

## On-Chain Identity
- Basename: baisedagent.base.eth
- GitHub: BAiSEDagent
- Twitter/X: @baised_agent
- Account created: Feb 5, 2026

## Five-Layer Stack (Strategic Framework)
- Layer 5: Settlement → Stripe / x402 / Tempo / AgentKit (COMMODITY)
- Layer 4: Sessions → Spend Sessions (OUR primitive)
- Layer 3: Coordination → Pact/BAiSE (discovery, negotiation, task routing)
- Layer 2: Auth → ERC-8128 (signed HTTP requests)
- Layer 1: Identity → ERC-8004 + EAS (live Ethereum Mainnet + 12 chains)
- Pitch: "Stripe is the cash register. We're the marketplace."

## Contract Addresses
- Identity Registry: 0x8004A169FB4a3325136EB29fA0ceB6D2e539a432
- Reputation Registry: 0x8004BAa17C55a88189AE136b182e5fdA19dE9b63
- EntryPoint (ERC-4337): 0x0576a174D229E3cFA37253523E645A78A0C91B57
- USDC on Base: 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913
- EAS Schema UID: 0xb20b7510235cc8546bacec919a8009379a97c3aab1c4447e64994c4b8e84ea0e

## Funding Opportunities
- Jason Calacanis / Launch.co — $25K seed (email: openclaw@launch.co)
- Virtuals Protocol — $10K stipends + credits
- Base Batches — up to $1M at demo day
- Base Grants — 1-5 ETH, self-nomination

## Key People / Agents
- **BAiSED Publisher** — operates on Twin.so, reviewed x402-paywall-skill 3 times, provided architecture spec, talked with JesseXBT about EAS caching and EIP-712
- **JesseXBT** — AI AGENT (not human Jesse Pollak), trained on Jesse's content, Base's builder quality gate. First submission scored 0.43. Co-designed Clawdbot spec. Top 10% get warm intro to real Jesse Pollak. Engaged with Publisher on technical details (EAS cache invalidation, chain auto-detection, staged mainnet testing). Respects honesty, pushes into implementation details, skeptical of hype. "Don't pitch him — have a conversation. Ask what he'd change."
- **GPT-5.2** — Adam had a separate GPT-5.2 agent review the x402-paywall-skill repo

## USDC Hackathon (Moltbook)
- 30,000 USDC prize pool — 10K per track
- Track 2: "Best OpenClaw Skill" — our target
- Submission format: `#USDCHackathon ProjectSubmission Skill` on m/usdc
- Must vote on 5+ other projects for eligibility
- Deadline was Feb 8, 2026 (likely passed)
- Submission status: unclear if we submitted in time

## Reference Skills Installed
- security-best-practices (OpenAI) — Express + React audit rules
- security-threat-model (OpenAI) — AppSec threat modeling from repo
- gh-fix-ci (OpenAI) — GitHub Actions debugging
- render-deploy (OpenAI) — Render deployment blueprints
- mcp-builder (Anthropic) — MCP server guide
- webapp-testing (Anthropic) — Playwright testing

## Technical Lessons Learned
- RPC read lag: after tx confirmation, the RPC node may not have updated state for the next read. Add delays or use event-based confirmation.
- Native module bundling: bcrypt/better-sqlite3 can't be bundled by esbuild. Use bcryptjs (pure JS) or externalize native modules.
- Render deployment: NODE_ENV=production skips devDependencies. Move runtime deps to regular deps.
- EIP-712 field ordering MUST match Solidity struct ordering — silent failure if mismatched.
- Real x402 uses EIP-3009 transferWithAuthorization (USDC native) — buyer signs (gasless), facilitator executes atomically.
- "Proof of use > proof of deploy" — the buyer agent demo was the turning point.
- Don't inflate claims. Count transactions accurately. Say "enabled" not "fixed."

## Cogent (Polymarket Trading Platform)
- AI agent trading infrastructure for Polymarket prediction markets
- Named "Cogent" — agents deposit USDC, trade autonomously, humans copy-trade
- 4 strategies: Whale Tracker, Arbitrage Scanner, Contrarian, Sentiment
- Builder address: 0x5cdda04d8f75befaacb49811788c109eb0cec2c5
- Revenue: builder fee share from Polymarket trades
- Competitor AIXBET analyzed — token-gated garbage, confirmed our approach (real revenue, no tokens)
- Dashboard: Arena view, leaderboard, activity feed, market explorer

## AgentHQ → BAiSE Rebrand
- GitHub launched "Agent HQ" feature → name conflict
- Brainstormed: Pact (briefly locked), then BAiSE (Base AI Service Exchange)
- French double meaning acknowledged, deemed acceptable
- Domains explored: baise.work, baise.network, baise.exchange — not yet purchased
- Name may still change

## Stripe + x402 (Feb 10)
- Stripe launched machine payments using x402 on Base with USDC
- Jeff Weinstein (Stripe product) announced it
- Strategic pivot: "Stripe handles settlement. We handle everything Stripe can't."
- Spend Sessions = 500x fewer on-chain transactions vs raw PaymentIntents

## Tempo (Coinbase Payments L2)
- Purpose-built payments chain by Coinbase
- Partners: Anthropic, OpenAI, Visa, Mastercard, Deutsche Bank, UBS, etc.
- Testnet live Feb 2026, mainnet likely Q2-Q3
- viem has Tempo chain definitions built in
- "Settlement is infrastructure. Coordination is the product."
- Tempo explicitly invites coordination layers to build on top

## ERC-8128 (HTTP Request Signing)
- Completes the stack: Identity (8004) → Auth (8128) → Payment (x402) → Reputation (EAS) → Coordination (AgentHQ)
- Stateless client auth via Ethereum signatures, no API keys
- @slicekit/erc8128 TypeScript library available
- Combined with ERC-8004: register once, sign every request

## npm Published
- @baised/agenthq@0.1.0 on npm
- npm org: baised
- Token: granular, 90-day, 2FA bypass

## Credentials on File
- Etherscan API key stored
- CDP API key + Wallet Secret stored
- Polymarket CLOB API keys + wallet private key in .env
- All in .env files, gitignored, server-side only

## x402-sessions Audit History
- Round 1: 7 critical + 5 high → all fixed (commit 2ab182d)
- Round 2: 5 specialist agents, 10 consolidated findings → all fixed (commit 4ee5aa3)
- Round 3: AgentHQ server — 36 findings across 3 passes → all fixed
- Key lesson: "Clean TypeScript creates false confidence. Write threat model BEFORE code."
- Rule: THREATS.md before src/ exists

## Revenue Model
- Low fees, high volume (Stripe model)
- 1-2% platform fee on task settlements
- No high fees — "volume and low fees to fund us"
- Marketing idea: 100 × $1 bounties → recruit 1000 agents for $100

## Adam's Wallet Drain (Feb 12)
- $179.87 USDC.e stolen from `0x23a473...282e` on Polygon
- Drain address: `0x351f65...403e` — multiple victims, consolidated 53K USDC.e
- Wallet is BURNED — never use again
- Was the money Adam planned to fund Cogent with
- Made the audit lessons visceral

## Cogent Trading Status
- 4 agents built, paper trading works
- Live trading BLOCKED: Polymarket CLOB returns 403 from US IPs
- VPN installed on Mac mini but doesn't route Node.js traffic
- Adam placed 2 manual trades via browser: Gov Shutdown YES, Iran Strikes YES
- Portfolio: $119.84 cash + positions
- Proxy wallet: `0x63a11834...c608` (Polymarket), signing key: `0x5898A57D...f6a0`
- Need VPS in Europe or proper VPN routing for automated trading

## Cogent Mini App (Farcaster)
- Scaffolded: Next.js 16, 1,308 lines, 23 files
- Threat model written first (new process worked!)
- Audited: 7 findings, 0 critical, all fixed
- Not yet deployed to Vercel

## Development Process Evolution
- **"Standard over speed"** — Adam's core directive, non-negotiable
- THREAT_MODEL.md required before any code
- Module-by-module builds with inline audits
- Always Opus 4.6 for everything including sub-agents
- "Never confuse velocity with value"
- Secure module template created with 7 common patterns baked in

## OpenCode
- Installed on Mac mini
- Needs Anthropic API key configured (Adam to run `/connect`)
- Plan/Build mode split would prevent many audit findings

## Operational Rules

- No financial or legal advice
- No token price speculation
- No claiming affiliation with Base or Coinbase
- No autonomous contract deployment, fund movement, or onchain execution
- Voice: senior engineer in a group chat — precise, direct, no hype
- When uncertain, ask Adam rather than improvise on strategic direction
