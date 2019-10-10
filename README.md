# gekkoin-tokens
Fiat tokens on [GEKKOIN](https://gekkoin.com) ecosystem.

Currently there is only one Gekkoin token in the ecosystem - Gekkoin EUR Token (EURG).

# Contracts
The implementation is fairly simple and straightforward.

The address of deployed contract - `TBD`.

The Gekkoin EUR Token contract (GekkoinEURToken) functionality is described below.

## ERC20 compatible
The Gekkoin EUR Token implements the ERC20 interface. It utilizes standard `StandardToken` and `BasicToken` contracts that only include following functions:

View functions:

`totalSupply`- returns Gekkoin total supply

`balanceOf` - returns token balance of account

`allowance` - returns account allowance for specified account

Public functions:

`transfer` - transfers tokens to specified account

`transferFrom` - transfers tokens from specified account to some account

`approve` - approves allowance for specified account

### BurnableToken
GKE tokens can be burned by any account on demand. `BurnableToken` contract inherits `BasicToken` and implements 2 functions:

`_burn` - internal function for token burn

`burn` - public function that calls `_burn`

### MintableToken
GKE tokens can be minted by owner account.

Original `MintableToken` contract inherits `StandardToken`, `Ownable` and implements 2 functions and 2 modifiers:

modifier `canMint` - checks whether minting is finished

modifier `hasMintPermission` - checks whether function caller is `owner`

function `mint` - mints tokens to specified account. The function has `hasMintPermission`, `canMint` modifiers

function `finishMinting` - finishes minting. The function has `hasMintPermission`, `canMint` modifiers. After the function was called it's impossible to mint any new tokens

As far as Gekkoin EUR Token is stable coin, minting is unlimited. Modifier `canMint` and function `finishMinting`  were removed from original OpenZeppelin implementation (parameter mintingFinished and event MintFinished as well).

### Access control
The Gekkoin EUR Token contract is Ownable contract. These functions can be only called by owner: `transferOwnership`, `mint`.

Function renounceOwnership was removed from original OpenZeppelin implementation (with OwnershipRenounced event).

## GekkoinEURToken
GekkoinEURToken inherits from `MintableToken`, `BurnableToken`. GekkoinEURToken sets name to `Gekkoin EUR Token`; symbol = `EURG`; decimals to `18`.

## Compiling
Gekkoin EUR token is truffle project. In order to compile the run  `truffle compile`
