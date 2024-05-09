# Layerzero transactions fee

1. an initial source blockchain transaction
2. the fee paid to the OApp's configured Security Stack
3. the configured Executor fee for executing the message on the destination chain
4. the message execution cost of the transaction on the destination blockchain itself

```solidity
    function _quote(
        address _sender,
        uint32 _dstEid,
        uint256 _msgSize,
        bool _payInLzToken,
        bytes calldata _options
    ) internal view returns (uint256, uint256) {
        (bytes memory executorOptions, WorkerOptions[] memory validationOptions) = _splitOptions(_options);

        // quote the verifier used in the library. for ULN, it is a list of DVNs
        uint256 nativeFee = _quoteVerifier(_sender, _dstEid, validationOptions);

        // quote executor
        ExecutorConfig memory config = getExecutorConfig(_sender, _dstEid);
        // assert msg size
        _assertMessageSize(_msgSize, config.maxMessageSize);

        nativeFee += ILayerZeroExecutor(config.executor).getFee(_dstEid, _sender, _msgSize, executorOptions);

        // quote treasury
        (uint256 treasuryNativeFee, uint256 lzTokenFee) = _quoteTreasury(_sender, _dstEid, nativeFee, _payInLzToken);
        nativeFee += treasuryNativeFee;

        return (nativeFee, lzTokenFee);
    }
```

1. `uint256 nativeFee = _quoteVerifier(_sender, _dstEid, validationOptions);`

- the fee paid to the OApp's configured Security Stack
- `totalFee += ILayerZeroDVN(dvn).getFee(_dstEid, _config.confirmations, _sender, options);`
- fee depend on each DVN we config. [dvn-addresses](https://docs.layerzero.network/v2/developers/evm/technical-reference/dvn-addresses)

2. `nativeFee += ILayerZeroExecutor(config.executor).getFee(_dstEid, _sender, _msgSize, executorOptions);`

- the configured Executor fee for executing the message on the destination chain
- the fee depend on executor we config. [executor-addresses](https://docs.layerzero.network/v2/developers/evm/technical-reference/executor-addresses)

3. `(uint256 treasuryNativeFee, uint256 lzTokenFee) = _quoteTreasury(_sender, _dstEid, nativeFee, _payInLzToken);`

- the protocol fee
- Now is zero, but it's can be config by layerzero team throw [treasury address](https://etherscan.io/address/0x5ebB3f2feaA15271101a927869B3A56837e73056)

PriceFeed.sol
https://etherscan.io/address/0x339d413ccefd986b1b3647a9cfa9cbbe70a30749

## Currency

- Layer zero fee can be pay by source native fee or layerzero token (LZ)
- Now layer zero not support pay by layerzero token (LZ) yet
  - V1 endpoint: https://etherscan.io/address/0x66a71dcef29a0ffbdbe3c6a460a3b5bc225cd675 (not support)
  - V2 endpoint: https://etherscan.io/address/0x1a44076050125825900e736c501f859c50fe728c (not support yet)

## Quote Machine

If a user wants to send a message from Chain A to Chain B, the gas quote returned on Chain A is:

`the execution cost on Chain A + fees for the Security Stack and Executor + a quote for the gas to be executed on Chain B`

For example, if a user wants 200000 gas units on Chain B, then a quote for that gas token is obtained by multiplying the gas by the gas price on the destination chain. It also takes into account dollar prices of the source and destination native tokens.

The source chain's native token quote is calculated using following formula:

`GAS × DESTINATION_GAS_PRICE ×
DESTINATION_NATIVE_TOKEN_PRICE /
SOURCE_NATIVE_TOKEN_PRICE`

For example, assume Chain A is Astar and Chain B is Astar zkEVM:

`200000 * (4000000000 / 10**18) * $3500 / $0.15 = 18.7 ASTR quote`

### How Layerzero parties calculator the price? For previous example ?

- Executor & DVN using PriceFeed contract to update & get pricing
- https://etherscan.io/address/0x339d413ccefd986b1b3647a9cfa9cbbe70a30749
