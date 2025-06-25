# bgat-bsc-bridge

> Cross-chain bridge for BGA Token (BGAT) from WAVES Blockchain to Binance Smart Chain (BSC)

This repository contains the smart contract and backend server logic used to mint and burn a wrapped version of the BGA Token (`BGAT`) on BSC. It includes a secure owner-controlled bridge contract, a Node.js backend, and webhook/alert integrations.

---

## 🌉 Bridge Flow Overview

1. Users send BGAT on WAVES to a monitored bridge address.
2. A backend server watches the WAVES blockchain and mints BGAT on BSC via the `BGATBridgeToken` contract.
3. For withdrawals, the server burns BGAT on BSC and releases BGAT on WAVES.
4. Discord Webhook alerts and logs are recorded for each transaction.

---

## 🛠 Requirements

- [Node.js](https://nodejs.org/) >= 14
- [Hardhat](https://hardhat.org)
- Metamask wallet (or any wallet with BNB Testnet support)

---

## 🔧 Technologies

- Solidity (`BGATBridgeToken.sol`, `Owner.sol`)
- Node.js / Express backend
- Hardhat (Solidity toolchain)
- Ethers.js (BSC interaction)
- @waves/waves-transactions
- Discord Webhook integration
- Logging via `bridge.log`

---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/BGA-Token/bgat-bsc-bridge.git
cd bgat-bsc-bridge

# Install dependencies:
npm install
```

---

## 🔐 Environment Setup

Create a `.env` file in the project root:

```bash
cp .env.example .env
```

Edit `.env` and fill in your credentials:

```env
PRIVATE_KEY=your_bsc_wallet_private_key
BSCSCAN_API_KEY=your_bscscan_api_key
BSC_CONTRACT_ADDRESS=deployed_contract_address
WAVES_SEED=waves_seed_for_bridge_wallet
WAVES_ADDRESS=waves_wallet_address_to_monitor
DISCORD_WEBHOOK=https://discord.com/api/webhooks/...
```

Use `.env.example` as a reference. **Never commit `.env`.**

---

## 🧪 Compile Contract

```bash
npx hardhat compile
```

---

## 🚀 Deploy to BSC Testnet/Mainnet

```bash
npx hardhat run scripts/deploy.js --network bscTestnet
```

---

## 🔁 Flatten Contracts (Optional)

```bash
npx hardhat flatten contracts/BGATBridgeToken.sol > flat/BGATBridgeToken.flat.sol
```

---

## 🌐 Start the Bridge Backend

```bash
node bridge-server.js
```

This will:
- Monitor WAVES for inbound transfers
- Mint BGAT on BSC
- Burn BGAT and release tokens on WAVES for withdrawals
- Send Discord webhook alerts

---

## 💻 Start the Frontend (Simple Static UI)

Open `frontend/index.html` in a browser. It allows:
- Connecting MetaMask
- Displaying wallet BGAT balance
- Triggering mint/burn via backend

---

## 📁 Project Structure

```
bgat-bsc-bridge/
├── contracts/
│   ├── BGATBridgeToken.sol       # BEP-20 token logic
│   └── Owner.sol                 # Ownership control
├── scripts/
│   └── deploy.js                 # Deployment script using Hardhat
├── flat/
│   └── BGATBridgeToken.flat.sol # Optional flattened version
├── frontend/
│   ├── index.html               # Basic frontend layout
│   ├── bridge.js                # Frontend logic (wallet interaction, API calls)
│   ├── abi/
│   │   └── BGATBridgeToken.json # ABI from compile
│   └── css/
│       └── style.css            # UI styling
├── bridge-server.js             # Node backend that watches WAVES and interacts with BSC
├── .env.example                 # Template for environment variables
├── .gitignore                   # Ignore secrets, artifacts, etc.
├── LICENSE                      # MIT license
├── hardhat.config.js            # Hardhat config with etherscan plugin
└── README.md                    # This file
```

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 📝 Notes

- You can update the token name/symbol/decimals in `BGATBridgeToken.sol`
- Ensure test BNB is available in your wallet for gas
- To deploy to mainnet, configure the `bscMainnet` network in `hardhat.config.js`

---

## 🙋 Support

Open a GitHub issue or reach out to the BGAT developer team.

Built with ❤️ for the BlockGators Army Advertising Network ecosystem.











