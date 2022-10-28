# Pecunia

![](./pecunia.jpeg)

Pecunia provides clients the ability to ensure that their heirs will be able to get their share of the crypto and NFT once the client dies.
# Architecture:


## Smart Contracts and Zero-Knowledge Proof:

The smart contracts are deployed on the Polygon Test and written in solidity. Here is a description of 3 main smart contracts:

1. HeirToken — An ERC721 token that provides an additional security layer and proof that a heir is entitled to receive assets.
2. PecuniaLock — This is main smart contract responsible for registering the owner, reserving amounts to heir and withdraw signature 
3. Verifier — verifies the ZK proof which is submitted by the heir/owner. This file is automatically generated by circom.

We have used Circom & snarkjs(groth16) to develop the circuits and creating the zero knowledge proofs. This ZKP is generated using the password, without revealing it to the verfier. The Heir executes the withdraw Signature and  proofs that he/she is the rightful heir. After the interval gets over the chainlink keepers transfer the amount to heirs.

ZK Proof are generated at two situations, first when the owner registers and the second time when the heir signs the `WithdrawSignature`. The proof is unique everytime it is generated but we are checking its uniqueness in our smart contracts to prevent used proof. The trusted setup is performed and the files generated are uploaded(though they should not be).

## Front End: 

The front of the Dapp is built using React and Ether.js helped us so much with communicating with our smart contract.


## Tech Stack
- REACT
- ZK SNARKS (using snarkjs and groth16)
- CIRCOM
- IPFS
- SEQUENCE WALLET
- CHAINLINK KEEPERS
- POLYGON
- SPHERON

# Installation
Create a `.env.local` file with following details `PRIVATE_KEY` and `MUMBAI_URL = https://matic-mumbai.chainstacklabs.com`. We have provided scripts for both deploying contracts to local `scripts/deploy_local.js` and testnet `scripts/deploy_new_net.js`.

-  Clone this Repo:
    ```
    git clone https://github.com/Alchemist21/pecunia
    ```

-   Install all dependencies:

    ```
    cd pecunia/
    yarn install
    ```

## Verified Smart Contract

PecuniaLock.sol: [0x45C38Ce5dDd5b34f2da4674cA0C3FeD18FB54dbb] (https://mumbai.polygonscan.com/address/0x45C38Ce5dDd5b34f2da4674cA0C3FeD18FB54dbb#code)

## Inspiration

Currently, there is no proper way to transfer crypto to the heirs or next of kin. So pecunia offer a safe way to do it.

## TODO/Areas For Improvement
- We will integrate DEXs which will allow the user to swap and deposit any token into his will by just depositing MATIC.
- We will be integrating functionality to deposit funds to different liquidity pools which will earn interest from the funds and including provision for dynamic NFTs(containing the real time balances that will be transferred to heir)
- We will introduce batch pay which will allow the transfer of funds to heir at multiple intervals. This will prevent the heir to carelessly spend all the funds at one go.

## Security Considerations

The Repository is currently not audited and is only meant for testing purposes on Testnets.