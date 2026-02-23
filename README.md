# AutoYield Agent DApp
DeFi Auto-Pilot Agent Wallet for Stablecoin Yield Optimization (DApp MVP)

AutoYield Agent is a web-based DApp that creates a dedicated Agent Wallet and automatically rotates USDC between lending protocols to optimize yield under strict user-defined rules.

This MVP runs on testnet only and is designed for live demo via browser UI (no CLI flow).

---

## Product Summary

Stablecoin lending APR changes frequently across protocols like Aave and Compound.
Most users do not track APR and do not want to sign multiple transactions for every optimization.

AutoYield Agent provides:
- A DApp dashboard
- A dedicated Agent Wallet address
- Rule-based autopilot controls
- APR monitoring and gas-aware rotation
- Transparent decision reasoning and transaction logs

---

## MVP Features

### DApp UI
- Connect wallet
- View Agent Wallet address and USDC balance
- Configure autopilot rules
- Start, pause, and run check manually
- See APR comparison and decision reasoning
- Execute rotation (manual confirm mode)
- View move history with tx hashes

### Strategy (MVP)
- Asset: USDC only
- Protocols: Aave vs Compound
- Strategy: rotate to higher net APR when delta >= threshold and net gain exceeds gas buffer
- Chain: testnet only

### Safety Controls
- min APR delta threshold
- max moves per day
- cooldown minutes
- max gas USD per move
- pause on error
- emergency withdraw

---

## DApp User Flow

### 1) Onboarding
1. User clicks Connect Wallet
2. DApp shows:
   - User wallet address
   - Agent wallet address (generated from server config)

### 2) Funding
1. User transfers testnet USDC to Agent Wallet
2. DApp shows live USDC balance

### 3) Rule Setup
User sets:
- Risk profile preset
- minAprDeltaPct
- maxMovesPerDay
- cooldownMinutes
- maxGasUsdPerMove
- execution mode: manual confirm or auto

Rules are saved in app storage for the current session (MVP uses JSON store).

### 4) Autopilot
User can:
- Run Check Now (manual)
- Start Autopilot (interval checks)

The DApp shows:
- Aave APR, Compound APR
- estimated gas USD
- decision output and reason

### 5) Execution
In manual confirm mode:
- DApp shows rotation suggestion
- User clicks Execute Rotation
- DApp sends on-chain transactions via Agent Wallet signer
- DApp displays tx hashes and updates current protocol state

---

## Pages (UI)

- `/` Landing + Connect Wallet
- `/dashboard` Main dashboard:
  - Agent wallet card
  - USDC balance
  - Rule config panel
  - APR comparison panel
  - Autopilot controls
  - Move history table

---

## Technical Architecture (MVP)

Frontend:
- Next.js DApp UI
- Wallet connection using wagmi or ethers BrowserProvider

Backend:
- Next.js API routes handle:
  - rules persistence
  - autopilot state
  - runOnce decision
  - optional scheduler trigger

On-chain:
- ethers.js signer for Agent Wallet
- Interact with Aave and Compound contracts on testnet

Data store:
- JSON store (rules.json, state.json, moves.json)

---

## Local Setup

### 1) Install
npm install

### 2) Env
Create `.env.local`:

RPC_URL=
NEXT_PUBLIC_CHAIN_ID=
AGENT_PRIVATE_KEY=
USDC_ADDRESS=
AAVE_POOL_ADDRESS=
COMPOUND_COMET_ADDRESS=

### 3) Run
npm run dev

Open:
http://localhost:3000

---

## Demo Script (Presentation)

1. Open DApp
2. Connect wallet
3. Show Agent Wallet address
4. Fund Agent Wallet with testnet USDC
5. Configure rule: min APR delta 1%, max moves/day 1
6. Click Run Check Now
7. Show decision reasoning (ROTATE)
8. Click Execute Rotation
9. Show tx hash and updated dashboard state
10. Pause autopilot and show emergency withdraw button

---

## Business Model

Freemium:
- Manual checks
- 1 move/day

Pro Subscription:
- Auto monitoring
- Unlimited moves within risk rules
- Advanced analytics dashboard

Future:
- Performance fee based on yield uplift vs baseline

---

## Roadmap

- Multi-chain and multi-asset support
- Protocol allowlist expansion
- Volatility-aware risk model
- DAO treasury tier
- Agent activity analytics dashboard
