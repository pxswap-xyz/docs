# PxLend
[Git Source](https://github.com/pxswap-xyz/pxswap/blob/2c1b5e496d31f38806f41c98ffce3d93b591270c/src/PxLend.sol)

**Inherits:**
[ILendData](/src/utils/ILendData.sol/contract.ILendData.md), [Ownable](/src/utils/Ownable.sol/contract.Ownable.md), [ERC721Holder](/src/utils/ERC721Holder.sol/contract.ERC721Holder.md), ERC1155Receiver, ERC1155Holder

**Authors:**
pxswap (https://github.com/pxswap-xyz/pxswap/blob/main/src/Pxswap.sol), Ali Konuk - @alikonuk1

*This contract is for lending and borrowing non-fungible tokens (NFTs)*

*Please reach out to ali@pxswap.xyz if you find any issues*


## State Variables
### beneficiary

```solidity
address payable private beneficiary;
```


### SECONDS_IN_DAY

```solidity
uint256 private constant SECONDS_IN_DAY = 86400;
```


### lendingID

```solidity
uint256 private lendingID = 1;
```


### borrowingID

```solidity
uint256 private borrowingID = 1;
```


### borrowFee

```solidity
uint256 public borrowFee = 100;
```


### tokenMap

```solidity
mapping(uint8 => address) private tokenMap;
```


### lendings

```solidity
mapping(bytes32 => Lending) private lendings;
```


### borrowings

```solidity
mapping(bytes32 => Borrowing) private borrowings;
```


## Functions
### constructor


```solidity
constructor(address payable beneficiary_);
```

### lend


```solidity
function lend(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory lendAmount,
    uint8[] memory maxBorrowDuration,
    bytes4[] memory dailyBorrowPrice,
    uint8[] memory paymentToken,
    bool[] memory willAutoRenew
) external;
```

### stopLend


```solidity
function stopLend(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory _lendingID
) external;
```

### borrow


```solidity
function borrow(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory _lendingID,
    uint8[] memory borrowDuration,
    uint256[] memory borrowAmount
) external payable;
```

### stopBorrow


```solidity
function stopBorrow(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory _lendingID,
    uint256[] memory _borrowingID
) external;
```

### claimBorrow


```solidity
function claimBorrow(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory _lendingID,
    uint256[] memory _borrowingID
) external;
```

### handleLend


```solidity
function handleLend(ILendData.CallData memory cd) internal;
```

### handleStopLend


```solidity
function handleStopLend(ILendData.CallData memory cd) internal;
```

### handleBorrow


```solidity
function handleBorrow(ILendData.CallData memory cd) internal;
```

### handleStopBorrow


```solidity
function handleStopBorrow(ILendData.CallData memory cd) private;
```

### handleClaimBorrow


```solidity
function handleClaimBorrow(CallData memory cd) private;
```

### manageWillAutoRenew


```solidity
function manageWillAutoRenew(
    ILendData.Lending storage lending,
    ILendData.Borrowing storage borrowing,
    address nftAddress,
    ILendData.NFTStandard nftStandard,
    uint256 tokenID,
    uint256 lendingID
) internal;
```

### bundleCall


```solidity
function bundleCall(function(ILendData.CallData memory) handler, ILendData.CallData memory cd) internal;
```

### takeFee


```solidity
function takeFee(uint256 borrowAmt, ERC20 token) internal returns (uint256 fee);
```

### distributePayments


```solidity
function distributePayments(
    ILendData.Lending memory lending,
    ILendData.Borrowing memory borrowing,
    uint256 secondsSinceBorrowStart
) private;
```

### distributeClaimPayment


```solidity
function distributeClaimPayment(ILendData.Lending memory lending, ILendData.Borrowing memory borrowing) internal;
```

### safeTransfer


```solidity
function safeTransfer(
    CallData memory cd,
    address from,
    address to,
    uint256[] memory tokenID,
    uint256[] memory lendAmount
) internal;
```

### getLending9CFF8D4


```solidity
function getLending9CFF8D4(address nftAddress, uint256 tokenID, uint256 _lendingID)
    external
    view
    returns (uint8, address, uint8, bytes4, uint16, uint16, uint8);
```

### getBorrowing144DC65D


```solidity
function getBorrowing144DC65D(address nftAddress, uint256 tokenID, uint256 _borrowingID)
    external
    view
    returns (address, uint16, uint8, uint32);
```

### createLendCallData


```solidity
function createLendCallData(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory lendAmount,
    uint8[] memory maxBorrowDuration,
    bytes4[] memory dailyBorrowPrice,
    uint8[] memory paymentToken,
    bool[] memory willAutoRenew
) internal pure returns (CallData memory cd);
```

### createBorrowCallData


```solidity
function createBorrowCallData(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory _lendingID,
    uint8[] memory borrowDuration,
    uint256[] memory borrowAmount
) internal pure returns (CallData memory cd);
```

### createActionCallData


```solidity
function createActionCallData(
    ILendData.NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory _lendingID,
    uint256[] memory _borrowingID
) internal pure returns (CallData memory cd);
```

### unpackPrice


```solidity
function unpackPrice(bytes4 price, uint256 scale) internal pure returns (uint256);
```

### sliceArr


```solidity
function sliceArr(uint256[] memory arr, uint256 fromIx, uint256 toIx, uint256 arrOffset)
    internal
    pure
    returns (uint256[] memory r);
```

### isNotZero


```solidity
function isNotZero(address addr) internal pure;
```

### isZero


```solidity
function isZero(address addr) internal pure;
```

### isReturnable


```solidity
function isReturnable(Borrowing memory borrowing, address msgSender, uint256 blockTimestamp) internal pure;
```

### isPastReturnDate


```solidity
function isPastReturnDate(Borrowing memory borrowing, uint256 nowTime) internal pure returns (bool);
```

### getPaymentToken


```solidity
function getPaymentToken(uint8 paymentToken) internal view returns (address);
```

### setPaymentToken


```solidity
function setPaymentToken(uint8 paymentToken, address t) external payable onlyOwner;
```

### setBorrowFee


```solidity
function setBorrowFee(uint256 borrowFee_) external payable onlyOwner;
```

### setBeneficiary


```solidity
function setBeneficiary(address payable beneficiary_) external payable onlyOwner;
```

