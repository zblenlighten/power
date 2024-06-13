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
  - History
    1. Hash function: one-way
    2. Public-key cryptography: one-way but can be reversed with private key
    3. Digital signature: prove who encrypted
    4. Blockchain
      - Mine a new block (verified by Bitcoin network) and plus a new nonce
      - A single history of the order of transactions
    5. Distributed computer: Ethereum Virtual Machine and smart contracts -> DApps
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
    - [NiceHash](https://www.nicehash.com/support/mining-help/nicehash-os/what-is-nicehash-os)
  - Fork
    - Accidental fork
    - Intentional fork
      - Hard fork: not backwards compatible, resulting in permanent splits of the blockchain
        - Ethereum (DAO attack): Ethereum (ETH) and Ethereum Classic (ETC)
        - Bitcoin (SegWit): Bitcoin (BTC) and Bitcoin Cash (BCH)
      - Soft fork: new rules are a subgroup of old rules, a temporary divergence
  - Blockchain trilemma: Decentralization, Security, Scalability
    - Bitcoin and Ethereum chose decentralization and security, which makes them fairly slow
  - Blockchain types: Public, Private, Consortium

- Consensus Protocol
  - Byzantine Fault
  - Challenges: Attackers, Competing chains
  - Cryptographic puzzles (hard to solve & easy to verify)
    - Verify the legitimacy of a transaction, ensure all participating nodes come to an agreement about the true and valid state of the network, avoid double-spending
    - Create new digital currencies by rewarding miners
  - Proof of Work (PoW: mine blocks)
    - Transactions are bundled together into a block
    - Miners verify transactions within each block are legitimate
    - Miners solve proof-of-work problem (inverse hashing) by computational resources
    - A cryptocurrency prize provided by the protocol (reward) is given to the first miner who solves each blocks problem
    - Verified transactions are stored in the public blockchain
  - Proof of Stake (PoS: validate blocks)
    - Validators take turns proposing and voting on the next block
    - The weight of each validator's vote depends on the size of its deposit (i.e. stake)
    - Energy efficiency, security and reduced risk of centralization
  - Proof of Burn
    - The more coins burned by the miner, the bigger the ensuing virtual mining rig

- Cryptocurrency
  - Layer 1 blockchains
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
      - Ethereum Virtual Machine (EVM): Staking, [Gas](https://ethereum.org/en/developers/docs/gas/), [Tokens](https://www.investopedia.com/terms/c/crypto-token.asp)
        - Standards: ERC-20 (fungible) vs ERC-721 (nonfungible, tokenId)
      - Smart Contract is a program / code that runs on the blockchain
        - Internal Transactions
        - Blockchain Oracle
      - Accounts
        - Externally owned account (EOA, has no associated code, controlled by private keys -> Elliptic Curve Cryptography (ECC))
        - Contract account (has associated code)
        - Ethereum Name Service (ENS)
      - Development tools
        - Tenderly
        - Truffle
        - Hardhat
    - BNB Chain
    - Solana
    - Avalanche
  - Layer 2 blockchains (off main chain)
    - Polygon
    - Bitcoin Lightning Network
    - Ethereum Plasma
    - Ethereum Optimism
  - Others
    - Trustless and Censorship resistance
    - Exchange-traded fund (ETF)
    - [Stablecoin](https://academy.binance.com/en/glossary/stablecoin): collateralized - algorithmic
      - Death spiral: TerraUSD / Luna
    - Tokenomics
      - Initial coin offering (ICO, e.g. KodakCoin)
      - Initial dex offering (IDO)
    - [Crypto Airdrop](https://academy.binance.com/en/articles/what-is-a-crypto-airdrop)
    - [Crypto Tax Guide](https://coinledger.io/crypto-taxes)

- Transaction
  - Unspent Transaction Output (UTXO)
  - Signatures ([demo](https://tools.superdatascience.com/blockchain/public-private-keys/signatures))
    - private key (send money) -> public key (verification function) -> address (for additional security, receive money)
  - [Crypto Wallets vs Exchanges](https://www.coingecko.com/learn/crypto-wallet-vs-exchange)
    - Hierarchical Deterministic (HD) Wallet
    - Multi-party computation (MPC) Wallet
    - Decentralized Exchange (DEX)
      - Automated Market Maker (AMM)
    - Fiat off-ramp
  - [Bridge](https://academy.binance.com/en/articles/what-s-a-blockchain-bridge)
    - [Cross-Chain Interoperability](https://chain.link/education-hub/blockchain-interoperability)
  - Crypto scam / fraud

### Web3

- Crypto data and analytics
  - Chainalysis
  - Coin Metrics
  - [The Graph](https://github.com/graphprotocol/graph-node)
  - [Dune Analytics](https://dune.com/browse/dashboards) ([tutorial](https://github.com/SixdegreeLab/MasteringChainAnalytics))
  - Messari
  - Others: [DefiLlama](https://defillama.com/), [Glassnode](https://studio.glassnode.com/), [Nansen](https://pro.nansen.ai/), Chainlink
  - References
    - [Blockchain.com Explorer](https://www.blockchain.com/explorer)
    - [Ethereum Charts & Statistics](https://etherscan.io/charts)
    - [Key Metrics for the Rapidly Expanding Web3 Ecosystem](https://blog.chain.link/web3-metrics/)

- Decentralized finance (DeFi)
  - Tokens and tokenomics
    - [In Praise of Ponzis](https://www.drorpoleg.com/content/images/size/w1600/2022/10/Screen-Shot-2022-10-25-at-1.32.11-PM.png)
    - Total value locked (TVL)
  - AMM
    - History
      - Central limit order book
      - Market maker
    - Liquidity pool: provide liquidity in the form of asset pairs / market maker in some currency pairs
      - Risk: adverse selection / impermanent loss
    - Staking: lock up cryptocurrency in a smart contract to support the network's operation and security
    - Yield Farming: fees generated by trades in the liquidity pool, newly minted tokens, or a combination of both
      - Annual percentage yield (APY)
  - Lending protocol
  - Maximal Extractable Value (MEV): gas auction
  - Protocols: Uniswap, Aave, Compound, and MakerDAO (DAI)
  - NFT
    - [Decentralizing NFT metadata on OpenSea](https://opensea.io/blog/announcements/decentralizing-nft-metadata-on-opensea/)
  - Regulatory compliance: [Zero Hash](https://blog.zerohash.com/)
  - Decentralized autonomous organization (DAO)

- Applications
  - KYC: [Crypto KYC Guide](https://sumsub.com/blog/crypto-kyc-guide/) - [What Is a KYC Analyst](https://sumsub.com/blog/kyc-analyst/)
  - Decentralized storage
    - InterPlanetary File System (IPFS)
    - Filecoin
  - Blockchain node services
  - DApp
    - [Alchemy](https://github.com/alchemyplatform/create-web3-dapp)
    - [thirdweb](https://portal.thirdweb.com/)
    - Moralis
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
  - Others
    - Helium
    - [Decentralised Privacy](https://www.tookitaki.com/glossary/tornado-cash)

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
