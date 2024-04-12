- [ ] Build on top of OApp
- [ ] Follow ONFT version 1

# OApp

- Build-in
  - `_lzSend`
  - `_lzReceive`
- Override
  - `send`
    - \_dstEid
    - \_message
    - \_options
      - OAppOptionsType1
      - OAppOptionsType2
      - OAppOptionsType3
    - MessagingFee
    - \_refundAddress
  - `quote`
  - `lzreceive`
    - \_origin
      - srcEid
      - sender
      - nonce
    - \_guid
    - payload
    - \_executor
    - \_extraData
  - `sendCompose`
    - \_lzSend() → \_lzReceive() + lzCompose()
- Message pattern
  - AB
  - ABA
  - Composed
  - Composed ABA
  - BatchSend
- Message ordering
  - Unordered
  - Ordered

# OFT implement OApp

# Others

- Pre-Crime ? https://medium.com/layerzero-official/introducing-pre-crime-49bef4a581d5
