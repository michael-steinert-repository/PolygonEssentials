# Polygon

* Polygon brings a trust-less bidirectional Transaction Chanel between Polygon and Ethereum by Introducing a Cross-Side Bridge
* With this Bridge a User can transfer his Tokens across Polygon without any Limitations, so it provides a Scaling Solution that is nearly free and highly flexible
* Token from the Ethereum Network are in the same Number locked as they are minted on the Polygon Network, so the Bagging of the Tokens is one to one

## Proof-of-Stake

* __Proof-of-Stake__ is a Type of Consensus Mechanism to achieve distributed Consensus
* It requires Users to stake their Ether to become a Validator in the Network
* Validators are responsible for ordering Transactions and Creating new Blocks so that all Nodes can agree on the State of the Network

## Ethereum Plasma

* Ethereum Plasma is an Off-Chain Scaling Technique
* It creates a Structure that consists of Side Chains, by doing so it should communicate and interact with the Main Chain (Ethereum) as little as possible
* This Structure is supposed to act as a Merkle Tree and be arranged in a certain Way hierarchically, thereby creating several smaller Chains on the Main Chain
* The smaller Chains are referred to as __Plasma Chains__
* Via Smart Contracts and Merkle Trees, an unlimited Number of Plasma Chains can be created, which are a smaller Copy of the parent Main Chain (Ethereum)
* The Ability to create additional Chains on top of the Plasma Chains forms the Tree Structure
* The Tree Structure facilitates Verification within the Trees of Chains, thus increasing the Efficiency of the Network
* Each Plasma Chain is a customizable Smart Contract and can Function in a unique Way to meet different Needs
* __Plasma Sharding__ is used to separate the entire Blockchain into smaller, independent Parts (__Shards__), thus increasing the Efficiency of the Blockchain
* Shards no longer need to check all Blocks to confirm their Transactions, but only the Blocks of the individual Shards - this allows individual Nodes to process their Transactions faster
* __Fraud Proof__ allows Plasma Chains to submit a Complaint to their Parent Chain - this may be the Case if the Plasma Chains cannot agree on a Consensus

## Polygon's hybrid Security Model (Proof-of-Stake and Plasma)

* Polygon uses a dual Consensus Mechanism - a Combination of Plasma and PoS that optimizes the Speed and Decentralization of the Polygon Network
* Polygon brings a trust-less two-way Transaction Chanel between Polygon and Ethereum by introducing a Cross-Chain Bridge with Plasma Bridge and PoS Bridge
* A Bridge allows swapping Tokens between a Root Chain and Child Chain
* Using the Cross-Chain Bridge Users can transfer their Tokens between Polygon and Ethereum
* The Polygon Bridge brings a Scaling Solution that is nearly no Costs and wide flexible
* Polygon Tokens (MATIC) are backed by Ethereum Tokens (ETH) - there is a One-to-One Ratio

|              | PoS Bridge                                                                                   | Plasma Bridge                                                                                 |
|--------------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Description  | PoSBridge is looking for Flexibility and faster Withdrawals with the PoS Consensus Mechanism | Plasma Bridge is looking for increased Security guarantees by with Plasma Consensus Mechanism |
| Security     | PoS Bridge is secured by a robust Set of external Validators                                 | Plasma Bridge is secured by the Ethereum's Security with a 7 Days Challenge Period            |

### Polygon Architecture

The Polygon Architecture consist of three Layer:

1) Staking Contracts and Plasma Contracts are deployed on Ethereum
1) Proof-of-Stake Layer (Heimdall) aggregates the Blocks (as a Merkle Tree) that are produced from the Bor (MATIC Side Chain) and provide them (the Root of the Merkle Tree) to the Main Chain (Ethereum)
1) Block Producer Layer (Bor) is a Side Chain (Polygon / MATIC Blockchain) to aggregate Transactions

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/141675718-8b55c317-a0c5-4f77-b224-0f60a17b401f.png" alt="Polygon Architecture" width="100%"/>
</P>

