// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {
    // public variables here
    string public tokenname = "Microprocessor";
    string public tokenAbbrv = "MP";
    uint public totalSupply = 0;
    address public owner;

    // mapping variable here
    mapping(address => uint) public myamount;

    // constructor to set the contract owner
    constructor() {
        owner = msg.sender;
    }

    // modifier to restrict certain functions to the owner
    modifier onlyOwner() {
        require(msg.sender == owner, "Only onwer can perform the action");
        _;
    }

    // mint function - only the owner can mint new tokens
    function mint(address _address, uint _cost) public onlyOwner {
        totalSupply += _cost;
        myamount[_address] += _cost;
    } 

    // burn function
    function burn(address _address, uint _cost) public {
        require(myamount[_address] >= _cost, "Insufficient balance to burn");
        totalSupply -= _cost;
        myamount[_address] -= _cost;
    }

    // transfer function
    function transfer(address _to, uint _amount) public {
        require(_to != address(0), "Invalid recipient address");
        require(myamount[msg.sender] >= _amount, "Insufficient balance");

        myamount[msg.sender] -= _amount;
        myamount[_to] += _amount;
    }
}
