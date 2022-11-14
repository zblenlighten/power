# Knowledge Memo

## Contents

- [Knowledge](#knowledge)
- [Web3](#web3)
- [Hyperledger Fabric](#hyperledger-fabric-consortium-blockchain)

## Blockchain

### Knowledge

- Blockchain
  - Blocks cryptographically linked together ([demo](https://tools.superdatascience.com/blockchain/blockchain))
    - Immutable ledger: Merkle tree -> Hash cryptography
    - A block stores multiple transactions
  - Decentralization (centralized example: client-server model)
    - Distributed peer-to-peer network (nodes: light client, full node, miner node)
    - Best-effort delivery (vs: reliable delivery)
  - Mining
    - Finding the golden nonce which will generate a hash value below a certain target (bits)
    - Hardware: CPU ( < 10 MH/s), GPU ( < 1 GH/s), ASIC ( > 1000 GH/s)
    - Mining Pool, Mempool, Orphan Block, 51% Attack
  - Fork
    - Accidental fork
    - Intentional fork
      - Hard fork: not backwards compatible, resulting in permanent splits of the blockchain
        - Ethereum (DAO attack): Ethereum (ETH) and Ethereum Classic (ETC)
        - Bitcoin (SegWit): Bitcoin (BTC) and Bitcoin Cash (BCH)
      - Soft fork: new rules are a subgroup of old rules, a temporary divergence
  - Openness: transparency

- Consensus Protocol
  - Byzantine Fault
  - Challenges: Attackers, Competing chains
  - Cryptographic puzzles (hard to solve & easy to verify)
    - Verify the legitimacy of a transaction, ensure all participating nodes come to an agreement about the true and valid state of the network, avoid double-spending
    - Create new digital currencies by rewarding miners
  - Proof of Work (Bitcoin mining: Hashcash)
    - Transactions are bundled together into a block
    - Miners verify transactions within each block are legitimate
    - Miners solve proof-of-work problem (inverse hashing) by computational resources
    - A cryptocurrency prize provided by the protocol (reward) is given to the first miner who solves each blocks problem
    - Verified transactions are stored in the public blockchain
  - Proof of Stake
    - Validators take turns proposing and voting on the next block
    - The weight of each validator's vote depends on the size of its deposit (i.e. stake)
    - Energy efficiency, security and reduced risk of centralization
  - Proof of Burn
    - The more coins burned by the miner, the bigger the ensuing virtual mining rig

- Cryptocurrency: technology - protocol - [token]((https://www.investopedia.com/terms/c/crypto-token.asp))
  - Bitcoin -> SHA-256
    - [Bitcoin Core](https://bitcoin.org/en/bitcoin-core/)
    - Monetary policy: halving principle, block time
    - [Bitcoin scalability problem](https://en.wikipedia.org/wiki/Bitcoin_scalability_problem)
    - Bitcoin Improvement Proposals (BIPs)
      - BIP32: seed -> key pairs
        - master private key -> private key -> public key -> address
        - master public key (recreate public key to auditor or someone who doesn't send money)
      - BIP39: mnemonic code
      - BIP44: coin type - account - change - address_index
  - Ethereum -> Keccak 256 (Ether)
    - Accounts
      - Externally owned account (EOA, has no associated code, controlled by private keys -> Elliptic Curve Cryptography (ECC))
      - Contract account (has associated code)
    - Smart contract is a program / code that runs on the blockchain
    - Ethereum virtual machine: [Gas](https://ethereum.org/en/developers/docs/gas/)
    - ERC-20 (e.g. SHIB)
  - Initial coin offering (ICO, e.g. KodakCoin)
  - Exchange-traded fund (ETF)
  - [Market](https://coinmarketcap.com/)

- Transaction
  - Blockchain trilemma: Decentralization, Security, Scalability
  - Blockchain type: Public, Private, Consortium
    - [Dune Analytics](https://dune.com/browse/dashboards)
    - Explorer
      - [Blockchain.com Explorer](https://www.blockchain.com/explorer)
      - [Blockchair](https://blockchair.com/)
  - Unspent Transaction Output (UTXO)
  - Signatures ([demo](https://tools.superdatascience.com/blockchain/public-private-keys/signatures))
    - private key (send money) -> public key (verification function) -> address (for additional security, receive money)
  - Latency and Throughput
    - SegWit
    - Layer 2 Scaling
      - Bitcoin Lightning Network
      - Ethereum Plasma
  - Hierarchical Deterministic (HD) Wallet

### Web3

- Principles: decentralized, permissionless, native payments, trustless

- Decentralized autonomous organization (DAO)
  - [daolist](https://daolist.fyi/)

- Decentralized finance (DeFi)
  - MakerDAO (DAI)
  - Compound Finance
  - Aave
  - Uniswap
    - Automated Market Maker (AMM)
  - Harvest Finance (FARM)
  - Stablecoins
  - Non-fungible token (NFT)
    - InterPlanetary File System (IPFS)
      - [Decentralizing NFT metadata on OpenSea](https://opensea.io/blog/announcements/decentralizing-nft-metadata-on-opensea/)
  - References
    - [defipulse](https://www.defipulse.com/)

- Applications
  - GameFi
    - CryptoKitties
    - Axie Infinity: Axie Infinity Shards (AXS) and Smooth Love Potions (SLP)
    - Alien Worlds: Trilium (TLM)
  - SocialFi
  - Metaverse
  - X to Earn
  - Creator Economy
    - mirror.xyz
    - audius.co

### Hyperledger Fabric (Consortium blockchain)

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
    - Private & permissioned
  - Ordering service: channels
    - solo, Kafka
  - Peer gossip
    - The communication layer for gossip is based on gRPC and utilizes TLS with mutual authentication
  - Ledger: block store, peer transaction manager (PTM)
    - world state (Key-Value Store of current values): Merkle Patricia tries (Radix tree)
    - blockchain (transaction log, immutable)
  - Chaincode (execution of smart contracts): Go, Java and Node.js
    - Channel: indentify each of the chaincode in the network
    - Shim API
    - Interface
    - Stub
  - Configuration and system chaincodes
