- `abi.encodePacked`

```solidity
hash1 = keccak256(abi.encodePacked([addr1], [addr2, addr3]));
hash2 = keccak256(abi.encodePacked([addr1, addr2], [addr3]));
require(hash1 == hash2);
```
