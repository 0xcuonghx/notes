# Unchecked

- To save gas, as the code inside unchecked{"Some Code"} isn't verified for underflow/overflow error cases.

```sol

unchecked {
  i++;
}
```
