# ERC20-ZK-Airdrop

# ERC20Verifier Contract

This is an implementation of the ERC20 token standard with additional features for Zero-Knowledge Proof (ZKP) verification and restriction of token transfers based on ZKP verification.

## Contract Details

The contract extends both the ERC20 and ZKPVerifier interfaces and implements the required functions for both. The ZKPVerifier interface defines methods for submitting ZKP proofs and managing their validity. The `_beforeProofSubmit` and `_afterProofSubmit` methods are implemented to handle the logic for verifying the submitted proofs.

The contract also has two mappings: `idToAddress` and `addressToId`, which are used to map user addresses to their corresponding identity IDs, as determined by the ZKP proofs. The constant `TRANSFER_REQUEST_ID` is defined with a value of 1 and is used to identify the type of ZKP proof required for a token transfer.

The `TOKEN_AMOUNT_FOR_AIRDROP_PER_ID` constant is defined to specify the amount of tokens to be given per identity during an airdrop.

The contract constructor takes two string arguments, `name_` and `symbol_`, which are used to initialize the ERC20 token's name and symbol.

## Token Transfer Restriction

The `_beforeTokenTransfer` method is overridden to include a requirement for ZKP proof validation before a token transfer can occur. This method checks whether the recipient of the transfer has provided a valid ZKP proof and only allows the transfer to proceed if the proof is valid.

## Usage

To use this contract, it must first be deployed on the Ethereum network. After deployment, you can interact with the contract using a web3 enabled wallet or through a custom front-end application.

Before a user can receive tokens, they must submit a valid ZKP proof and have their identity mapped to their Ethereum address in the idToAddress and addressToId mappings.

To transfer tokens, the sender must ensure that the recipient has provided a valid ZKP proof. If the recipient's proof is valid, the transfer can proceed as normal. If the proof is not valid, the transfer will be rejected.

## Notes
This contract is designed to work with a specific ZKP verification system and may require modifications to work with a different system.

The TRANSFER_REQUEST_ID constant and related logic are designed to only allow transfers to recipients who have provided a specific type of ZKP proof. If you want to allow transfers to recipients without this proof, you should remove or modify this logic.

The TOKEN_AMOUNT_FOR_AIRDROP_PER_ID constant is provided as a placeholder and should be updated with the actual amount of tokens to be given out during an airdrop.

This contract is provided as-is and without warranty. It is your responsibility to thoroughly test the contract and ensure that it meets your requirements before deploying it to a production environment.
