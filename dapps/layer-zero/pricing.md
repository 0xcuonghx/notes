# Total Fee

1. an initial source blockchain transaction
2. the fee paid to the OApp's configured Security Stack
3. the configured Executor fee for executing the message on the destination chain
4. the message execution cost of the transaction on the destination blockchain itself

```solidity
// DVN fee
uint256 nativeFee = _quoteVerifier(_sender, _dstEid, validationOptions);
// -> getFee, PayFee
// -> totalFee += ILayerZeroDVN(dvn).getFee(_dstEid, _config.confirmations, _sender, options);
// -> ILayerZeroPriceFeed

// Executor Fee + Execution Cost
nativeFee += ILayerZeroExecutor(config.executor).getFee(_dstEid, _sender, _msgSize, executorOptions);
// -> getFee, PayFee
// -> uint256 remoteFee = (gasForCallData + _gas) * remotePrice.gasPriceInUnit;
// -> ILayerZeroPriceFeed

// Protocol fee
(uint256 treasuryNativeFee, uint256 lzTokenFee) = _quoteTreasury(_sender, _dstEid, nativeFee, _payInLzToken);
// -> getFee, PayFee
// -> Treasury: https://etherscan.io/address/0x3773E1E9Deb273fCdf9f80bc88bB387B1e6Ce34d#readContract
// Now is zero

nativeFee += treasuryNativeFee;
```

PriceFeed.sol
https://etherscan.io/address/0x339d413ccefd986b1b3647a9cfa9cbbe70a30749

## Currency

- Native currency
- LZ token
  - set `_payInLzToken: true`

```solidity
supplied = IERC20(lzToken).balanceOf(address(this));
```

- V1 endpoint: https://etherscan.io/address/0x66a71dcef29a0ffbdbe3c6a460a3b5bc225cd675 (not support)
- V2 endpoint: https://etherscan.io/address/0x1a44076050125825900e736c501f859c50fe728c (not support yet)

## Quote Machine

```js
GAS × DESTINATION_GAS_PRICE × (SOURCE_NATIVE_TOKEN_PRICE / DESTINATION_NATIVE_TOKEN_PRICE)
```

## Pricing Updater

- PriceFeed.sol contract
- https://etherscan.io/address/0x339d413ccefd986b1b3647a9cfa9cbbe70a30749

- Using multiple oracles: https://docs.layerzero.network/v1/developers/oracle/google-cloud-oracle ~ DVN

<!-- - AxelarDVNAdapter
- CCIPDVNAdapter -->
