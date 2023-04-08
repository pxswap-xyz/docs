# Pxswap
[Git Source](https://github.com/pxswap-xyz/pxswap/blob/2c1b5e496d31f38806f41c98ffce3d93b591270c/src/Pxswap.sol)

**Inherits:**
[SwapData](/src/SwapData.sol/contract.SwapData.md), [Ownable](/src/utils/Ownable.sol/contract.Ownable.md), [HandleERC20](/src/utils/HandleERC20.sol/contract.HandleERC20.md), [HandleERC721](/src/utils/HandleERC721.sol/contract.HandleERC721.md), [ERC721Holder](/src/utils/ERC721Holder.sol/contract.ERC721Holder.md)

**Authors:**
pxswap (https://github.com/pxswap-xyz/pxswap/blob/main/src/Pxswap.sol), Ali Konuk - @alikonuk1

*This contract is for buying, selling and swapping non-fungible tokens (NFTs)*

*Please reach out to ali@pxswap.xyz if you find any issues*


## State Variables
### swaps

```solidity
Swap[] public swaps;
```


### protocol

```solidity
address public protocol;
```


### pxNft

```solidity
address public pxNft;
```


### flatFee

```solidity
uint256 public flatFee;
```


### discountedFee

```solidity
uint256 public discountedFee;
```


### fee

```solidity
uint256 public fee;
```


### mutex

```solidity
bool public mutex;
```


## Functions
### putSwap

*Creates a new swap by the seller with the specified NFTs and tokens offered.*


```solidity
function putSwap(
    address[] memory nftsGiven,
    uint256[] memory idsGiven,
    address[] memory nftsWanted,
    address buyer,
    address tokenWanted,
    uint256 amount,
    uint256 ethAmount
) external noReentrancy;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`nftsGiven`|`address[]`|Array of addresses of the NFTs given by the seller.|
|`idsGiven`|`uint256[]`|Array of IDs of the NFTs given by the seller.|
|`nftsWanted`|`address[]`|Array of addresses of the NFTs wanted by the seller.|
|`buyer`|`address`|The address of the buyer for the swap.|
|`tokenWanted`|`address`|The address of the ERC20 token wanted by the seller.|
|`amount`|`uint256`|The amount of ERC20 tokens wanted by the seller.|
|`ethAmount`|`uint256`|The amount of ether wanted by the seller. Emits a {PutSwap} event indicating the creation of the swap and its ID.|


### cancelSwap

*Allows the seller to cancel an active swap and transfer the ERC721 tokens back to the seller.*


```solidity
function cancelSwap(uint256 id) external noReentrancy;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`id`|`uint256`|The ID of the swap to be cancelled.|


### acceptSwap

*Allows the buyer to accept a swap by ID and transfer the assets to the respective parties.*


```solidity
function acceptSwap(uint256 id, uint256[] memory tokenIds) public payable noReentrancy;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`id`|`uint256`|The ID of the swap to be accepted.|
|`tokenIds`|`uint256[]`|An array of token IDs for ERC721 tokens.|


### setProtocol

*Function to set the protocol address.*


```solidity
function setProtocol(address protocol_) external onlyOwner;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`protocol_`|`address`|The address of the protocol.|


### setFee

*Allows the contract owner to set the transaction fee.*


```solidity
function setFee(uint256 fee_) external onlyOwner;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`fee_`|`uint256`|The new transaction fee.|


### setDiscountedFee

*Allows the contract owner to set the discounted transaction fee.*


```solidity
function setDiscountedFee(uint256 discountedFee_) external onlyOwner;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`discountedFee_`|`uint256`|The new discounted transaction fee.|


### setFlatFee

*Allows the contract owner to set the flat transaction fee.*


```solidity
function setFlatFee(uint256 flatFee_) external onlyOwner;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`flatFee_`|`uint256`|The new flat transaction fee.|


### setPxNft

*Allows the contract owner to set the pxswap's nft contract address.*


```solidity
function setPxNft(address pxNft_) external onlyOwner;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`pxNft_`|`address`|pxswap's nft contract address.|


### noReentrancy


```solidity
modifier noReentrancy();
```

### _nonReentrantBefore


```solidity
function _nonReentrantBefore() internal;
```

### _nonReentrantAfter


```solidity
function _nonReentrantAfter() internal;
```

### getLength

*Returns the number of swaps in the contract.*


```solidity
function getLength() external view returns (uint256);
```
**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`uint256`|The length of the swaps array.|


### getSwap

*Returns the details of a specific swap by its ID.*


```solidity
function getSwap(uint256 id) external view returns (Swap memory);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`id`|`uint256`|The ID of the swap to be retrieved.|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`Swap`|The details of the swap as a memory struct.|


## Events
### PutSwap

```solidity
event PutSwap(uint256 indexed id);
```

### CancelSwap

```solidity
event CancelSwap(uint256 indexed id);
```

### AcceptSwap

```solidity
event AcceptSwap(uint256 indexed id);
```

## Errors
### Unauthorized

```solidity
error Unauthorized();
```

### NotActive

```solidity
error NotActive();
```

### NotEnoughEth

```solidity
error NotEnoughEth();
```

