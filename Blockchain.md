# Knowledge Memo

## Contents

- [Knowledge](#knowledge)
- [Hyperledger Fabric](#hyperledger-fabric)

## Blockchain

### Knowledge

- Block
  - Cryptographic hash
  - Trusted timestamping
  - Transaction data (immutable): Merkle tree / hash tree

- Decentralization (centralized example: client-server model)
  - Peer-to-peer network (nodes: light client, full node, mining)
  - Best-effort delivery (contrast: reliable delivery)
  - Public-key cryptography

- Openness: transparency

- Uses
  - Cryptocurrencies
    - Bitcoin ([Bitcoin scalability problem](https://en.wikipedia.org/wiki/Bitcoin_scalability_problem))
    - Ethereum
  - Smart contracts
  - Financial services

- Consensus (ensure all participating nodes come to an agreement about the true and valid state of the network)
  - Purposes
    - Verify the legitimacy of a transaction, avoid double-spending
    - Create new digital currencies by rewarding miners
  - Proof of work (Bitcoin mining: Hashcash)
    - Transactions are bundled together into a block
    - Miners verify transactions within each block are legitimate
    - Miners solve proof-of-work problem: inverse hashing (by computational resources)
    - A cryptocurrency prize provided by the protocol (reward) is given to the first miner who solves each blocks problem
    - Verified transactions are stored in the public blockchain
  - Proof of stake
    - Validators take turns proposing and voting on the next block
    - The weight of each validator's vote depends on the size of its deposit (i.e. stake)
    - Energy efficiency, security and reduced risk of centralization
  - Proof of burn
    - The more coins burned by the miner, the bigger the ensuing virtual mining rig

### Hyperledger Fabric

- Private & permissioned

- Distributed application of Fabric
  - Smart contract: chaincode
  - Endorsement policy

- Nodes
  - Clients: submit transaction proposals for execution
  - Peers: execute transaction proposals and validate transactions
    - Endorser
    - Committer
  - Ordering Service Nodes (OSN): collectively form the ordering service
  - Pruned nodes: remove non-critical information from local storage to have a lighter footprint

- Transaction flow
  - Execution phase
  - Ordering phase
  - Validation phase

- Fabric components
  - Membership service provider (MSP)
    - Certification authorities (CAs)
  - Ordering service: channels
    - solo, kafka
  - Peer gossip
    - The communication layer for gossip is based on gRPC and utilizes TLS with mutual authentication
  - Ledger: block store, peer transaction manager (PTM)
    - world state (Key-Value Store of current values): Merkle Patricia tries (Radix tree)
    - blockchain (transaction log, immutable)
  - Chaincode execution: Go, Java, Node.js...
  - Configuration and system chaincodes
