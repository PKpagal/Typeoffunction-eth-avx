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
License
This project is licensed under the MIT License.
#Author 
prince kumar
email:kumarprincerajput124@gmail.com
