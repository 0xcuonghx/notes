- ERC20 short address attack.

```solidity
transfer(address _to, uint256 _amount)
```

```shell
// encode send data transaction 0x90b98a1100000000000000000000000062bec9abe373123b9b635b75608f94eb8644163e0000000000000000000000000000000000000000000000000000000000000002

0x90b98a11 // method signature
00000000000000000000000062bec9abe373123b9b635b75608f94eb8644163e // "to" address
0000000000000000000000000000000000000000000000000000000000000002 // "amount"
```

```shell
0x90b98a11
00000000000000000000000062bec9abe373123b9b635b75608f94eb86441600
00000000000000000000000000000000000000000000000000000000000002
                                                              ^^
                                           Note the missing byte
```

- the number of coins transferred became 512 ( 2<<8 = 512)

```solidity
contract NonPayloadAttackableToken {
   modifier onlyPayloadSize(uint size) {
     assert(msg.data.length == size + 4);
     _;
   }

  function transfer(address _to, uint256 _value) onlyPayloadSize(2 * 32) {
    // do stuff
  }
}
```
