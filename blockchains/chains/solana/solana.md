# Features

- 400ms confirmed block
- low fees
- high throughput

# Development

- Composable: build on top of deployed programs

## Types

- Onchain
  - Rust
  - Anchor: Framework
- Client-side
  - SDK

# Concepts

- Account model
- Transaction
- Transaction fee
- Programs
- Program Derived Address (seeds, sign)
- Cross Program Invocation
- Token
- RPC Endpoints

## Account model

- ED25519

```
{
 data
 executable
 amports
 owner
}
```

- Native program
- BPF loader
- Sysvar program
- custom program
  - program account
  - data account

![account-model](./figures/account-model.png)

## Transaction

- instructions
  - order
  - atomic
