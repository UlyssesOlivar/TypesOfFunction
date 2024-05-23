# ERC20
The technical description for smart contracts on the Ethereum network is called ERC-20 (Ethereum Request for Comment 20). The ERC-20 standard outlines the rules and functions that all tokens intended for usage on Ethereum must adhere to in order to be deemed ERC-20 compliant. It also provides guidance on how the given tokens should interact with one another. These guidelines include a wide range of related tasks, such as how to move tokens between wallets, show the total quantity of tokens in circulation, and find the balance of tokens in an Ethereum account. When it comes to launching initial coin offers (ICOs) and deploying different decentralized apps (DApps), ERC-20 tokens have taken over as the most popular kind on the Ethereum network. Developers can benefit from simplicity when standard ERC-20 tokens are created.

# GETTING STARTED
Remix is an online Solidity IDE that may be used to run this software; to get started, visit the Remix website at https://remix.ethereum.org.

Click the "+" symbol in the left-hand sidebar to start a new file once you are on the Remix website. Save the file (LeviToken.sol, for example) using the.sol extension. The code below should be copied and pasted into the file:

/// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

import {ERC20} from "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {

    address owner;
    
    constructor(string memory name, string memory symbol) ERC20(name, symbol) {
        owner = msg.sender;
    }

    function mint(address account, uint256 amount) public {
        require(msg.sender == owner, "Only the owner of this contract can mint its tokens");
        _mint(account, amount);
    }
    
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
    
    function transfer(address reciever, uint256 amount) public override returns (bool) {
        _transfer(msg.sender, reciever, amount);
        require(balanceOf(msg.sender) >= amount, "Insufficient balance");
        return true;
    }
}

Select the "Solidity Compiler" tab from the sidebar on the left to begin compiling the code. Click the "Compile Module3.sol" button after ensuring that the "Compiler" option is selected to "0.8.0" (or another compatible version).

After the code has been compiled, choose "Module3.sol" from the list of contracts under "Deploy and run transactions" and click the deploy button.

The name and symbol of your token must be entered before the contract can be deployed. You can now use the mint, burn, and transact functions after that. You will receive a copy of the account address for transacting.

# Author
Olivar, Ulysses O. 3.1 BSIT
