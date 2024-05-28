# Blockchain of Blockchains

- TON blockchain
- TON DNS
- TON Storage
- TON Sites

- cross-chain interoperability

- accountChain -> accountChains -> shardChain
- shardChain
- accountBlock -> accountBlocks
- shardBlock -> shardBlocks -> shardChain

- Dynamic splitting and merging shardChains (1, infinity) account chains

- Workchain: 2^32
  - MasterChain
  - BaseChain

# Smart Contract Addresses

- Actor model
- (workchain_id, account_id)
  - workchain_id
    - masterchain: workchain_id=-1
    - basechain: workchain_id=0
  - account_id = hash(initial code, initial state)
    - Raw address `-1:fcb91a3a3816d0f7b8c2c76108b8a9bc5a6b7a55bd79f8ab101c52db29232260`
    - User-friendly addresses
      - base64: `kf/8uRo6OBbQ97jCx2EIuKm8Wmt6Vb15+KsQHFLbKSMiYIny`
      - base64URL: `kf_8uRo6OBbQ97jCx2EIuKm8Wmt6Vb15-KsQHFLbKSMiYIny`

## User-Friendly Address

- flags: isBounceable, isTestnetOnly, isUrlSafe
- workchain_id
- account_id
- address verification: CRC16-CCITT signature

# Cells

- storage
- DAG

# Networking

- Abstract Datagram Network Layer (ADNL)
- nodes (even full-nodes) subscribe few shard chains
  - Overlay network
    - Overlay subnetworks
      - gossip protocol
- RLDP
- DHT (The Kademlia-like Distributed Hash Table)
