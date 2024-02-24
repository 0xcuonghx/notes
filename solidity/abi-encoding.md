# ABI encoding

- `abi.decode(bytes memory encodedData, (...)) returns (...)`
- `abi.encode(...) returns (bytes memory)`
- `abi.encodePacked(...) returns (bytes memory)`
- `abi.encodeWithSelector(bytes4 selector, ...) returns (bytes memory)`
- `abi.encodeCall(function functionPointer, (...)) returns (bytes memory)`
- `abi.encodeWithSelector(functionPointer.selector, (...))`
- `abi.encodeWithSignature(string memory signature, ...) returns (bytes memory)`
