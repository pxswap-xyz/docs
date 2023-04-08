# Ownable
[Git Source](https://github.com/pxswap-xyz/pxswap/blob/2c1b5e496d31f38806f41c98ffce3d93b591270c/src/utils/Ownable.sol)


## State Variables
### _owner

```solidity
address private _owner;
```


## Functions
### constructor


```solidity
constructor();
```

### onlyOwner


```solidity
modifier onlyOwner();
```

### owner


```solidity
function owner() public view virtual returns (address);
```

### _checkOwner


```solidity
function _checkOwner() internal view virtual;
```

### transferOwnership


```solidity
function transferOwnership(address newOwner) public virtual onlyOwner;
```

### _transferOwnership


```solidity
function _transferOwnership(address newOwner) internal virtual;
```

## Events
### OwnershipTransferred

```solidity
event OwnershipTransferred(address indexed previousOwner, address indexed newOwner);
```

