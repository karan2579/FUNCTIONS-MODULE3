# ETH-AVAX-Module-3-Contract
In this project we are suggested to create our own token on local HardHat. After that contract creater  should be able to mint tokens to a provided address. Any user should be able to burn and transfer tokens.

# Process of Connecting Hardhat Network with Remix
Step 1: Visit to  Project Directory Open your terminal and navigate to the project directory where my Solidity contract is Written.
Step 2: Run npm install @remix-project/remixd Command In the terminal, this  following command will start the remixd service:
npx remixd -s <project_directory>--remix-ide https://remix.ethereum.org
Now i will Replace <project_directory> with the absolute path of my project directory this will create a connection between Remix IDE and with your local project directory.
Step 3:Now i will open Remix IDE on our browser.
Step 4:Now i have to connect with Localhost Workspaces in my Remix IDE, Selecting "default_workspace" to "Localhost" button in the top-right "Workspaces" corner. As a result this will connect my  project directory on remix IDE.
Step 5:Afte writting our contract successfully now i will  Compile the contract in Remix IDE, find and open your ".sol" file in your contract folder and switch to the "Solidity Compiler" tab in the left hand side of IDE. NOw i wiil  click on the "Compile" button to compile the contract.
Follwing are my contract
```
solidity
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
```
Step 6: Now i will Deploy and Interact with the Contract. In Top left corner the "Environment" dropdown, and  select "Injected Web3" to connect to local Hardhat.
To interact with the contract effectively, we wiil follow these steps:

Go to the "Deployed Contracts" section and select the contract name.
Observe the available functions and variables of the contract.
Click the "Deploy" button to deploy the contract.
Once the contract is successfully deployed, we can interact with it functions as follows:

NOw I will Provide the required parameters for the function you want to use.
Click the corresponding function button to execute the function.
Congratulations! You have now connected your local Hardhat network with Remix, and you have deployed and interacted with a contract.

To ensure everything works smoothly, make sure that your local Hardhat network is running using npx hardhat node and that you have installed all necessary dependencies with npm install.

To customize the contract to suit your specific requirements, refer to the provided code and add relevant information and code in a well-structured manner within the Token contract.

## Authors
Karanveer Mittal

## License

This project is licensed under the MIT License
