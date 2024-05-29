# Overview
- Types of blockchain
  - 1st gen: Bitcoin
  - 2nd gen: Ethereum (+ EVM)
  - 3rd gen: TON (+ Scale)
- Costodial & Non-custodial
- Ecosystem
  - TON blockchain
  - TON DNS
  - TON Storage
  - TON Sites
- cross-chain interoperability

# TON blockchain (Blockchain of Blockchains)
- account(state)
  - isolated each other -> no access state of others
  - comunicate by asynchronous message
  
- message -> change account state -> accountChain

- prallel execute & validate
  - double spending
    - consensus: POS
  - routing meessages 


- accountChain -> accountChains -> shardChain
- shardChain
- accountBlock -> accountBlocks
- shardBlock -> shardBlocks -> shardChain

- Dynamic splitting and merging shardChains (1, infinity) account chains

- Workchain: 2^32
  - MasterChain
    - non-shardable, expensive, not scalable
    - snapshot another chains
  - BaseChain
    - shardable
    - split & merge
- Scale
  - scale groups of validator (multiple groups)
  - sharding

# Smart Contract
- State
  - data
  - code
  - balance

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

## Tokens
- Non fungible token
  - TON DNS
- Fungible token
  - No signle contract controlling all tokens
  - token wallets
  - scalibility ?

## Scalable
- TON guarantees that it can scale down to granularity of individual contracts.
- Best pratice
  - avoid having length data
  - data list short & bounded (no dynamic grouwth)
  - big dynamic data owned by signle owner (not anyone change size of data accept owner)
  - large list or dictionaries of data is to use blockchain itself
- Target building successful application
  - scale indenfinitely
  - constant storage cost
  - constant operation cost
- Examples
  - Tokens: Minter contract -> subcontracts for each user (jetton wallet)
    - -(external call)-> Wallet A -(internal call)-> Jetton wallet A -(internal call)-> Jetton wallet B
  - Multi-signature
    - tokenlizing request
      - flood request will be expensive
    - voting
  - version 4, the wallets support the plugins that enable people to create subscription payment
    - owner manage
    - better way: distinct plugin code?
# Fees
- Gas cost
  - cost = gas quantity * gas price
    - gas price: global parameter config, changed by consensus of validators (unlike ETH, BTC because TON infinity scale)
  - Rent
    - price * bit * sec
      - Frozen contracts
        - Hashing -> after 1/2 year inactivity -> compelete offloads
  - Messages fee
    - Number of fees for importing & creating out-going message

- Make sure contract exist
  - anyone can sen TON to contract
  - upper bound of cost  

# Cells
- smallest unit stograge
- upto 1023 bits
- upto 4 reference other cells
- bag of cells
  - merkle proof 

- cell -> bag of cells -> merkle tree
- memory layout
   - hash map (a prefix tree)

- unpacking cells
  - jump reference
  - expensive operation
  - don't store a lot data at one place

- DAG

# TVM
- stack-based vitrual machine
- limit the amount of work that is done in any single place
  -  scalable across contracts but each individual contract is not scalable out of the box by itself
- Types
  - Cells
  - Intergers

# Messages
- External
- Internal

- message is input of transaction

- phase of transaction
  - storage phase
  - credit phase
  - compute phase
  - action phase
  - bounce phase
    - roll back when contract has failed
- authorization
  - signature
    - external message
  - message sender
  - DNA check
    - hash of contract code & data
  - lack of authentication for censorship resistance
    - decentralized staking pool
# Networking

- Abstract Datagram Network Layer (ADNL)
- nodes (even full-nodes) subscribe few shard chains
  - Overlay network
    - Overlay subnetworks
      - gossip protocol
- RLDP
- DHT (The Kademlia-like Distributed Hash Table)

# TO-DOs

- [ ] https://docs.ton.org/learn/docs#original-documentation
