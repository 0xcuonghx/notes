contract Faucet {

    uint256 public amountAllowed = 100; // the allowed amount for each request is 100
    address public tokenContract;   // contract address of the token
    mapping(address => bool) public requestedAddress;   // a map contains requested address

    // Event SendToken
    event SendToken(address indexed Receiver, uint256 indexed Amount);

    // Set the ERC20'S contract address during deployment
    constructor(address _tokenContract) {
        tokenContract = _tokenContract; // set token contract
    }

    // Function for users to request tokens
    function requestTokens() external {
        require(requestedAddress[msg.sender] == false, "Cannot Request Multiple Times!"); // Only one request per address
        IERC20 token = IERC20(tokenContract); // Create an IERC20 contract object
        require(token.balanceOf(address(this)) >= amountAllowed, "Faucet Empty!"); // Faucet is empty

        token.transfer(msg.sender, amountAllowed); // Send token
        requestedAddress[msg.sender] = true; // Record the requested address

        emit SendToken(msg.sender, amountAllowed); // Emit SendToken event
    }

}
