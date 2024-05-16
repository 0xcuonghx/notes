# Protocols

- Each version of Uniswap, once deployed, will function in perpetuity, with 100% uptime, provided the continued existence of the Ethereum blockchain.

## V1

- Paper: https://hackmd.io/@HaydenAdams/HJ9jLsfTz?type=view
- Github: https://github.com/Uniswap/v1-contracts

### Features

- Trade ERC20 <-> ETH
- Trade ERC20 <-> ERC20: ERC20 <-> ETH, ETH <-> ERC20

### Pool ERC20 vs ETH

```
def createExchange(token: address) -> address:
```

uniswap_factory ---create-> uniswap_exchange

### Liquidity

- Model `x * y = k`

## V2

- Paper: https://docs.uniswap.org/whitepaper.pdf
- Github: https://github.com/Uniswap/v2-core

### Features

- ERC20/ERC20 pairs
- Oracle support
  - Prevent price manipulate
  - Estimate the time-weighted average price for the two assets over arbitrary intervals
- Flash swaps

## V3

- Paper:https://uniswap.org/whitepaper-v3.pdf
- Github: https://github.com/Uniswap/v3-core

## V4

- Paper: https://github.com/Uniswap/v4-core/blob/main/docs/whitepaper-v4.pdf
- Github: https://github.com/Uniswap/v4-core

### Features

- Concentrated Liquidity
- Flexible fees
- Improve Price Oracle
- Liquidity Oracle
