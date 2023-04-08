# SwapData
[Git Source](https://github.com/pxswap-xyz/pxswap/blob/2c1b5e496d31f38806f41c98ffce3d93b591270c/src/SwapData.sol)


## Structs
### Swap

```solidity
struct Swap {
    uint256[] giveId;
    uint256 amount;
    uint256 ethAmount;
    address seller;
    address buyer;
    address[] giveNft;
    address[] wantNft;
    address wantToken;
    bool active;
}
```

