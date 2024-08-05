```solidity
(bool success, ) = someAddress.call.value(55)("");
if(!success) {
    // handle failure code
}
```
