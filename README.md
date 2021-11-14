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
* The Tree structure facilitates Verification within the Trees of Chains, thus increasing the Efficiency of the Network
* Each Plasma Chain is a customizable Smart Contract and can Function in a unique Way to meet different Needs
* __Plasma Sharding__ is used to separate the entire Blockchain into smaller, independent Parts (__Shards__), thus increasing the Efficiency of the Blockchain
* Shards no longer need to check all Blocks to confirm their Transactions, but only the Blocks of the individual Shards - this allows individual Nodes to process their Transactions faster
* __Fraud Proof__ allows Plasma Chains to submit a Complaint to their Parent Chain - this may be the Case if the Plasma Chains cannot agree on a Consensus

## Polygon's hybrid Security Model (Proof-of-Stake and Plasma)

* Polygon uses a dual Consensus Mechanism - a Combination of Plasma and PoS that optimizes the Speed and Decentralization of the Polygon Network
* Polygon brings a trust-less two-way Transaction Chanel between Polygon and Ethereum by introducing a Cross-Chain Bridge with Plasma Bridge and PoS Bridge
* Using the Cross-Chain Bridge Users can transfer their Tokens between Polygon
* The Polygon Bridge brings a Scaling Solution that is nearly no Costs and wide flexible
* Polygon Tokens (MATIC) are backed by Ethereum Tokens (ETH) - there is a One-to-One Ratio

| |PoS Bridge|Plasma Bridge|
|---|---|---|
|Description|PoSBridge is looking for Flexibility and faster Withdrawals with the PoS Consensus Mechanism|Plasma Bridge is looking for increased Security guarantees by with Plasma Consensus Mechanism|
|Security|PoS Bridge is secured by a robust Set of external Validators|Plasma Bridge is secured by the Ethereum's Security with a 7 Days Challenge Period|

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

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/141695437-c6c0a712-4b5d-4a32-b962-e3c952bcdad1.png" alt="Polygon Architecture" width="75%"/>
</P>

* The Smart Contracts that are deployed on Ethereum handle the State Management of the Checkpoint Nodes (Heimdall)

* The Checkpoint Nodes handle State Management of the Polygon / MATIC Side Chain - this PoS Layer do Snapshots at a fixed Internal of the Polygon / Matic Side Chain and save it on the Ethereum Chain  

## PoS Bridge Deposit

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/141675807-0725bd7d-0817-447d-9336-5a60672d22b6.png" alt="POS Bridge Deposit" width="100%"/>
</P>

## PoS Bridge Withdraw

<p align="center">
    <img src="https://user-images.githubusercontent.com/29623199/141675795-f05a396a-ba84-4726-b4b6-32435f745476.png" alt="POS Bridge Withdraw" width="100%"/>
</P>

## Types of Transactions

* Transfer of Funds between EOAs (Externally-owned Accounts)
* Deployment of Smart Contracts
* Contract Interaction to execute Functions on deployed Smart Contracts

## Polygon Blockchain Explorer

## Polygon Gas Station