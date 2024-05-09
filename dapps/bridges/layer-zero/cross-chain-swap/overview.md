# Approach

- integration with Uniswap
- liquidity provider

## Sushi swap

- https://docs.sushi.com/docs/Products/SushiXSwap%20-%20Crosschain%20AMM/Overview
- https://www.sushi.com/swap/cross-chain

- leverages LayerZero’s Stargate protocol
  - https://stargate.finance/
- Contracts [https://github.com/sushiswap/sushixswap-v2, https://github.com/sushiswap/sushixswap]
  - SushiXSwap
  - Adapter

### sushixswap

- Adapter
  - BentoAdapter
  - StargateAdapter
  - SushiLegacyAdapter
  - TokenAdapter
  - TridentSwapAdapter

### SushiXSwapV2

- Adapter

  - StargateAdapter
  - AxelarAdapter

? How SushiXSwapV2 calculator amountOut? (DG <-> 1inch)

- E.g: https://www.sushi.com/swap/cross-chain?chainId0=1&chainId1=137&token0=0xEE06A81a695750E71a662B51066F2c74CF4478a0&token1=0x9c2C5fd7b07E95EE044DDeba0E97a665F142394f&swapAmount=1.5
