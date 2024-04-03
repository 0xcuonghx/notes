# \_options

- Because the source chain has no concept of the destination chain's state. You must specify the amount of gas you anticipate will be necessary for executing your lzReceive or lzCompose
  - lzReceiveOption
  - lzComposeOption
  - lzNativeDropOption

## Option builders

```solidity
import { OptionsBuilder } from "@layerzerolabs/lz-evm-oapp-v2/contracts/oapp/libs/OptionsBuilder.sol";
```

```js
import { Options } from "@layerzerolabs/lz-v2-utilities";
```

## Option Types

1. lzReceiveOption

```solidity
// (uint128 _gas, uint128 _value)
// 200000 should be enough for most transactions
Options.newOptions().addExecutorLzReceiveOption(200000, 0);
```

2. lzComposeOption

```solidity
// (uint16 _index, uint128 _gas, uint128 _value)
// Although 1000000 is commonly used as a default, it's important to perform tailored testing to determine the optimal gas requirement for your specific transaction needs
Options.newOptions().addExecutorLzComposeOption(0, 1000000, 0);
```

3. lzNativeDropOption

```solidity
// (uint128 _amount, bytes32 _receiver)
Options.newOptions().addExecutorNativeDropOption(1000000000000, receiverAddressInBytes32);
```

4. OrderedExecutionOption

```solidity
// bytes: The argument should always be initialized as an empty bytes array ("").
Options.newOptions().addExecutorOrderedExecutionOption(bytes(''));
```

5. DuplicateOption

```solidity
bytes memory options = OptionsBuilder.newOptions().addExecutorLzReceiveOption(200000, 0).addExecutorLzComposeOption(0, 1000000, 0).addExecutorLzComposeOption(1, 500000, 0);
```

# Costs

1. an initial source blockchain transaction
2. the fee paid to the OApp's configured Security Stack
3. the configured Executor fee for executing the message on the destination chain
4. the message execution cost of the transaction on the destination blockchain itself

```js
GAS × DESTINATION_GAS_PRICE × (SOURCE_NATIVE_TOKEN_PRICE / DESTINATION_NATIVE_TOKEN_PRICE)
```

- V1

```solidity
nativeFee = nativeFee.add(relayerFee).add(oracleFee)
```

- AxelarDVNAdapter
- CCIPDVNAdapter
- https://github.com/LayerZero-Labs/LayerZero-v2/tree/main/messagelib/contracts/uln/dvn/adapters