1) Block Producers are chosen, with (2 / 3 + 1) of Block Producers the Majority is reached (Consensus)

2) At regular Intervals, the Root of the Merkle Tree of generated Blocks must be verified by the Set of Nodes (Checkpoints - PoS)

3) The Verifier (PoS) is then chosen to collect the Signatures of the Merkle Roots from the Checkpoints and publish them to the Ethereum Main Chain

* Only the Merkel Root (from the Merkle Tree) of the Plasma Checkpoint Nodes (PoS) is stored in the Root Chain (Ethereum)

* The Checkpoint has an Interval of 5 Minutes, these means, each 5 Minutes the Blocks are validated

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/141695437-c6c0a712-4b5d-4a32-b962-e3c952bcdad1.png" alt="Polygon Architecture" width="75%"/>
</P>

* The Smart Contracts that are deployed on Ethereum handle the State Management of the Checkpoint Nodes (Heimdall)

* The Checkpoint Nodes handle State Management of the Polygon / MATIC Side Chain - this PoS Layer do Snapshots at a fixed Internal of the Polygon / Matic Side Chain and save it on the Ethereum Chain  

* The Proof-of-Stake Layer (Heimdall):
  * validates all the Blocks since the last Checkpoint,
  * creates a Merkle tree of the Block hashes and
  * publishes the Merkle Root to the Main Ethereum Chain

* The Gasprice of a Transaction is measured in GWEI in the Polygon Network

## Types of Transactions

* Transfer of Funds between EOAs (Externally-owned Accounts)
* Deployment of Smart Contracts
* Contract Interaction to execute Functions on deployed Smart Contracts

## Asset Flow in Plasma Bridge

1) An Asset (like Ether) is deposited into the Plasma Side Chain
2) The deposited Assets are reflected in the Plasma Side Chain and can be there be used with lower Fees and higher Transaction Throughput
3) After the Use of the Polygon Network the remaining (deposited) Assets can be withdrawn from the Plasma Side Chain 
4) Once the Checkpoint is submitted to the Ethereum Smart Contract, an Exit-NFT Token is created of equivalent Value of the remaining Assets
5) The User has to wait 7 Days until his Assets can be claimed back into the Ethereum Mainnet

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147771110-9eb84b08-512d-4a26-9a3b-5a7fe236f380.png" alt="Asset-Flow-in-Plasma-Bridge" width="100%"/>
</P>

### PoS Bridge Deposit

* The Predicate Contract on Ethereum is the Spender Contract which will issue the Polygon Assets in Return of other Assets (like Ether) and also locks these others Assets
  * This means, that the Tokens that leave the Ethereum Network are locked and the same Number of Tokens are minted on Polygon as a pegged Token and
  * to move the Tokens back to the Ethereum Network, the locked Tokens on Ethereum Network are unlocked and their Counterpart on Polygon is burned and
  * the Proof of Burn is submitted to the Ethereum Chain
* The next Step is to deposit the Asset by calling the RootChainManager Contract which will trigger the ChildChainManager Contract on the Polygon Network - this happens through a State-Sync-Mechanism
* The ChildChainManager will call the `deposit` Function on the Child Token (Polygon Asset) and mint the corresponding Amount of Polygon Assets to the User's Account

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/141675807-0725bd7d-0817-447d-9336-5a60672d22b6.png" alt="POS Bridge Deposit" width="100%"/>
</P>

### PoS Bridge Withdraw

