# Project Title

Functions and errors.

## Description

A JavaScript function is a block of code designed to perform a particular task.


## Getting Started

You need an invitation to metacrafters to do this project.
### Executing program

* To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:



```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract UpdatedContract {
    address public owner; // Representing the owner of the contract
    mapping(address => uint) public balances;

    constructor() {
        owner = msg.sender; // Setting the contract deployer as the owner
    }

    function deposit() public payable {
        require(msg.value > 0, "Deposit amount must be greater than 0"); // Ensuring the deposit amount is greater than 0
        balances[msg.sender] += msg.value; // Adding the deposited amount to the sender's balance
    }

    function withdraw(uint amount) public {
        require(amount > 0, "Withdrawal amount should be greater than 0"); // Ensuring the withdrawal amount is greater than 0
        require(balances[msg.sender] >= amount, "Insufficient balance"); // Checking if the sender has enough balance

        balances[msg.sender] -= amount; // Subtracting the withdrawal amount from the sender's balance

        bool success = payable(msg.sender).send(amount); // Sending the amount to the sender
        require(success, "Transfer failed."); // Ensuring the transfer was successful
    }

    function doubleValue(uint value) public pure returns (uint) {
        uint result = value * 2; // Doubling the input value
        return result;
    }

    function safeDivision(uint value) public pure returns (uint) {
        require(value != 0, "Value cannot be 0"); // Requiring the input value to be non-zero
        return 100 / value; // Returning the result of 100 divided by the input value
    }
}

```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile HelloWorld.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "HelloWorld" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the sayHello function. Click on the "HelloWorld" contract in the left-hand sidebar, and then click on the "sayHello" function. Finally, click on the "transact" button to execute the function and retrieve the "Hello World!" message.
## Help
You must have a laptop and strong internet.
```
command to run if program contains helper info
```

## Authors

Contact info

Quezie Obrique 
8210606@ntc.edu.ph
## License

This project is licensed under the [MIT license] License - see the LICENSE.md file for details
