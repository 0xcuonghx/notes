### Proxies

- Proxy forwarding
- Unstructured Storage Proxies

### **Initializers**

```js
_init();
_init_unchained();
```

- Initializing the Implementation Contract

```js
/// @custom:oz-upgrades-unsafe-allow constructor
constructor() {
    _disableInitializers();
}
```

### **Modifying Your Contracts**

- Storage Gaps

```js
uint256[50] __gap; // MAX 50
```

- Namespaced Storage Layout
  - EIP-7201

```js
pragma solidity ^0.8.20;

contract Example {
    /// @custom:storage-location erc7201:example.main
    struct MainStorage {
        uint256 x;
        uint256 y;
    }

    // keccak256(abi.encode(uint256(keccak256("example.main")) - 1)) & ~bytes32(uint256(0xff));
    bytes32 private constant MAIN_STORAGE_LOCATION =
        0x183a6125c38840424c4a85fa12bab2ab606c4b6d0e7cc73c0c06ba5300eab500;

    function _getMainStorage() private pure returns (MainStorage storage $) {
        assembly {
            $.slot := MAIN_STORAGE_LOCATION
        }
    }

    function _getXTimesY() internal view returns (uint256) {
        MainStorage storage $ = _getMainStorage();
        return $.x * $.y;
    }
}
```
