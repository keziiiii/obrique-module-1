/ SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyContract {
    address public kezi;  // Setting 'kezi' as the owner
    mapping(address => uint) public balances;

    constructor() {
        kezi = msg.sender;  // Initializing 'kezi' as the contract deployer
    }

    function deposit() public payable {
        require(msg.value > 0, "Value must be greater than 0");  // Ensuring the deposit amount is greater than 0
        balances[msg.sender] += msg.value;  // Updating the balance mapping for the sender
    }

    function withdraw(uint amount) public {
        require(amount > 0, "Withdrawal amount should be greater than 0");  // Ensuring the withdrawal amount is greater than 0
        require(balances[msg.sender] >= amount, "You have insufficient balance");  // Checking if the sender has enough balance

        balances[msg.sender] -= amount;  // Updating the balance mapping for the sender

        bool success = payable(msg.sender).send(amount);  // Sending the amount to the sender
        require(success, "Transfer failed.");  // Ensuring the transfer was successful
    }

    function assertE(uint value) public pure returns (uint) {
        uint result = value * 2;  // Doubling the input value
        assert(result > value);  // Asserting that the result is greater than the input value
        return result;
    }

    function revertE(uint value) public pure returns (uint) {
        require(value != 0, "Value cannot be 0");  // Requiring the input value to be non-zero
        return 100 / value;  // Returning the result of 100 divided by the input value
    }
}
  
