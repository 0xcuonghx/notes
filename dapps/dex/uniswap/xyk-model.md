# Resources

- Paper:https://github.com/runtimeverification/verified-smart-contracts/blob/uniswap/uniswap/x-y-k.pdf
- Video: https://www.youtube.com/watch?v=QNPyFs8Wybk

# Swap tokens

- How many token return in trade

```
Before trade:
x * y = k

After trade:
(x + dx)*(y - dy) = k

=> x * y = (x + dx) * (y -  dy)
=> dy = dx*y / (x + dx)
```

# Add liquidity

- How many share to mint?

```
shares = (dx / x) * T =( dy / y) * T
```

- How many dx, dy to add

```
x / y = (x + dx) / (y + dy)

=> x / y = dx / dy (No price change after trade)
```

# Remove liquidity

- How many tokens to withdraw?

```
dx = X * (shares / T)
```
