# Knowledge Memo

## Contents

- [Practice](#practice)
- [Infrastructure](#infrastructure)
- [Data storage](#data-storage)
- [Backend](#backend)
- [Frontend](#frontend)
- [System design](#system-design)

## Development

### Practice

- WBS: Work breakdown structure
  - RfQ: Request for quotation
  - POC: Proof of concept
  - Feature (list) & [User story](http://www.myagilediary.com/the-art-of-story-writing-in-agile/)
    - Who, What, Why, Acceptance Criteria (AC)
  - Website wireframe design (Adobe XD)
  - Software architecture design
  - Coding, testing, pull request, release
  - Maintenance & Iterative and incremental development

- Methodology
  - Waterfall
  - [Agile](http://cheatsheetworld.com/programming/agile-development-cheat-sheet/)

- Development Approach
  - FDD: Feature-Driven
    - Git flow
    - Github flow
    - Gitlab flow
  - TDD: Test-Driven
  - BDD: Behavior-Driven
  - DDD: Domain-Driven

- Other: GDPR, i18n, Karte...

### Infrastructure

- Architecture
  - What: organize business, technology and staff to drive business growth
  - Monolith
  - Microservice (Evolutionary architecture)
    - [Docker](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
    - Kubernetes
    - Service discovery (SDP)
  - Serverless
    - AWS Lambda (FaaS)

- API
  - Manager: [WSO2](https://docs.wso2.com/display/AM260/Key+Concepts), Kong, Zuul, ...
  - Gateway
    - Core: portal features, security, load balancing, protocol transformation, routing, orchestration
    - Admin: API lifecycle (draft, publish, upgrade, etc)
    - Monitor: logging for analytics and monitoring
  - Swagger
  - [API Design](http://static.googleusercontent.com/media/research.google.com/en//pubs/archive/32713.pdf) (backward compatibility and new releases)
  - ~~WireMock~~

- Distributed system
  - Three-phase commit protocol (3PC)：for solving atomic commit
  - Paxos: for solving consensus in a network
  - RPC
    - Dubbo
    - gRPC

- Message broker (Message-oriented middleware: MOM)
  - Kafka
    - Concepts: cluster, topics, record (key, value, timestamp)
    - Core APIs: Producer, Consumer, Streams, Connector
    - Use cases: Messaging, Website Activity Tracking, Metrics, Log Aggregation, Stream Processing, Event Sourcing, Commit Log
    - Reasons to fast:
      - Avoids Random Disk Access (sequential write)
      - Memory Mapped Files (mmap)
      - Zero Copy ([原理](https://www.jianshu.com/p/2581342317ce))
      - Batch Data in Chunks
      - Can Scale Horizontally
  - ActiveMQ, RabbitMQ

- Search engine
  - Elasticsearch (Solr)
    - Lucene (Inverted index)
    - Restful API (HTTP)
    - Distributed (master - slave)

- Stream
  - Spark: Resilient Distributed Dataset (RDD)
  - Flink

- Batch
  - MapReduce
  - Airflow (Workflow management)
    - ~~Celery~~

- Monitoring
  - Logging (Event)
    - Collection → Transport → Storage → Analysis → Alerting
    - ELK: Elasticsearch, Logstash, Kibana
    - Graylog
  - Metric ([types](https://prometheus.io/docs/concepts/metric_types/))
  - Tracing
  - Tools
    - Prometheus (service oriented)
    - Zabbix (ip oriented)
    - ~~Dapper (APM: Application performance management)~~

- DevOps
  - Continuous integration / Continuous delivery (CI/CD)
    - Jenkins
  - Version control
  - Configuration
    - Ansible
    - Puppet
  - Single vs. Multi-tenant

- Other
  - [Vim](http://www.ruanyifeng.com/blog/2018/09/vimrc.html)
  - Terraform
  - Google Analysis
  - Team Collaboration: Miro

### Data storage

- Knowledge
  - Engines
    - log-structure storage (SSTable → LSM Tree)
    - page-oriented storage (B tree)
  - Concurrency control
    - Pessimistic locking
    - Optimistic locking
  - SnowFlake
  - Scaling
    - Read/Write Split (read/write master database and read-only slaves)
    - [Shard](https://www.digitalocean.com/community/tutorials/understanding-database-sharding): speed up query response time (a type of horizontal partition)

- File System
  - Linux (inode)
  - Redundant Array of Independent Disks (RAID): 0, 1, 10, 5, 6
  - Hadoop Distributed File System (HDFS): MapReduce/Spark
    - DataNode
    - NameNode

- RDBMS
  - [ORM](http://www.ruanyifeng.com/blog/2019/02/orm-tutorial.html): Object-relational mapping
  - SQL query → Server connector → Parser (parse tree) → Optimization → Execution (InnoDB, MyIsam)
  - PrepareStatement
    - Get pre compiled and access plan cached in database
    - Prevents SQL Injection attacks

- [NoSQL](https://en.wikipedia.org/wiki/NoSQL)
  - Key-value: **LevelDB**, Dynamo, Redis ([点赞功能](https://juejin.im/post/5bdc257e6fb9a049ba410098))
  - Document: MongoDB
  - Wide-column: HBase
  - Graph

- [Cache](https://en.wikipedia.org/wiki/Cache_(computing))
  - [Cache replacement policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)
  - Cache coherence: Distributed lock manager (DLM): Chubby, ZooKeeper

- Business Intelligence
  - Database: Oracle, Mysql, PostgreSQL
  - Data warehouse: Redshift, Hive, Greenplum (OLTP: Online analytical processing Database)

### Backend

- Server Content
  - Static sites
    - Content delivery network (CDN): push, pull
  - Dynamic sites
    - JSP/Servlet

- Authentication: you are who you say you are
  - ~~OpenID~~
  - Cryptographic hash function: MD5 (rainbow table), Secure Hash Algorithm (SHA)
  - Public-key cryptography
  - Hash-based message authentication code (HMAC)
  - Kerberos (kinit, rlogin, ...)

- Authorization: you are permitted to do what you are trying to do
  - [OAuth 2.0](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html): token
  - [JSON Web Token](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html) (JWT)

- Java
  - Spring

- Python
  - Flask

- Go ([pointer](https://www.runoob.com/go/go-pointers.html), [channel](https://www.runoob.com/w3cnote/go-channel-intro.html))
  - Beego

- Ruby
  - Rails

### Frontend

- JavaScript
  - Node.js
  - Vue
    - Model–view–viewmodel (MVVM)
      - Model: JavaScript
      - View: HTML
      - two-way data bindings([双向绑定](https://www.liaoxuefeng.com/wiki/1022910821149312/1109527162256416)）
    - Vuex
  - Rich Text Editor
  - Business Process Model and Notation (BPMN): Rappid

- WWW standards
  - CSS
  - DOM: Document Object Model
  - HTML
  - SVG
  - XML

- Security
  - [Content Security Policy](http://www.ruanyifeng.com/blog/2016/09/csp.html) (CSP)
  - [Same-origin policy](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html): [Cross-Origin Resource Sharing](http://www.ruanyifeng.com/blog/2016/04/cors.html) (CORS)
    - cookie

### System design

- ~~steps~~:
  - ~~Use case, constraints and assumptions~~

- if the system...
  - goes slow: **scalability**, performance
  - goes down: **resiliency** (single point of failure (SPOF) ), availability, stability

- trade-offs:
  - Performance vs Scalability
  - Latency vs Throughput
  - Availability vs Consistency: Consistency, Availability, Partition tolerance (CAP)
    - CP vs AP (BASE: Basically Avaiable Soft state Eventual consistency)

- cases:
  1. Web crawler
      - BFS & DFS (Overhead time) by Scheduler (Priority queue stores URLs that have been discovered but not yet downloaded)
      - Page analysis and URL extraction (parsing Javascript)
      - URL table (In the case of thousands of servers: 明确每台下载服务器的分工，向散列表发送询问判断URL是否下载)

  2. Search engine
      - PageRank

  3. URL shortening
      - Distributed ID Generator
      - Key-value store
      - URL redirection (302)

  4. Twitter / News feed

- references
  - [服务端高并发分布式架构演进之路](https://segmentfault.com/a/1190000018626163)
