- The nonReentrant modifier should occur before all other modifiers

# Prevent reentrancy attack

- Use the Checks-Effects-Interactions Pattern
- Using ReentrancyGuard
- Using `.tranfer()`, `.send()` limit 2300 gas forward

## Don't use transfer() or send()

- This forwards 2300 gas, which may not be enough if the recipient is a contract and gas costs change
- Using `.call()` with Checks-Effects-Interactions Pattern / ReentrancyGuard
