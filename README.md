# Create and mint token

In this Solidity program  we create and manage a token by creating a smart contract. In the contract, we use ERC20 to add functionalities like total supply, balances, transferring tokens and many more.

## Description

This program is a written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain.In this contract, we have inherited two contracts ERC20.sol and Ownable.sol from the OpenZeppelin to add the functionalities of ERC-20 tokens. The contract have three functions-the mint function , burn function and the transfer function. The mint function takes two parameters: an address and a value. This function is only accessable to the owner i.e. only the owner can mint the tokens in this contract. The burn function destroy tokens. It takes an address and value just like the mint functions. The transfer function is used to send tokens from the sender to the receipent address. Any user can use the burn and the transfer function function.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Create_token.sol). Copy and paste the following code into the file:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    // public variables here
    string public tokenName = "Metacrafters";
    string public tokenAbbrv = "Meta";

    // Owner address
    address public owner;

    constructor() ERC20(tokenName, tokenAbbrv) {
        owner = msg.sender; // Set the contract deployer as the owner
    }

    // Modifier that only allows the owner to perform the action
    modifier onlyOwner() {
        require(msg.sender == owner, "Only the owner can call this function");
        _;
    }

    //mint function code here increases balances
    function mint(address _address, uint _value) public onlyOwner {
        _mint(_address, _value);
    }

    //burn function code here opposite of mint function
    function burn(address _address, uint _value) public onlyOwner {
        _burn(_address, _value);
    }

    // transfer function
    function transfer(address recipient, uint256 amount) public override returns (bool) {
        _transfer(msg.sender, recipient, amount);
        return true;
    }
}




```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.0" (or another compatible version), and then click on the "Compile Create_token.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the mint, burn and  function. Now, provide the input for the mint and burn functions and then click on transact to get the output.

## Authors

Gungun
gungunbansal2604@gmail.com

## License

This project is licensed under the [MIT] License - see the LICENSE.md file for details
