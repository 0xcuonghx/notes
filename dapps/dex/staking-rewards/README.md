# Overview

1. `owner` set duration and rewards
2. `user` stake in duration
3. `user` withdraw staked token and total rewards

# Math

- Reward per second

```
r = R / n
```

## How many reward for user?

- `R`: reward token per second

```
Total i from k to n - 1: Si / Ti * R
```

```js
// Calculate reward per token
r += R / (totalSupply * (current time - last update time))

// Calculate reward earned by user
rewards[user] += balanceOf[user] * (r - userRewardPerTokenPaid[user])

// Update user reward per token paid
userRewardPerTokenPaid[user] = r;
// Update last update time
last update time  = current time
// Update staked amount
balanceOf[user] += amount // on staking
or balanceOf[user] -= amount // on withdraw
```

### Source

- https://github.com/ibdotxyz/StakingRewards
- https://solidity-by-example.org/defi/staking-rewards/
