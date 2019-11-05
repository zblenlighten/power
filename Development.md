# Knowledge Memo

## Contents

- [Practice](#practice)
- [Infrastructure](#infrastructure)
- [Distributed system](#distributed-system)
- [Data storage](#data-storage)
- [Backend](#backend)
- [Frontend](#frontend)
- [System design](#system-design)

## Development

### Practice

- WBS: Work breakdown structure
  - RfQ: Request for quotation
  - POC: Proof of concept
  - Feature (list)
  - [User story](http://www.myagilediary.com/the-art-of-story-writing-in-agile/)
    - Who, What, Why, Acceptance Criteria (AC)
  - Website wireframe design (Adobe XD)
  - Database design
  - Coding & QA
  - Release
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
    - [Docker](http://www.ruanyifeng.com/blog/2018/02/docker-wordpress-tutorial.html)
    - Kubernetes
    - Service discovery (SDP)
  - Serverless
    - AWS Lambda (FaaS)
  - Event Driven

- DevOps
  - Continuous integration / Continuous delivery (CI/CD)
    - Jenkins
  - Version control
  - Single vs. Multi-tenant

- API
  - Gateway
    - Core: portal features, security, load balance, protocol transformation, routing, orchestration
    - Admin: API lifecycle (draft, publish, upgrade, etc)
    - Monitor: analytics, monitoring
  - Swagger
  - ~~WireMock~~

- Search engine
  - Elasticsearch (Solr)
    - Lucene (Inverted index)
    - Restful API (HTTP)
    - Distributed (master - slave)

- Log
  - Tools
    - ELK: Elasticsearch, Logstash, Kibana
    - Graylog
  - Stream

- Operation and maintenance
  - Application performance management (APM)
    - ~~Dapper~~
  - Monitoring
    - Zabbix
  - Workflow management
    - Airflow
      - Celery

- Other
  - [Vim](http://www.ruanyifeng.com/blog/2018/09/vimrc.html)
  - Terraform
  - Google Analysis
  - Team Collaboration: Miro

### Distributed system

- Protocols
  - Three-phase commit protocol (3PC)：for solving atomic commit
  - Paxos: for solving consensus in a network

- Frameworks
  - Hadoop
    - MapReduce

- Softwares
  - Zookeeper
  - Consul

- Message broker (Message-oriented middleware: MOM)
  - Kafka
    - Concepts: cluster, topics, record (key, value, timestamp)
    - Core APIs: Producer, Consumer, Streams, Connector
    - Use cases: Messaging, Website Activity Tracking, Metrics, Log Aggregation, Stream Processing, Event Sourcing, Commit Log
    - Reasons to fast:
      - Avoids Random Disk Access (sequential write)
      - Memory Mapped Files (mmap)
      - Zero Copy (sendfile)
      - Batch Data in Chunks
      - Can Scale Horizontally
  - ActiveMQ, RabbitMQ

- Data storage
  - Data Replicate Center

### Data storage

- Components
  - Concurrency control
    - Pessimistic locking
    - Optimistic locking
  - SnowFlake
  - Sharding: response time (a type of horizontal partition)
  - Database tuning

- [Cache](https://en.wikipedia.org/wiki/Cache_(computing))
  - [Cache replacement policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)

- SQL DBMS
  - [ORM](http://www.ruanyifeng.com/blog/2019/02/orm-tutorial.html): Object-relational mapping

- [NoSQL](https://en.wikipedia.org/wiki/NoSQL)
  - Key-value: LevelDB, Dynamo, Redis
  - Document: MongoDB
  - Wide-column: HBase
  - Graph

### Backend

- Server Content
  - Static sites
    - Content delivery network (CDN): push, pull
  - Dynamic sites
    - JSP/Servlet

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
    - npm
  - Vue
    - Vuex
  - Rich Text Editor: Froala
  - Business Process Model and Notation (BPMN): Rappid

- WWW standards
  - CSS
  - DOM: Document Object Model
  - HTML
  - SVG
  - XML

- Authentication
  - [OAuth 2.0](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html): token
  - [JSON Web Token](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html) (JWT)

- Security
  - Cryptographic hash function: MD5 (rainbow table)
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
