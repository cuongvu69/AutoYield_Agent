# mvpcontest
# AutoYield Agent
DeFi Auto-Pilot Agent Wallet for Stablecoin Optimization

AutoYield Agent is an AI-powered Agent Wallet that automatically rotates USDC between lending protocols to optimize yield within user-defined risk rules.

The goal is simple:
Let users earn better stablecoin yield without manually tracking APR or signing transactions every time.

---

## Overview

In DeFi, lending APR changes frequently across protocols such as Aave and Compound.

Most users:
- Leave stablecoins idle
- Forget to rotate funds
- Miss higher APR opportunities
- Avoid automation because they fear losing control

AutoYield Agent solves this by:

1. Creating a dedicated Agent Wallet
2. Allowing users to define strict rules
3. Monitoring APR differences
4. Executing rotations only when it makes economic sense

The system is rule-based, transparent, and includes risk controls.

---

## Core Features (MVP)

- Agent Wallet (separate EOA)
- USDC only
- Aave vs Compound lending
- Rule-based rotation
- APR comparison engine
- Gas-aware decision logic
- Move history logging
- Pause and emergency withdraw
- Manual or auto execution mode

---

## How It Works

### Step 1: Connect Wallet
User connects their wallet.

### Step 2: Fund Agent Wallet
User deposits USDC into the Agent Wallet address.

### Step 3: Configure Rules
User sets:

- Risk profile
- Minimum APR delta
- Maximum moves per day
- Cooldown duration
- Gas limit per move
- Manual or auto execution mode

### Step 4: Autopilot Runs
The system:
- Fetches APR from Aave and Compound
- Estimates gas cost
- Calculates net yield difference
- Decides whether rotation is economically rational
- Executes withdraw + supply if conditions are met

### Step 5: Dashboard Updates
User sees:
- Current protocol
- Current APR
- Last decision reason
- Move history
- Transaction hashes

---

## Business Model

### Freemium
Free:
- Manual run
- 1 move per day limit

Pro Subscription:
- Automatic monitoring
- Unlimited moves (within rule caps)
- Advanced analytics
- Custom gas buffer logic

Future:
- Performance fee on yield uplift

---

## Safety Controls

- Minimum APR delta threshold
- Gas cost sanity check
- Maximum moves per day
- Cooldown timer
- Max total capital limit
- Pause button
- Emergency withdraw

---

## Tech Stack

Frontend:
- Next.js

Blockchain:
- ethers.js

Protocols:
- Aave (USDC lending)
- Compound (USDC lending)

Storage:
- JSON store (rules, state, moves)

Network:
- Testnet only

---

## Running Locally

1. Install dependencies
2. Create `.env.local` with:

RPC_URL=
AGENT_PRIVATE_KEY=
USDC_ADDRESS=
AAVE_POOL_ADDRESS=
COMPOUND_COMET_ADDRESS=

3. Run:
npm run dev

4. Connect wallet
5. Fund agent wallet
6. Configure rules
7. Click Run Check

---

## Demo Flow (Presentation Day)

1. Connect wallet
2. Show agent wallet balance
3. Configure rules (min APR delta 1%)
4. Run check
5. Show decision reasoning
6. Execute rotation
7. Show transaction hash
8. Show updated dashboard

---

## Why This Matters

DeFi is composable.
But users are not.

AutoYield Agent introduces a rule-based AI layer that makes DeFi more accessible while preserving control and transparency.

AI becomes a yield optimizer, not a black-box trading bot.

---

## Roadmap

- Multi-chain support
- Multi-asset support
- Volatility-aware risk model
- Treasury version for DAO
- Performance analytics dashboard
