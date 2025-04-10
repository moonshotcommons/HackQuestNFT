## Foundry

**Foundry is a blazing fast, portable and modular toolkit for Ethereum application development written in Rust.**

Foundry consists of:

-   **Forge**: Ethereum testing framework (like Truffle, Hardhat and DappTools).
-   **Cast**: Swiss army knife for interacting with EVM smart contracts, sending transactions and getting chain data.
-   **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network.
-   **Chisel**: Fast, utilitarian, and verbose solidity REPL.

## Documentation

https://book.getfoundry.sh/

## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```

### 设置环境变量
```
# 账户地址
export PHA_DEMO=0x6c49d46cf7267A3De0A698cab95792BF69c91aFC
# 部署账户私钥
export PRIVATE_KEY=0x.....
# Arbitrum Sepolia RPC
export ARB_RPC=https://sepolia-rollup.arbitrum.io/rpc
export ETHERSCAN_API_KEY=...
```

### 部署合约
```
# 部署 HackQuestNFT 合约
forge create \
    --rpc-url $ARB_RPC \
    --private-key $PRIVATE_KEY \
    --broadcast \
    src/HackQuestNFT.sol:HackQuestNFT \
    --constructor-args "HackQuest" "HQ"

forge create --rpc-url $ARB_RPC --private-key $PRIVATE_KEY --broadcast  --verify --etherscan-api-key $ETHERSCAN_API_KEY src/AutoTimelock.sol:AutoTimelock --constructor-args 0xF54C5b9c05C2dE971f427056Ae4a6e0f1b745D66
```

### Format

```shell
$ forge fmt
```

### Gas Snapshots

```shell
$ forge snapshot
```

### Anvil

```shell
$ anvil
```

### Deploy

```shell
$ forge script script/Counter.s.sol:CounterScript --rpc-url <your_rpc_url> --private-key <your_private_key>
```

### Cast

```shell
$ cast <subcommand>
```

### Help

```shell
$ forge --help
$ anvil --help
$ cast --help
```
