# Design Pattern

## Factory Pattern

```
contract Factory {
  address[] deployed;
  function deploy() public {}
}
```

- https://github.com/safe-global/safe-singleton-factory

## Proxy Pattern

```
contract Proxy {
  address public implementation;
  function upgradeImplementation(address newImplementation) public {
    implementation = newImplementation;
  }
  fallback() external {
    // Forward function calls to the implementation contract
    (bool success, ) = implementation.delegatecall(msg.data);
    require(success, "Call to implementation failed");
  }
}
```

## State Machine

```
contract MultiSigWallet {
    // State Machine: Pending, Approved, Rejected
    enum ProposalState {
        Pending,
        Approved,
        Rejected
    }
    struct Proposal {
        address to;
        uint256 value;
        bytes data;
        ProposalState state;
        uint256 approvals;
    }
    Proposal[] public proposals;
    mapping(address => bool) public isOwner;
    mapping(uint256 => mapping(address => bool)) public hasApproved;
    modifier onlyOwner() {
        require(isOwner[msg.sender], "Not an owner");
        _;
    }

    function submitProposal(
        address to,
        uint256 value,
        bytes memory data
    ) public onlyOwner {
        // Create a new proposal
        proposals.push(Proposal(to, value, data, ProposalState.Pending, 0));
    }

    function approveProposal(uint256 proposalId) public onlyOwner {
        Proposal storage proposal = proposals[proposalId];
        require(!hasApproved[proposalId][msg.sender], "Already approved");
        require(
            proposal.state == ProposalState.Pending,
            "Proposal not pending"
        );
        proposal.approvals++;
        hasApproved[proposalId][msg.sender] = true;
        if (proposal.approvals >= (ownersCount() / 2) + 1) {
            executeProposal(proposalId);
        }
    }

    function executeProposal(uint256 proposalId) internal {
        Proposal storage proposal = proposals[proposalId];
        (bool success, ) = proposal.to.call{value: proposal.value}(
            proposal.data
        );
        require(success, "Transaction failed");
        proposal.state = ProposalState.Approved;
    }

    function ownersCount() public view returns (uint256) {
        uint256 count = 0;
        for (uint256 i = 0; i < proposals.length; i++) {
            if (isOwner[proposals[i].to]) {
                count++;
            }
        }
        return count;
    }
}
```

## Withdrawal Pattern

```
contract Wallet {
    mapping(address => uint256) public balances;

    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }

    function withdraw(uint256 amount) public {
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
        (bool success, ) = msg.sender.call{value: amount}("");
        require(success, "Transfer failed");
    }
}
```

## Library Pattern

```
library MathUtils {
    function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        require(c >= a, "Overflow detected");
        return c;
    }
}
```
