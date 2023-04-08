# ERC721Holder
[Git Source](https://github.com/pxswap-xyz/pxswap/blob/2c1b5e496d31f38806f41c98ffce3d93b591270c/src/utils/ERC721Holder.sol)

**Inherits:**
[IERC721Receiver](/src/utils/IERC721Receiver.sol/contract.IERC721Receiver.md)

*Implementation of the {IERC721Receiver} interface.
Accepts all token transfers.
Make sure the contract is able to use its token with {IERC721-safeTransferFrom}, {IERC721-approve} or {IERC721-setApprovalForAll}.*


## Functions
### onERC721Received

*See {IERC721Receiver-onERC721Received}.
Always returns `IERC721Receiver.onERC721Received.selector`.*


```solidity
function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4);
```