* The Withdrawing of Polygon Assets back to Ethereum will burn that Assets on Polygon
* The Proof of the Burn-Transaction has to be submitted on the Ethereum Network to release the deposited Ether
* It will take up to three hours for the Checkpoint to validate the Burn-Transaction which done by the PoS Validators (Heimdall)
* Once the Burn-Transaction si submitted to the Checkpoint then a Proof of the Burn-Transaction will be submitted to the RootChainManager Contract on Ethereum by calling the `exit` Function
* The `exit` Function Call will verify the Checkpoint Inclusion and will trigger the Predication Contract that hold the initial deposited Asset (like Ether) to release these Assets and refund them to the User's Account on Ethereum

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/141675795-f05a396a-ba84-4726-b4b6-32435f745476.png" alt="POS Bridge Withdraw" width="100%"/>
</P>

### PoS ETH Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837634-054df71d-b1e2-4ce5-938b-d4804621ba88.png" alt="PoS-ETH-Flow" width="85%"/>
</P>

### PoS ERC20 Deposit Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837688-d30127e2-a949-49fa-bda4-9681f9c4b331.png" alt="PoS-ERC20-Deposit-Flow" width="85%"/>
</P>

### PoS ERC20 Withdraw Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837715-dd24b309-5776-4b79-be08-3b5458a3182a.png" alt="PoS-ERC20-Withdraw-Flow" width="85%"/>
</P>

### PoS ERC721 Deposit Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837737-644668ba-4d7d-4e60-8ba4-0b8e8ae9a397.png" alt="PoS-ERC721-Deposit-Flow" width="85%"/>
</P>

### PoS ERC721 Withdraw Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837796-0ab99d5e-2030-4de0-af07-14011bf6ed63.png" alt="PoS-ERC721-Withdraw-Flow" width="85%"/>
</P>

### PoS ERC1155 Deposit Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837895-e4ba08c2-6a15-4ac2-b33f-4f0c95a3b56e.png" alt="PoS-ERC1155-Deposit-Flow" width="85%"/>
</P>

### PoS ERC1155 Withdraw Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837943-db0748ed-023f-49b0-82ea-d5721ec6b4d7.png" alt="PoS-ERC1155-Withdraw-Flow" width="85%"/>
</P>

### Plasma ETH Deposit Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147837976-b9f71600-b874-4b6c-aa5f-cc93a8a5d185.png" alt="Plasma-ETH-Deposit-Flow" width="85%"/>
</P>

### Plasma ETH Withdraw Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147838002-7a0b2701-dbd5-4455-afc8-e5bfa46b34b5.png" alt="Plasma-ETH-Withdraw-Flow" width="85%"/>
</P>

### Plasma ETH Transfer Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147838076-2d53da41-590a-4843-a8fd-de6590f6b554.png" alt="Plasma-ETH-Transfer-Flow" width="85%"/>
</P>

### Plasma ERC20 Transfer Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147838109-d949f4bd-5ec7-4944-aa83-f5e99268b640.png" alt="Plasma-ERC20-Transfer-Flow" width="85%"/>
</P>

### Plasma ERC721 Deposit Flow

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147838155-c5327d0a-e999-4ddd-aa53-dd19b11e0392.png" alt="Plasma-ERC721-Deposit-Flow" width="85%"/>
</P>

## Polygon SDK (maticnetwork/matic.js)

* __MaticPlasmaClient__ allows interacting with the Smart Contracts on the Plasma Chain
* __MaticPoSClient__ allows interacting with the Smart Contracts on the PoS Layer

### Initialization of the Plasma Client

* __parentProvider__: A Provider allows interacting with a Blockchain therefore a `parentProvider` will be an EVM-based Chain Provider (like Goërli)
* __maticProvider__ will be a Mumbai Provider (Testnet)
* __parentDefaultOptions__ specifies who is passing the Transactions

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147823869-81a6c9a4-35df-4cb6-8ed0-10ddb2a6eef8.png" alt="MaticPlasmaClient-Constructor" width="50%"/>
</P>

### Initialization of the PoS Client

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/147824288-71f70048-43ad-4890-bac0-a076ab77c5b5.png" alt="MaticPoSClient-Constructor" width="50%"/>
</P>


