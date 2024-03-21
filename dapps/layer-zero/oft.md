# OFT

- ERC20
- `_debit`

  - `_debitView`

  - remove dust: Internal function to remove dust from the given local decimal amount.

  ```
  - SD: 6
  - LD: 18

  amount: 10000...123 after remove dust become 1000...000
  ```

- `_credit`

# OFTCore

## decimals

- shareDecimals == SD == shared Decimals
- localDecimals == LD == local decimals

```solidity
* Lowest common decimal denominator between chains.
* Defaults to 6 decimal places to provide up to 18,446,744,073,709.551615 units (max uint64).
* For tokens exceeding this totalSupply(), they will need to override the sharedDecimals function with something smaller.
function sharedDecimals() public pure virtual returns (uint8) {
    return 6;
}
```

## send

- sendParam

```solidity
struct SendParam {
    uint32 dstEid; // Destination endpoint ID.
    bytes32 to; // Recipient address.
    uint256 amountLD; // Amount to send in local decimals.
    uint256 minAmountLD; // Minimum amount to send in local decimals.
    bytes extraOptions; // Additional options supplied by the caller to be used in the LayerZero message.
    bytes composeMsg; // The composed message for the send() operation.
    bytes oftCmd; // The OFT command to be executed, unused in default OFT implementations.
}
```

- messageFee

  - quoteSend to endpoint

- OAppPreCrimeSimulator
