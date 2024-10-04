# Typeoffunction-eth-avx
DegenToken Smart Contract
Welcome to the DegenToken project, developed as part of the Metacrafters program. This project demonstrates proficiency in Solidity, smart contracts, and ERC20 token standards by creating a token system that integrates real-world use cases, including minting, transferring, redeeming for NFTs, and burning tokens.

Overview
DegenToken is an ERC20-compliant token designed for a gaming or reward system where players can earn, transfer, and redeem tokens for exclusive in-game NFTs. The smart contract includes essential functionalities that align with decentralized token economies, focusing on transparency, ownership, and user interaction.

Features
Minting Tokens:

The contract owner has the exclusive ability to mint new tokens to reward players or increase supply.
Transferring Tokens:

Players can transfer tokens to other users, enabling a decentralized trading system within the platform.
Redeeming for NFTs:

Players can redeem tokens for exclusive NFTs representing iconic landmarks and artworks. The redemption process burns the respective token amount, ensuring a balanced token economy.
Burning Tokens:

Users can burn their tokens, reducing the overall supply and managing scarcity.
Checking Collections:

Users can view their redeemed NFTs, showcasing the items they’ve earned through the platform.


1. Minting Tokens
   function mint(address to, uint256 amount) public onlyOwner
Purpose: Mints new tokens for specified users.
Access: Only the owner can execute this function.
2. Transferring Tokens
function transferToken(address _receiver, uint256 val) external
Purpose: Transfers Degen tokens between users.
Access: Public.
3. Redeeming Tokens
function redeemToken(uint256 NFTId) external payable
Purpose: Redeems tokens for NFTs, burning the corresponding token amount.
Access: Public.
4. Burning Tokens
function burn(uint256 val) public
Purpose: Burns tokens that are no longer needed.
Access: Public.
5. Viewing NFT Collections
function showUserCollection(address user) public view returns (uint256[] memory)
Purpose: Displays a user’s NFT collection.
Access: Public.
Available NFTs for Redemption
The store offers a selection of landmark NFTs that can be redeemed using Degen tokens:

Eiffel Tower: 440 tokens
Mona Lisa: 100 tokens
Great Wall of China: 200 tokens
Statue of Liberty: 350 tokens
Mount Everest: 390 tokens
Colosseum: 410 tokens
Sydney Opera House: 600 tokens
Big Ben: 400 tokens
Deployment and Testing
This contract was developed and tested using the following tools:

Solidity v0.8.18: For writing the smart contract.
OpenZeppelin: To leverage battle-tested ERC20 and ownership standards.
Remix IDE: For deployment and interaction testing.
#code 

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

//1. Minting new tokens: The platform should be able to create new tokens and distribute them to players as rewards. Only the owner can mint tokens.
//2. Transferring tokens: Players should be able to transfer their tokens to others.
//3. Redeeming tokens: Players should be able to redeem their tokens for items in the in-game store.
//4. Checking token balance: Players should be able to check their token balance at any time.
//5. Burning tokens: Anyone should be able to burn tokens, that they own, that are no longer needed.

contract DegenToken is ERC20 {
    struct Store {
        string name;
        uint256 price;
    }
    
    struct UserCollection {
        uint256 id;
    }
    address public owner;
    mapping(uint256 => Store) public redeemableNFT;
    mapping(address => mapping(uint256 => uint256)) public NFTsCollection;
    mapping(address => UserCollection[]) public userCollections;

    constructor() ERC20("Degen Token", "DEGEN") {
        owner = msg.sender;
        redeemableNFT[1] = Store("NFT: Eiffel Tower", 440);
        redeemableNFT[2] = Store("NFT: Mona Lisa", 100);
        redeemableNFT[3] = Store("NFT: Great Wall of China", 200);
        redeemableNFT[4] = Store("NFT: Statue of Liberty", 350);
        redeemableNFT[5] = Store("NFT: Mount Everest", 390);
        redeemableNFT[6] = Store("NFT: Colosseum", 410);
        redeemableNFT[7] = Store("NFT: Sydney Opera House", 600);
        redeemableNFT[8] = Store("NFT: Big Ben", 400);
        
    }
     modifier onlyOwner() {
        require(msg.sender == owner, "Only the contract owner can call this function you can't");
        _; 
    }

function mint(address to, uint256 amount) public onlyOwner {
    _mint(to, amount);
}

function burn(uint256 val) public {
    require(balanceOf(msg.sender) >= val, "You don't have enough Degen tokens to burn");
    _burn(msg.sender, val);
}

function transferToken(address _receiver, uint256 val) external {
    require(balanceOf(msg.sender) >= val, "You don't have enough Degen tokens to transfer");
    _transfer(msg.sender, _receiver, val);
}

function redeemToken(uint256 NFTId) external payable {
    require(balanceOf(msg.sender) >= redeemableNFT[NFTId].price, "You don't have enough Degen tokens to redeem");
    _burn(msg.sender, redeemableNFT[NFTId].price);
    NFTsCollection[msg.sender][NFTId] += 1;
    userCollections[msg.sender].push(UserCollection(NFTId));
}

    function showUserCollection(address user) public view returns (uint256[] memory) {
        uint256[] memory userCollection = new uint256[](8);

        for (uint256 i = 1; i <= 8; i++) {
            userCollection[i-1] = NFTsCollection[user][i]; 
        }

        return userCollection;
    }



    function showStore() external pure returns (string memory) {
        return "Landmark: Eiffel Tower\n2. Artwork: Mona Lisa\n3. Structure: Great Wall of China\n4. Monument: Statue of Liberty\n5. Peak: Mount Everest\n6. Mausoleum: Taj Mahal\n7. Landmark: Hollywood Sign\n8. Amphitheater: Colosseum\n9. Building: Sydney Opera House\n10. Clock Tower: Big Ben";
    }
}
License
This project is licensed under the MIT License.
#Author 
prince kumar
email:kumarprincerajput124@gmail.com
