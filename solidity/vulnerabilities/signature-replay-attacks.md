# Remediation

- Store every message hash that has been processed
- Include the address of contract
- Using nonce
- Include `chainId`
- Include `parameters`
- Include expiration timestamp
- `ecrecover()` which returns 0 if the signature is invalid
