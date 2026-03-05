SatsStream ⚡
Bitcoin-native streaming subscriptions on Bitcoin L1 via OPNet.
The world's first decentralized subscription layer on Bitcoin. Subscribe to creators, newsletters, VPNs and AI tools — pay micro-sats per Bitcoin block. Cancel anytime. Zero middlemen. Pure BTC.
🌍 Live Demo
Frontend: https://satsstream.netlify.app
Contract Address: opt1sqqvw5dlrv9hhc49gw84lu5thtt9kqpujkyvwh4f5
Deploy TX: f301c832f41c073829f7aff22270e4b59dd335e6340737869d2ea7bde6dc3faa
Explorer: View on OP_SCAN
🚨 The Problem
Patreon takes 8–12% of every payment
Stripe doesn't speak Bitcoin
Lightning doesn't support subscriptions
Every "Bitcoin payment" app still routes through banks or custodians
SatsStream is the first primitive that changes this — fully on-chain, fully trustless.
✅ The Solution
SatsStream is an OPNet smart contract written in AssemblyScript, compiled to WASM, and deployed to a Bitcoin P2OP address. No sidechain. No rollup. No wrapped assets. Settlement is Bitcoin-final.
How it works:
Step
Action
01
Connect OP_WALLET
02
Subscribe to a creator at their sats/block rate
03
Micro-sats accrue every Bitcoin block (~10 mins)
04
Cancel anytime with 1 transaction
🔧 Contract Architecture
// SatsStream.ts — Core settlement logic

function registerCreator(name, ratePerBlock) {
  // stores rate on-chain, emits CreatorRegistered event
}

function subscribe(creatorAddress) {
  // snapshots rate + blockHeight, marks sub active
}

function settleStream(subscriber, creator) {
  const elapsed = currentBlock - startBlock;
  const gross   = elapsed × ratePerBlock;
  const fee     = gross × 1%;  // → OPNet treasury
  const net     = gross - fee; // → creator wallet

  transferBTC(creator, net);
  transferBTC(treasury, fee);
}

function unsubscribe(creatorAddress) {
  // final settle → marks sub inactive
}

function pendingAmount(subscriber, creator) {
  // view function
}

// Zero trust. Zero banks. Just math.
🛠 Tech Stack
Smart Contract: AssemblyScript → WASM → Bitcoin P2OP
Protocol: OPNet (Bitcoin L1 smart contracts)
Wallet: OP_WALLET
Frontend: HTML/CSS/JS — deployed on Netlify
Network: OPNet Testnet
🚀 Running Locally
Clone this repo
Open index.html in your browser for the landing page
Open satsstream-dapp.html for the dApp
Install OP_WALLET to connect
💡 Why SatsStream Wins
For Creators — Native BTC revenue. No permission, no KYC, no bank account needed. Anywhere on Earth.
For Users — True ownership. Sats stay in your wallet until settle. Cancel in one tx.
For OPNet — Highest-volume dApp potential. One subscriber = dozens of micro-transactions per day.
For Bitcoin — A new reason to use sats daily. The utility layer Bitcoin has been missing.
📄 License
MIT — open source, fork it, build on it.
Built for Vibecode Hackathon Week 2 · Built entirely on a mobile phone 📱
#opnetvibecode @opnetbtc
