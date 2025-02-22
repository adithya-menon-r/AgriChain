# AgriChain Development Installation Guide

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [MetaMask Setup](#metamask-setup)
3. [Environment Setup](#environment-setup)
4. [Project Installation](#project-installation)
5. [Development Server](#development-server)
6. [Smart Contract Deployment](#smart-contract-deployment)
7. [Troubleshooting](#troubleshooting)

## Prerequisites

Before beginning the installation, ensure you have the following tools installed:

| Tool | Version | Purpose |
|------|---------|----------|
| Node.js | Latest LTS | JavaScript runtime |
| npm | Bundled with Node.js | Package manager |
| MetaMask | Latest | Blockchain interaction |
| PostgreSQL/NeonDB | Latest | Database management |

## MetaMask Setup

### 1. Install MetaMask
1. Visit the [MetaMask website](https://metamask.io/download/)
2. Install the extension for your browser (Chrome, Firefox, Brave, or Edge)
3. Click on the extension icon and follow the setup wizard

### 2. Create or Import Wallet
```plaintext
# For new wallet:
1. Click "Create a new wallet"
2. Set up a secure password
3. Store your 12-word seed phrase securely
4. Confirm your seed phrase

# For existing wallet:
1. Click "Import wallet"
2. Enter your 12-word seed phrase
3. Set up a new password
```

### 3. Configure Sepolia Network
```plaintext
1. Click network dropdown (usually shows "Ethereum Mainnet")
2. Click "Add network"
3. Add Sepolia network details:
   - Network Name: Sepolia Test Network
   - RPC URL: https://sepolia.infura.io/v3/
   - Chain ID: 11155111
   - Currency Symbol: SepoliaETH
   - Block Explorer: https://sepolia.etherscan.io
```

### 4. Get Test ETH
```plaintext
1. Copy your wallet address
2. Visit Sepolia faucet: https://sepoliafaucet.com
3. Request test ETH for development
```

### 5. Connect Wallet to AgriChain
```plaintext
1. Visit your local AgriChain application (http://localhost:3000)
2. Click "Connect Wallet" button
3. Select your MetaMask account
4. Approve the connection
```

## Environment Setup

### 1. Repository Setup
```bash
# Clone the repository
git clone https://github.com/YOUR_REPOSITORY_URL.git

# Navigate to project directory
cd YOUR_PROJECT_DIRECTORY
```

### 2. Environment Configuration

Create the following environment files in their respective directories:

#### Frontend Configuration (`frontend/.env`)
```plaintext
# API Configuration
API_PORT="YOUR_API_PORT"                # Backend API port number
CONTRACT_ADDRESS="YOUR_CONTRACT_ADD"    # Deployed Sepolia contract address
```

#### Backend Configuration (`backend/.env`)
```plaintext
# Server Configuration
PORT=5000                              # Backend server port
GEMINI_API_KEY="YOUR_GEMINI_API_KEY"   # AI insights API key
DB_URL="YOUR_DB_URL"                   # Database connection URL
DB_PORT="YOUR_DB_PORT"                 # Database port number
```

#### Smart Contract Configuration (`smart-contracts/.env`)
```plaintext
# Blockchain Configuration
SEPOLIA_RPC_URL="https://eth-sepolia.g.alchemy.com/v2/YOUR_ALCHEMY_API_KEY"
PRIVATE_KEY="YOUR_WALLET_PRIVATE_KEY"  # ⚠️ Keep this secure
ETHERSCAN_API_KEY="YOUR_ETHERSCAN_API_KEY"
```

> [!TIP]
> Create a copy of the `.env.example` and rename it to `.env`

## Project Installation

Install all project dependencies with a single command:

```bash
# Install dependencies for all components
npm run install-all
```

This command installs dependencies for:
- Frontend application
- Backend server
- Smart contract development

## Development Server

Launch the development environment:

```bash
# Start all services
npm run dev
```

This command initiates: (by default)
- Frontend server at `http://localhost:3000`
- Backend server at `http://localhost:5000`

## Smart Contract Deployment

For deploying smart contracts to the Sepolia testnet:

```bash
# Navigate to smart contracts directory
cd smart-contracts

# Deploy contracts
npx hardhat run scripts/deploy.js --network sepolia

# Verify on Etherscan (replace with your contract address)
npx hardhat verify --network sepolia YOUR_DEPLOYED_CONTRACT_ADDRESS
```

## Troubleshooting

Common issues and solutions:

1. **Port Conflicts**
   - Ensure ports 3000 and 5000 are available

2. **Database Connection**
   - Verify database credentials in `.env`
   - Ensure database service is running

3. **Smart Contract Deployment**
   - Confirm sufficient test ETH in wallet
   - Verify RPC URL and private key
   - Check network connectivity

4. **Environment Variables**
   - Double-check all `.env` files are properly configured

## Security Notes

- Never commit `.env` files to version control
- Keep private keys secure and never share them
- Use test networks (Sepolia) for development
- Regularly update dependencies for security patches
