# ETH-Assessment
# MyToken Smart Contract

## Description
GarvCoin (GK) is a simple Solidity smart contract for a token named "Garv" with the abbreviation "GK". This contract allows for the minting and burning of tokens, along with tracking token balances and the total supply.

## Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
    string public Token_name = "Garv";
    string public Token_Abbrv = "GK";
    uint public totalSupply;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _to, uint _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    // burn function
    function burn(address _from, uint256 _value) public {
        if (balances[_from] >= _value) {
            totalSupply -= _value;
            balances[_from] -= _value;
        }
        // If the balance is insufficient, do nothing
    }
}
```
## Contract Details

The contract includes the following features:

### Public Variables:

- `Token_name`: The name of the token (Garv).
- `Token_Abbrv`: The abbreviation or symbol of the token (GK).
- `totalSupply`: The total supply of the token.

### Mapping:

- `balances`: A mapping from addresses to their token balances.

### Mint Function:

- `mint(address _to, uint _value)`: This function increases the total supply of tokens and the balance of the specified address by the given value.

### Burn Function:

- `burn(address _from, uint256 _value)`: This function decreases the total supply of tokens and the balance of the specified address by the given value, only if the address has a sufficient balance.

## Usage
1. Deploy the contract on a compatible Ethereum Virtual Machine (EVM) using a Solidity compiler. Or
You run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.
3. Interact with the contract using the defined functions:
   - `mint`: Mint new tokens and assign them to a specified address.
   - `burn`: Burn existing tokens from a specified address.
4. Ensure proper permission control and validation when calling contract functions to prevent unauthorized access or misuse.

## Authors

- Garv Kumar (garvkumar287@gmail.com)

## License
This contract is licensed under the MIT License. See the [LICENSE](LICENSE.md) file for details.
