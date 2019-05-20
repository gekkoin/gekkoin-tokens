# gekkoin-tokens
Fiat tokens on [GEKKOIN](https://gekkoin.com) network. <br />
Currently there is only one Gekkoin token - Gekkoin EUR Token (GKE). <br />
Token for USD (GKU) is coming soon.

# Contracts
The implementation is fairly simple and straightforward.
## Gekkoin EUR Token
The Gekkoin EUR Token offers a number of capabilities, which briefly are described below.

### ERC20 compatible
The Gekkoin EUR Token implements the ERC20 interface.

### Minting/Burning
Tokens can be minted or burned on demand. The contract supports minting only by `owner`.

### Ownable
The contract has an Owner, who can change the `owner` address.
