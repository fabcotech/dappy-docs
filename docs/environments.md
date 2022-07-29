---
sidebar_position: 2
---

# Environments

Below are up to date environment variables for **RChain testet** / **RChain mainnet** / **local**. Please report to us anything that would not work on [discord](https://discord.gg/8Cu5UFV).

For each of the environments :
- A working URL for a validator node of the testnet
- A working URL for a read-only node of the testnet (they may be the same)
- The shard ID of the RChain network
- The master registry URI (address of rchain-token master contract)
- The dappy name system contract ID (the NFT contract that handles the domain names)

### Environments for RChain testnet + dappy name system

```json
"readOnly": "https://node2.testnet.rchain.coop"
"validator": "https://observer.testnet.rchain.coop"
"shardId": "testnet6"
"masterRegistryUri": "ahgaqqqptoidsjggj1ymey5c3ucwokibb1uot89w444"
"nameSystemContractId": "ahgdappynamesystem"
```

### Environments for RChain mainnet + dappy name system

```json
"readOnly": "https://..."
"validator": "https://..."
"shardId": "..."
"masterRegistryUri": "..."
"nameSystemContractId": "..."
```

### Environments for local dev

We cannot know for sure, but if you have followed the default tutorials and configurations [rchain.coop/developer](https://rchain.coop/developer.html), you should be fine with the following.

Follow instructions at [rchain-token](https://github.com/fabcotech/rchain-token/DAPPY.MD) to set up a name system and retreive `masterRegistryUri` and `nameSystemContractId` variables.

```json
"readOnly": "http://127.0.0.1:40403"
"validator": "http://127.0.0.1:40403"
"shardId": "dev"
"masterRegistryUri": "..."
"nameSystemContractId": "..."
```
