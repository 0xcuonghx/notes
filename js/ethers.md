# Solidity error handler

## Types

These are the possible `ErrorType` that could be returned as the `type` property in the `DecodedError` object:

| Type                        | Description                               |
| --------------------------- | ----------------------------------------- |
| `ErrorType.EmptyError`      | Contract reverted without reason provided |
| `ErrorType.RevertError`     | Contract reverted with reason provided    |
| `ErrorType.PanicError`      | Contract reverted due to a panic error    |
| `ErrorType.CustomError`     | Contract reverted due to a custom error   |
| `ErrorType.UserRejectError` | User rejected the transaction             |
| `ErrorType.RpcError`        | An error from the JSON RPC                |
| `ErrorType.UnknownError`    | An unknown error was thrown               |

## Handler

- https://raw.githubusercontent.com/superical/ethers-decode-error
