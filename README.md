# special-octo-garbanzo
non-custodial p2p nft swap

Overview
The P2PNFTExchange contract allows users to trade NFTs (non-fungible tokens) on the Ethereum blockchain without the need for a central custodian. It implements a peer-to-peer protocol in which users can initiate, cancel, and complete NFT swaps with each other.

Usage
To use the P2PNFTExchange contract, you will need an Ethereum wallet with a balance of ether and a connection to the Ethereum network.

Functions
The P2PNFTExchange contract has the following public functions:

initiateSwap(address _to, uint256 _tokenId)
This function is used to initiate an NFT swap with another user. It takes the following arguments:

_to: The Ethereum address of the user who will receive the NFT in the swap.
_tokenId: The ID of the NFT that will be swapped.
cancelSwap(address _to, uint256 _tokenId)
This function is used to cancel an NFT swap that has been initiated but not yet completed. It takes the same arguments as initiateSwap().

completeSwap(address _from, address _to, uint256 _tokenId)
This function is used to complete an NFT swap that has been initiated by another user. It takes the following arguments:

_from: The Ethereum address of the user who initiated the swap.
_to: The Ethereum address of the user who will receive the NFT in the swap (should be the same as the _to argument in the initiateSwap() call).
_tokenId: The ID of the NFT that will be swapped (should be the same as the _tokenId argument in the initiateSwap() call).
Events
The P2PNFTExchange contract emits the following events:

SwapInitiated(address _from, address _to, uint256 _tokenId)
This event is emitted when a swap is initiated by calling the initiateSwap() function. It includes the following arguments:

_from: The Ethereum address of the user who initiated the swap.
_to: The Ethereum address of the user who will receive the NFT in the swap.
_tokenId: The ID of the NFT that will be swapped.
SwapCancelled(address _from, address _to, uint256 _tokenId)
This event is emitted when a swap is cancelled by calling the cancelSwap() function. It includes the same arguments as SwapInitiated.

SwapCompleted(address _from, address _to, uint256 _tokenId)
This event is emitted when a swap is completed by calling the completeSwap() function. It includes the same arguments as SwapInitiated.

Examples
Here are some examples of how to use the P2PNFTExchange contract:

Initiating a swap
To initiate a swap, you can call the initiateSwap() function with the Ethereum address of the recipient and the ID of the NFT that you want to swap. For example:
p2pNFTExchange.initiateSwap("0x123456...", 123);

This will initiate a swap with the user at the specified address for the NFT with the ID 123.

Cancelling a swap
To cancel a swap, you can call the cancelSwap() function with the Ethereum address of the recipient and the ID of the NFT that you want to cancel the swap for. For example:
p2pNFTExchange.cancelSwap("0x123456...", 123);

This will cancel the swap for the NFT with the ID 123 with the user at the specified address.

Completing a swap
To complete a swap, you can call the completeSwap() function with the Ethereum address of the user who initiated the swap, the Ethereum address of the recipient, and the ID of the NFT that you want to complete the swap for. For example: 
p2pNFTExchange.completeSwap("0x123456...", "0x789012...", 123);
This will complete the swap for the NFT with the ID 123 between the two specified users.

Security considerations
It is important to note that the P2PNFTExchange contract does not provide any built-in mechanism for ensuring that the NFTs being traded are actually owned by the users who are initiating the swaps. As such, it is possible for users to attempt to initiate swaps for NFTs that they do not own.

It is up to the users of the P2PNFTExchange contract to ensure that they are only initiating swaps for NFTs that they actually own and have the right to trade. This can be done by verifying the ownership of the NFTs using an external contract or other means before initiating a swap.
