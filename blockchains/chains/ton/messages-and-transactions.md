# Messages
- external: outside -> smart_contract
- internal: smart_contract -> smart_contract
- logs: smart_contract -> outside

https://docs.ton.org/v3/documentation/smart-contracts/message-management/ecosystem-messages-layout
# Transactions
- in_msg
- out_msg[]: optional

- synchronous blockchain: Ethereum
- asynchronous
- infinite sharding paradigm
  - full parallelization: execution of each transation is independence
  - transaction in TON is only executed on a single smart contract
  - smart contract can only interact with each other
 
# Logical Time (lt)
- each block, start_lt -> end_lt
- block ordered by its lt
- child block on a shartd has a higher lt than its parents
- masterchain block's lt is higher that the lts of shard blocks that it lists

# Sending messages
- Composition, parsing, and sending messages
  - TL-B schemas
