# Unit Protocol: Liquidator contract

## Overview

Manages liquidation process.

<br >


## Liquidator UML diagram

<span style="color:red">**UPDATE** diagram</span>

<p align="center">
  <img alt="Liquidator UML diagram" src = "./images/svg/Liquidator.svg">
</p>

<br >


## Is Liquidatable Position

Determines whether a position is liquidatable.

<br >


```javascript
function isLiquidatablePosition(address token, address user) public view returns (bool)
```

* token:  The address of token using as main collateral.
* user: The owner of a position.
* RETURN: Whether a position is liquidatable.

<br >


## Get Collateralization Ratio

Calculates position's collateral ratio based on collateral proportion.

<br >


```javascript
function CR(uint mainUsdValue, uint colUsdValue, uint debt) public pure returns (uint)
```

* mainUsdValue: USD value of main collateral in position.
* colUsdValue: USD value of COL amount in position.
* debt: USDP borrowed.
* RETURN: Collateralization ratio of a position.

<br >


## Get Liquidation Ratio

Calculates position's liquidation ratio based on collateral proportion.

<br >


```javascript
function LR(address asset, uint mainUsdValue, uint colUsdValue) public view returns(uint)
```

* asset: The address of the main collateral token of a position.
* mainUsdValue: USD value of main collateral in position.
* colUsdValue: USD value of COL amount in position.
* RETURN: Liquidation ratio of a position.

<br >


## Liquidate

Triggers liquidation process. Funds transfers directly to the liquidation system's address.


<br >


```javascript
function liquidate(address asset, address user, USDPLib.ProofData memory mainPriceProof, USDPLib.ProofData memory colPriceProof) public
```

* msg.sender: The account which shall liquidate the borrower.
* asset: The address of the main collateral token of a position.
* user: The owner of a position.
* mainPriceProof: ProofData struct for the main collateral token price.
* colPriceProof: ProofData struct for the COL token price.

<br >