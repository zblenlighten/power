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
  - Peer-to-peer network
  - Gossip protocol
  - Nodes: light client, full node, mining
  - Public-key cryptography

- Openness: transparency

- Uses
  - Cryptocurrencies
    - Bitcoin (Satoshi Nakamoto)
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
    - Endorser, committer, Ledger, KVS, Gossip
  - Ordering Service Nodes (OSN): collectively form the ordering service

- Transaction flow
  - Execution phase
  - Ordering phase
  - Validation phase

- Fabric components
  - Communication: gRPC
  - Membership service provider (MSP)
    - Certification authorities (CAs)
  - Ordering service: channels
    - solo, kafka
  - Peer Gossip
  - Ledger: block store, peer transaction manager (PTM)
    - world state (database of current values)
    - blockchain (transaction log, immutable)
  - Chaincode Execution: Go, Java, Node.js...
  - Configuration and System Chaincodes
