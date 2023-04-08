# ILendData
[Git Source](https://github.com/pxswap-xyz/pxswap/blob/2c1b5e496d31f38806f41c98ffce3d93b591270c/src/utils/ILendData.sol)


## Functions
### lend


```solidity
function lend(
    NFTStandard[] memory nftStandard,
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
    NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory lendingID
) external;
```

### borrow


```solidity
function borrow(
    NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory lendingID,
    uint8[] memory borrowDuration,
    uint256[] memory borrowAmount
) external payable;
```

### stopBorrow


```solidity
function stopBorrow(
    NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory lendingID,
    uint256[] memory borrowingID
) external;
```

### claimBorrow


```solidity
function claimBorrow(
    NFTStandard[] memory nftStandard,
    address[] memory nftAddress,
    uint256[] memory tokenID,
    uint256[] memory lendingID,
    uint256[] memory borrowingID
) external;
```

## Events
### Lend

```solidity
event Lend(
    bool is721,
    address indexed lenderAddress,
    address indexed nftAddress,
    uint256 indexed tokenID,
    uint256 lendingID,
    uint8 maxBorrowDuration,
    bytes4 dailyBorrowPrice,
    uint16 lendAmount,
    uint8 paymentToken,
    bool willAutoRenew
);
```

### Borrow

```solidity
event Borrow(
    address indexed borrowerAddress,
    uint256 lendingID,
    uint256 borrowingID,
    uint16 borrowAmount,
    uint8 borrowDuration,
    uint32 borrowedAt
);
```

### StopLend

```solidity
event StopLend(uint256 indexed lendingID, uint32 stoppedAt, uint16 amount);
```

### StopBorrow

```solidity
event StopBorrow(uint256 indexed borrowingID, uint32 stoppedAt);
```

### BorrowClaimed

```solidity
event BorrowClaimed(uint256 indexed borrowingID, uint32 collectedAt);
```

## Structs
### CallData

```solidity
struct CallData {
    uint256 left;
    uint256 right;
    NFTStandard[] nftStandard;
    address[] nftAddress;
    uint256[] tokenID;
    uint256[] lendAmount;
    uint8[] maxBorrowDuration;
    bytes4[] dailyBorrowPrice;
    uint256[] lendingID;
    uint256[] borrowingID;
    uint8[] borrowDuration;
    uint256[] borrowAmount;
    uint8[] paymentToken;
    bool[] willAutoRenew;
}
```

### Lending

```solidity
struct Lending {
    NFTStandard nftStandard;
    address payable lenderAddress;
    uint8 maxBorrowDuration;
    bytes4 dailyBorrowPrice;
    uint16 lendAmount;
    uint16 availableAmount;
    uint8 paymentToken;
    bool willAutoRenew;
}
```

### Borrowing

```solidity
struct Borrowing {
    address payable borrowerAddress;
    uint8 borrowDuration;
    uint32 borrowedAt;
    uint16 borrowAmount;
}
```

## Enums
### NFTStandard

```solidity
enum NFTStandard {
    E721,
    E1155
}
```

