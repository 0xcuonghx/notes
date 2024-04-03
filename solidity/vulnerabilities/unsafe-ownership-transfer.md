- Transferring ownership of your contract, e.g. when transferring governance rights or even changing your proxy admin, it’s scary
- Use an ACK method for approve the new owner.

```solidity
    address private _owner;
    address private _ownerCandidate;
    /**
     * @dev Enqueues the ownership transfer of the contract to a new account (`newOwnerCandidate`).
     * Can only be called by the current owner.
     */
    function transferOwnership(address newOwnerCandidate) public virtual onlyOwner {
        _ownerCandidate = newOwnerCandidate;
    }

    /**
     * @dev Confirms the ownership transfer of the contract to a new account.
     * Can only be called by the new owner candidate.
     */
    function confirmOwnershipTransfer() public virtual {
        require(_ownerCandidate == _msgSender(), "Ownable: caller is not the owner candidate");
        _transferOwnership(_ownerCandidate);
    }
```
