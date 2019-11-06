# Knowledge Memo

## Contents

- [Knowledge](#knowledge)
- [Hyperledger Fabric](#hyperledger-fabric)

## Blockchain

### Knowledge

- Block
  - Cryptographic hash
  - Trusted timestamping
  - Transaction data (Merkle tree / hash tree): immutable

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
    - world state (Key-Value Store of current values)
    - blockchain (transaction log, immutable)
  - Chaincode execution: Go, Java, Node.js...
  - Configuration and system chaincodes
