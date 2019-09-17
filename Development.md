# Knowledge Memo

## Contents

- [Practice](#practice)
- [Infrastructure](#infrastructure)
- [Data store](#data-store)
- [Backend](#backend)
- [Frontend](#frontend)
- [System design](#system-design)

## Development

### Practice

- WBS: Work breakdown structure
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
- Other
  - GDPR
  - i18n
  - Karte

### Infrastructure

- Architecture
  - Monolith
  - Microservice
    - Kubernetes
    - Docker
  - Serverless
    - AWS Lambda (FaaS)
- API Gateway
- Service Function
  - Message broker (Message queue)
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
  - Search engine
    - Elasticsearch (Solr)
      - Lucene (Inverted index)
      - Restful API (HTTP)
      - Distributed (Master - slave)
  - Log monitoring
    - ELK: Elasticsearch, Logstash, Kibana
- Distributed
  - Hadoop
    - MapReduce
  - Zookeeper
  - Data Replicate Center
- DevOps
  - CI/CD
    - Jenkins
  - Version control
- Tools
  - [Vim](http://www.ruanyifeng.com/blog/2018/09/vimrc.html)
  - Terraform
  - Swagger
  - WireMock (?)
  - Google Analysis

### Data store

- Components
  - Concurrency control
    - Pessimistic locking
    - Optimistic locking
  - SnowFlake
  - Sharding: response time (a type of horizontal partition)
  - <strong>Tuning</strong>

- [Cache](https://en.wikipedia.org/wiki/Cache_(computing))
  - [Cache replacement policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)

- SQL DBMS
  - ORM: Object-relational mapping

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
- Language
  - Java
    - Spring
  - Python
    - Django
    - webpy
  - Go
    - Beego
  - Ruby
    - Rails

### Frontend

- JavaScript
  - Node.js
    - npm
  - Vue
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
  - [JSON Web Token](ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html) (JWT)
- Security
  - Cryptographic hash function: MD5 (rainbow table)
  - [Content Security Policy](http://www.ruanyifeng.com/blog/2016/09/csp.html) (CSP)
  - [Same-origin policy](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html): [Cross-Origin Resource Sharing](http://www.ruanyifeng.com/blog/2016/04/cors.html) (CORS)
    - cookie

### System design

- steps:
  - Use case, constraints and assumptions

- trade-offs:
  - Performance vs scalability
  - Latency vs throughput
  - Availability vs consistency
    - CAP: Consistency, Availability, Partition tolerance

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
