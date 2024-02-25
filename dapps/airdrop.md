```
/// @notice Transfer ERC20 tokens to multiple addresses
contract Airdrop {
    /// @notice Transfer ERC20 tokens to multiple addresses, authorization is required before use
    ///
    /// @param _token The address of ERC20 token for transfer
    /// @param _addresses The array of airdrop addresses
    /// @param _amounts The array of amount of tokens (airdrop amount for each address)
    function multiTransferToken(
        address _token,
        address[] calldata _addresses,
        uint256[] calldata _amounts
        ) external {
        // Check: The length of _addresses array should be equal to the length of _amounts array
        require(_addresses.length == _amounts.length, "Lengths of Addresses and Amounts NOT EQUAL");
        IERC20 token = IERC20(_token); // Declare IERC contract variable
        uint _amountSum = getSum(_amounts); // Calculate the total amount of airdropped tokens
        // Check: The authorized amount of tokens should be greater than or equal to the total amount of airdropped tokens
        require(token.allowance(msg.sender, address(this)) >= _amountSum, "Need Approve ERC20 token");

        // for loop, use transferFrom function to send airdrops
        for (uint256 i; i < _addresses.length; i++) {
            token.transferFrom(msg.sender, _addresses[i], _amounts[i]);
        }
    }

    /// Transfer ETH to multiple addresses
    function multiTransferETH(
        address payable[] calldata _addresses,
        uint256[] calldata _amounts
    ) public payable {
        // Check: _addresses and _amounts arrays should have the same length
        require(_addresses.length == _amounts.length, "Lengths of Addresses and Amounts NOT EQUAL");
        // Calculate total amount of ETH to be airdropped
        uint _amountSum = getSum(_amounts);
        // Check: transferred ETH should equal total amount
        require(msg.value == _amountSum, "Transfer amount error");
        // Use a for loop to transfer ETH using transfer function
        for (uint256 i = 0; i < _addresses.length; i++) {
            _addresses[i].transfer(_amounts[i]);
        }
    }


    // sum function for arrays
    function getSum(uint256[] calldata _arr) public pure returns(uint sum)
    {
        for(uint i = 0; i < _arr.length; i++)
            sum = sum + _arr[i];
    }
}
```
