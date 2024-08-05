- `private` type variables can be read on smart contract

```js
// slot: https://docs.soliditylang.org/en/latest/internals/layout_in_storage.html
await provider.getStorageAt(address, slot);
```
