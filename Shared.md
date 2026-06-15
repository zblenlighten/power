# Shared Knowledge

Cross-cutting topics referenced by multiple knowledge files.

## Contents

- [Security & Cryptography](#security--cryptography)
- [Distributed Systems](#distributed-systems)
- [Communication Patterns](#communication-patterns)

## Security & Cryptography

### Cryptography

- Cryptographic hash function
  - MD5 (rainbow table) - bcrypt (salt) - Secure Hash Algorithm (SHA)
  - Hash function: one-way, easy to compute, even distribution, less collision
  - Requirements: One-way, Deterministic, Fast computation, [Avalanche effect](https://en.wikipedia.org/wiki/Avalanche_effect), Must withstand collisions
    - [Collision](http://www.ruanyifeng.com/blog/2018/09/hash-collision-and-birthday-attack.html): Separate chaining, Open addressing, 2-choice hashing ([Perfect hash function](https://en.wikipedia.org/wiki/Perfect_hash_function))
- MAC functions: Hash-based message authentication code (HMAC)
- Symmetric-key algorithm
  - AES256 (symmetric, faster)
- Public-key cryptography: one-way but can be reversed with private key
  - Integer factorization: RSA, Rabin
  - Discrete logarithm: ElGamal
  - Elliptic Curve Cryptography (ECC)
  - Digital signature (Electronic signature: DocuSign): prove who encrypted
  - Public key infrastructure (PKI)
    - Certificate authority (CA)
- Advanced cryptography
  - Zero-knowledge proof
  - Post-quantum cryptography

### Identity and Access Management (IAM)

- Basic topics: [Intro to IAM](https://auth0.com/intro-to-iam/), [What is IAM](https://www.cloudflare.com/learning/access-management/what-is-identity-and-access-management/)
- Authentication (AuthN: who you are)
  - Basic authentication & Digest authentication
  - Login form, HTTP authentication
  - Key management (cryptographic keys)
  - Secure Authentication (e.g. Multi Factor Authentication, MFA)
- Authorization (AuthZ: what you can do)
  - Role-based access control (RBAC)
  - Attribute-based access control (ABAC/PBAC)
  - Centralized vs Decentralized
  - URL access controls
  - Access control list (ACL)
    - Filesystem ACL
    - Network ACL
    - SQL ACL
  - Privileged Access Management (PAM)
- [Identity Brokering](https://docs.redhat.com/en/documentation/red_hat_single_sign-on/7.1/html/server_administration_guide/identity_broker#identity_broker_overview) vs User Federation
- System for Cross-domain Identity Management (SCIM)
- [Zero trust](https://cloud.google.com/learn/what-is-zero-trust)

### Security Protocols

- Central Authentication Service (CAS): single sign-on (SSO)
- [OAuth 2.0](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html)
  - OpenID Connect (OIDC)
  - Token Formats: [JSON Web Token](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html) (JWT)
  - Token delegation
    - On-Behalf-Of (OBO) flow (Microsoft Entra ID specific)
    - Token Exchange (standard, cross-platform)
- SAML 2.0 (Security Assertion Markup Language)
- Kerberos

### Secure Communication

- SSH
- [SSL/TLS](http://www.ruanyifeng.com/blog/2014/09/illustration-ssl.html)
  - Data in transit: TLS encrypts data between server and client (asymmetric)
  - OpenSSL
  - Network security services (NSS)
- Virtual Private Network (VPN)
  - [VPN error code](https://www.paessler.com/help/vpn-errors)

### Application Security

- Principle of least privilege (PoLP)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Web Application Security Checklist](https://www.appsecmonkey.com/blog/web-application-security-checklist)
- Encryption Options (e.g. Customer Managed Key, CMK)
- Encryption (data at rest & data in transit), Data masking, Data erasure
- Data loss prevention (DLP)
- Vault (Secrets Management)
  - Data in transit: TLS encrypts data between server and client (asymmetric)
  - Internal data: AES256 (symmetric, faster)
  - Key sharding: the master key is split into several unseal keys using Shamir's Secret Sharing (two-man rule)
  - Authentication: data that must be kept confidential is a secret, access to secret is performed by token
    - wrap-ttl: generate a wrapping token
  - Policy (Authorization): policy is associated to tokens and grants capabilities to a secrets engine path
  - AppRole: Jenkins

## Distributed Systems

### Consensus

- Fault-tolerant Consensus: for solving consensus in a network
  - Properties: uniform agreement, integrity, validity, termination
  - Consensus algorithms: Paxos, Raft, Zab (ZooKeeper)
- Byzantine Fault
  - Challenges: Attackers, Competing chains
  - Cryptographic puzzles (hard to solve & easy to verify)
- Proof of Work (PoW: mine blocks)
  - Transactions are bundled together into a block
  - Miners verify transactions within each block are legitimate
  - Miners solve proof-of-work problem (inverse hashing) by computational resources
  - A cryptocurrency prize provided by the protocol (reward) is given to the first miner who solves each block's problem
  - Verified transactions are stored in the public blockchain
- Proof of Stake (PoS: validate blocks)
  - Validators take turns proposing and voting on the next block
  - The weight of each validator's vote depends on the size of its deposit (i.e. stake)
  - Energy efficiency, security and reduced risk of centralization
- Proof of Burn
  - The more coins burned by the miner, the bigger the ensuing virtual mining rig

### Peer-to-peer Networks

- Network model: client-server vs peer-to-peer
- Distributed peer-to-peer network
  - Peer-to-peer file sharing: BitTorrent
  - Blockchain nodes: light client, full node, miner node
- Best-effort delivery (vs: reliable delivery)

### Key Technologies

- [ZooKeeper](https://zookeeper.apache.org/doc/current/zookeeperInternals.html) (vs: Chubby)
  - Features: linearizable atomic operations, total ordering operations, failure detection, change notifications
  - Central coordinator: manage state and hold configuration (ZooKeeper ensemble)
  - Recover from partial failures: master crashes, worker crashes, network trouble
  - Service discovery: leader election
  - Membership / coordination service
- Merkle tree
  - Data structure: identify inconsistencies between nodes
  - Blockchain: immutable ledger via hash cryptography
- InterPlanetary File System (IPFS)
  - Distributed File System
  - Decentralized storage (blockchain)
- Consistent hashing
  - Load balancing ([reference](https://www.toptal.com/big-data/consistent-hashing))
  - Distributed cache: each node owns part of cached data
- GeoHash (location based service)
  - Multi-column index: Geohash, R tree

## Communication Patterns

### Messaging Patterns

- Synchronous
  - REST
  - RPC
    - Remote procedure call
    - Thrift & Avro
    - [gRPC](https://github.com/grpc-ecosystem/awesome-grpc): HTTP/2 & Protocol Buffers
    - Finagle: Futures
- Asynchronous
  - publish-subscribe: [WebSocket](https://www.ruanyifeng.com/blog/2017/05/websocket.html), Message Queuing Telemetry Transport (MQTT)
  - message queue / message broker: RabbitMQ, Kafka
  - stream: Server-Sent Events (SSE), WebRTC
- Event-driven
  - webhooks (an HTTP callback, vs: API polling)
  - event-based architectures: Event sourcing, Event-driven microservices

### Inter-process Communication (IPC)

- Shared memory, Pipe, Message queue, Semaphore
- Remote procedure call (RPC)
- Sockets
