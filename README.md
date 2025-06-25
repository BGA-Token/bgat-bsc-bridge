# bgat-bsc-bridge

> Cross-chain bridge for BGA Token (BGAT) from WAVES Blockchain to Binance Smart Chain (BSC)

This repository contains the smart contract and backend server logic used to mint and burn a wrapped version of the BGA Token (`BGAT`) on BSC. It includes a secure owner-controlled bridge contract, a Node.js backend, and webhook/alert integrations.

---

## 🌉 Bridge Flow Overview

1. Users send BGAT on WAVES to a bridge address.
2. A backend server watches the WAVES blockchain and mints BGAT on BSC via the `BGATBridgeToken` contract.
3. For withdrawals, the server burns BGAT and releases BGAT on WAVES.
4. Webhook alerts and logs are recorded for each transaction.

---

## 🔧 Technologies

- Solidity (`BGATBridgeToken.sol`, `Owner.sol`)
- Node.js / Express backend
- Ethers.js (BSC interaction)
- @waves/waves-transactions
- Discord Webhook integration
- Logging via `bridge.log`

---

## 📁 Structure
contracts/
├── BGATBridgeToken.sol
└── Owner.sol

scripts/
└── deploy.js (optional Hardhat)

bridge-server.js # Node.js backend
.env.example # Environment config template


---

## 🚀 Deployment

1. Deploy `BGATBridgeToken.sol` using Remix or Hardhat to BSC Testnet or Mainnet.
2. Copy the contract address to your `.env`.
3. Run the backend server:

```bash
npm install
node bridge-server.js



