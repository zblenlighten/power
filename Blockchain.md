# Knowledge Memo

## Blogs

- [Mirror's web3 publishing community](https://dao.mirror.xyz/collection)

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
  - Blockchain trilemma: Decentralization, Security, Scalability

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

- Cryptocurrency: technology - protocol - [token](https://www.investopedia.com/terms/c/crypto-token.asp)
  - Layer 1 (main chain network, scalability problem)
    - [Bitcoin](https://bitcoin.org/bitcoin.pdf) -> SHA-256
      - [Bitcoin Core](https://bitcoin.org/en/bitcoin-core/)
      - Monetary policy: halving principle, block time
      - [Bitcoin scalability problem](https://en.wikipedia.org/wiki/Bitcoin_scalability_problem)
      - Bitcoin Improvement Proposals (BIPs)
        - BIP32: seed -> key pairs
          - master private key -> private key -> public key -> address
          - master public key (recreate public key to auditor or someone who doesn't send money)
        - BIP39: mnemonic code / secret recovery phrase (SRP) ([converter](https://iancoleman.io/bip39/))
        - BIP44: coin type - account - change - address_index
        - [Bitcoin Core file system](https://github.com/bitcoin/bitcoin/blob/master/doc/files.md)
    - Ethereum -> Keccak 256 (Ether)
      - Accounts
        - Externally owned account (EOA, has no associated code, controlled by private keys -> Elliptic Curve Cryptography (ECC))
        - Contract account (has associated code)
      - Smart contract is a program / code that runs on the blockchain
        - Internal Transactions
        - Blockchain Oracle
      - Ethereum Virtual Machine: [Gas](https://ethereum.org/en/developers/docs/gas/)
      - ERC-20 Token Standard
      - Development tools
        - Tenderly
        - Truffle
        - Hardhat
    - BNB Chain
    - Solana
  - Layer 2 (off chain)
    - Polygon
    - Bitcoin Lightning Network
    - Ethereum Plasma
    - Ethereum Optimism
  - Others
    - Initial coin offering (ICO, e.g. KodakCoin) - Initial dex offering (IDO)
    - [Crypto Airdrop](https://academy.binance.com/en/articles/what-is-a-crypto-airdrop)
    - Exchange-traded fund (ETF)
    - [Crypto Tax Guide](https://coinledger.io/crypto-taxes)

- Transaction
  - Blockchain type: Public, Private, Consortium
  - Unspent Transaction Output (UTXO)
  - Signatures ([demo](https://tools.superdatascience.com/blockchain/public-private-keys/signatures))
    - private key (send money) -> public key (verification function) -> address (for additional security, receive money)
  - Types of crypto fraud
    - Payments fraud: stolen card monetization
    - Scams: investment and social engineering scams
    - Friendly fraud
    - Off-ramping fraud
  - [Crypto Wallets vs Exchanges](https://www.coingecko.com/learn/crypto-wallet-vs-exchange)
    - Hierarchical Deterministic (HD) Wallet
    - Multi-party computation (MPC) Wallet
    - Decentralized Exchange (DEX)
      - Automated Market Maker (AMM)
  - [Cross-Chain Interoperability](https://chain.link/education-hub/blockchain-interoperability)
    - [Blockchain Bridge](https://academy.binance.com/en/articles/what-s-a-blockchain-bridge)

### Web3

- Principles: decentralized, permissionless, native payments, trustless

- Crypto data and analytics
  - Chainalysis
  - Coin Metrics
  - [The Graph](https://github.com/graphprotocol/graph-node)
  - [Dune Analytics](https://dune.com/browse/dashboards)
  - Messari
  - Others: [DefiLlama](https://defillama.com/), [Glassnode](https://studio.glassnode.com/), [Nansen](https://pro.nansen.ai/), Chainlink
  - References
    - [Blockchain.com Explorer](https://www.blockchain.com/explorer)
    - [Ethereum Charts & Statistics](https://etherscan.io/charts)
    - [Key Metrics for the Rapidly Expanding Web3 Ecosystem](https://blog.chain.link/web3-metrics/)

- Decentralized autonomous organization (DAO)

- Decentralized finance (DeFi)
  - Non-fungible token (NFT)
    - [Decentralizing NFT metadata on OpenSea](https://opensea.io/blog/announcements/decentralizing-nft-metadata-on-opensea/)
  - AMM
    - Liquidity: allow users to trade assets
    - Yield Farming: fees come from the trading activity that takes place on exchange or marketplace that uses liquidity pool
      - Annual percentage yield (APY)
  - Maximal Extractable Value (MEV)
  - Protocols: Uniswap, Aave, Compound, and MakerDAO (DAI)
  - Regulatory compliance: Zero Hash
  - [Stablecoin](https://academy.binance.com/en/glossary/stablecoin)

- Applications
  - [How to pass KYC (Know Your Customer)](https://sumsub.com/how-to-pass-verification/)
  - [Zero Hash](https://blog.zerohash.com/)
  - Decentralized storage
    - InterPlanetary File System (IPFS)
    - Filecoin
  - Blockchain node services
  - DApp
    - [Alchemy](https://github.com/alchemyplatform/create-web3-dapp)
    - Moralis
    - MetaMask
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
