# My Token

This Solidity program is a simpleprogram that demonstrates the basic syntax and functionality of the Solidity programming language to create a token. 
## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The MyToken contract is a basic implementation of a token contract in Solidity. It includes public variables TokenName, TokenAbr, and TotalSupply to store details about the token's name, abbreviation, and total supply respectively. The contract also utilizes a mapping balances to keep track of token balances for each address. Two essential functions are defined: mint and burn. The mint function increases the total supply by a specified _value and adds _value tokens to the balance of _address. The burn function decreases the total supply by _value and subtracts _value tokens from the balance of _address, but only if _address has sufficient tokens to burn, ensuring no tokens are burned if the balance is insufficient. The use of conditionals in burn ensures the contract follows the requirement that the balance of _address must be greater than or equal to the amount being burned. This contract serves as a foundational example demonstrating token minting and burning functionalities with basic integrity checks for token balances.
## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```javascript
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
    string public TokenName='Bitcoin';
    string public TokenAbr='BTC';
    uint public TotalSupply=0;

    // mapping variable here
    mapping(address=>uint)public balances;

    // mint function
    function mint(address _address,uint _value)public{
        TotalSupply +=_value;
        balances[_address] +=_value;
    }

    // burn function
    function burn(address _address,uint _value)public{
        if(balances[_address]>=_value){
            TotalSupply -=_value;
            balances[_address] -=_value;
        }
        
    }

}


```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile My Token.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "My Token" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the mint and burn functions .

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
