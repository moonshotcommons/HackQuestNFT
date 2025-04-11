# Pharos Workshop Project

## Project Overview
This is an ERC721-compliant NFT contract project that enables users to mint NFTs for free by deploying smart contracts.

### Key Features
- Built on ERC721 standard
- Free NFT minting
- Fully compatible with Pharos chain
- One NFT per user limit

### Minting Requirements
Users must successfully deploy a contract on the Pharos chain and use that contract address to mint their NFT.

## Development Environment Setup

### 1. Installing Foundry
Foundry is a fast, portable toolkit for Ethereum development written in Rust.

```bash
# Download Foundry installer
curl -L https://foundry.paradigm.xyz | bash

# Install forge, cast, anvil, and other tools
foundryup
```

After installation, follow the terminal prompts to configure your environment variables.

Verify the installation:
```bash
forge --version
```

> **Note**: Windows users must install within WSL. For detailed installation instructions, refer to the [Foundry Book](https://book.getfoundry.sh/?open_in_browser=true)

### 2. Pharos Devnet Configuration
| Parameter | Value |
|-----------|-------|
| Chain Name | Pharos Devnet |
| Chain ID | 50002 |
| RPC URL | https://devnet.dplabs-internal.com |
| Block Explorer | https://pharosscan.xyz/ |
| Currency Symbol | ETH |

## Project Setup

### 1. Initialize Project
```bash
forge init MyNFT
cd MyNFT
```

### 2. Install Dependencies
```bash
forge install OpenZeppelin/openzeppelin-contracts --no-git --no-commit
```

### 3. Project File Configuration
1. Rename `src/Counter.sol` to `src/MyNFT.sol` and copy the code from `src/HackQuestNFT.sol` into `MyNFT.sol`
2. Rename `test/Counter.t.sol` to `src/MyNFT.t.sol` and copy the code from `src/HackQuestNFT.t.sol` into `MyNFT.t.sol`
3. Delete or comment out `script/Counter.s.sol`

## Development Workflow

### Compilation and Testing
```bash
# Compile contracts
forge build

# Run tests
forge test
```

### Contract Deployment

#### Environment Variable Setup
```bash
# Deployment account address
export PHA_DEMO=0x6c49....
# Deployment account private key
export PRIVATE_KEY=0x.....
# Pharos RPC
export PHA_RPC=https://devnet.dplabs-internal.com
```

#### Deployment Command
```bash
forge create \
    --rpc-url $PHA_RPC \
    --private-key $PRIVATE_KEY \
    --broadcast \
    src/MyNFT.sol:MyNFT \
    --constructor-args "MyNFT" "MT"
```

## Claiming Your NFT
1. Visit [Pharos Workshop](https://nft-front-lilac.vercel.app/)
2. Connect your wallet (ensure Pharos Devnet is configured and you have test tokens)
3. Use your deployed contract address to claim the NFT

Alternatively, use cast CLI to claim:
```bash
export YOUR_PRIVATE_KEY=0x82.....
export PHA_RPC=https://devnet.dplabs-internal.com
export HQNFT=0xCD7b9304C6ce5531d92B3Ea481f62851C533825D

cast send $HQNFT "mint(address)" $YOUR_NFT_ADDRESS --rpc-url $PHA_RPC --private-key $YOUR_PRIVATE_KEY
```
