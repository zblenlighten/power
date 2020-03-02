# Knowledge Memo

## Blogs

- [Netflix](https://medium.com/netflix-techblog)
- [Airbnb](https://medium.com/airbnb-engineering)
- [Uber](https://eng.uber.com/)
- [LinkedIn](https://engineering.linkedin.com/blog)
- [Facebook](https://engineering.fb.com)

## Contents

- [Infrastructure](#infrastructure)
- [Modes of dataflow](#modes-of-dataflow)
- [Data storage](#data-storage)
- [Backend](#backend)
- [Frontend](#frontend)
- [System design](#system-design)
- [Practice](#practice)

## Development

### Infrastructure

- Architecture: organize business, technology and staff to drive business growth
  - Monolith
  - Microservices (Evolutionary architecture)
    - Style
      - A suite of small services
      - Bare minimum of centralized management of these services
    - Service Mesh
      - Istio
    - Protocol
      - Service discovery (SDP)
  - Serverless
    - AWS Lambda (FaaS)

- API
  - Manager: [WSO2](https://docs.wso2.com/display/AM260/Key+Concepts), Kong, Tyk, Zuul, ...
  - Gateway
    - Core: portal features, security, load balancing, protocol transformation, routing, orchestration
    - Admin: API lifecycle (draft, publish, upgrade, etc)
    - Monitor: logging for analytics and monitoring
  - Swagger
  - [API Design](http://static.googleusercontent.com/media/research.google.com/en//pubs/archive/32713.pdf)

- Distributed system
  - Three-phase commit protocol (3PC)：for solving atomic commit
  - Paxos: for solving consensus in a network (Chubby, ZooKeeper)
  - Thrift
  - Flume
  - Hadoop
    - Hadoop Distributed File System (HDFS)
    - Hadoop MapReduce
    - HBase
  - RPC
    - Dubbo
    - gRPC

- Search engine
  - [Elasticsearch](http://www.ruanyifeng.com/blog/2017/08/elasticsearch.html) (Solr)
    - Lucene
      - Inverted index
    - Restful API
    - Distributed (master - slave)

- Monitor
  - Logging (Event)
    - Collection → Transport → Storage → Analysis → Alerting
    - ELK: Elasticsearch, Logstash (Fluentd), Kibana
    - Graylog
  - Metric ([types](https://prometheus.io/docs/concepts/metric_types/))
  - Tracing
  - Tools
    - Prometheus (service oriented)
    - Zabbix (ip oriented)
    - ~~Dapper (APM: Application performance management)~~

- DevOps
  - Version control
    - Git
  - Continuous integration / Continuous delivery (CI/CD)
    - Jenkins
    - Webhook
  - Container
    - [Docker](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
    - Kubernetes
  - Configuration
    - Ansible ([YAML](http://www.ruanyifeng.com/blog/2016/07/yaml.html))
    - Puppet
  - Load balancer
    - Nginx ([入门](https://yq.aliyun.com/articles/423970))
  - Single vs Multi-tenant

- Tools
  - Terraform
  - ~~Google Analysis~~
  - Team Collaboration: Miro

### Modes of dataflow

- Rolling upgrades
  - Backward compatibility: newer code read data that was written by older code (vs: Forward compatibility)
  - Serialization: from data structures in memory to self-contained sequence of bytes (i.e. JSON document) write to file or send over network (vs: Parsing / Deserialization)
    - [Java: serialization](https://www.geeksforgeeks.org/serialization-in-java/)
    - [Python: pickle](https://www.liaoxuefeng.com/wiki/1016959663602400/1017624706151424)
  - Binary schema driven formats

- Scenarios
  - Database: sending a message to your future self
  - Service calls (RPC and REST APIs)
  - Asynchronous message passing (via message broker or actor)

- Message broker (Message-oriented middleware: MOM)
  - Type
    - Advanced Message Queuing Protocol (AMQP)/Java Message Service (JMS) style message broker
    - Log based message broker
  - Software
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
    - ActiveMQ
    - RabbitMQ

- Batch & Stream
  - Airflow (Workflow management)
  - Spark: Resilient Distributed Dataset (RDD)
  - Storm
  - Flink

### Data storage

- Knowledge
  - Engines
    - log-structure storage (SSTable → LSM Tree)
    - page-oriented storage (B tree)
  - Database transaction
    - Atomicity
    - Consistency
    - Isolation
      - Serializable
      - Repeatable reads
      - Read committed
      - Read uncommitted
    - Durability
  - Concurrency control
    - Pessimistic locking
    - Optimistic locking
  - SnowFlake
  - Partition([Shard](https://www.digitalocean.com/community/tutorials/understanding-database-sharding))
    - Read/Write Split (read/write master database and read-only slaves)

- File System
  - Linux ([inode](https://www.ruanyifeng.com/blog/2011/12/inode.html))
  - Redundant Array of Independent Disks (RAID): 0, 1, 10, 5, 6
  - HDFS
    - DataNode
    - NameNode

- RDBMS
  - [ORM](http://www.ruanyifeng.com/blog/2019/02/orm-tutorial.html): Object-relational mapping
  - SQL query → Server connector → Parser (parse tree) → Optimization → Execution (i.e. InnoDB, MyIsam)
  - PrepareStatement
    - Get pre compiled and access plan cached in database
    - Prevent SQL Injection attacks

- [NoSQL](https://en.wikipedia.org/wiki/NoSQL)
  - Key-value: LevelDB, Dynamo, Redis ([点赞功能](https://juejin.im/post/5bdc257e6fb9a049ba410098))
  - Document: MongoDB
  - Wide-column: HBase
  - Graph

- [Cache](https://en.wikipedia.org/wiki/Cache_(computing))
  - [Cache replacement policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)
  - Cache coherence: Distributed lock manager (DLM)

- Comparison
  - Transaction processing systems (OLTP: online transaction precessing)
    - Row-oriented
    - Database: Oracle, Mysql, PostgreSQL
  - Analytic systems (OLAP: Online analytical processing)
    - Column-oriented
    - Database (Data warehouse): Teradata, Redshift, Hive, Greenplum
    - High availability and low latency
    - Business Intelligence: optimization for analytic access patterns

- References
  - [MongoDB vs Elasticsearch](https://mindmajix.com/mongodb-vs-elasticsearch)

### Backend

- Server Content
  - Static sites: ~~Content delivery network (CDN)~~
  - Dynamic sites: CGI, Servlet/JavaServer Pages (JSP)
    - Servlet
      - Life cycle: init, service (request & response), destroy
      - Container: Apache Tomcat (services provided by the Servlet container)
      - Info & Config
    - Session management in HTTP
      - URL Rewriting & Hidden form filed
      - Cookies
      - HTTPSession
    - JSP: ~~Expression Language, Standard Tag Library (JSTL), JavaBean, Tag~~
    - Listener (Event): changing the state of an object
      - ServletContext, HttpSession, ServletRequest
    - Filter (authentication, log, ...)
      - Wrapper
    - Other topics
      - ErrorHandler
      - JDBC
      - Development: registration, uploading & downloading files, sending email, writing image, ...

- Java
  - Spring
    - Core
      - Inversion of Control (IoC) Container
        - Bean
      - Annotation
        - **Dependency Injection**: Autowired, Bean
        - Context Configuration
        - Stereotype: Component, Controller, Service, Repository
    - Aspect oriented programming (AOP)
      - Web Layer: **controller**, exception handler, filter, view template
      - **Service** Layer
      - **Repository** Layer
    - Projects: [link](https://spring.io/projects)
  - Design patterns
    - Creational Patterns: Factory, Singleton
    - Structural Patterns: Decorator, Adapter, Facade, Composite, Proxy
    - Behavioral Patterns: Observer, Command, Template, Iterator, State
    - J2EE Patterns: Compound (MVC: Model, View, Controller)
    - Principles
      - Single Responsibility Principle
      - Open Close Principle
      - Liskov Substitution Principle
      - Interface Segregation Principle
      - Dependence Inversion Principle
      - ~~Demeter Principle & Composite Reuse Principle~~

- Go ([pointer](https://www.runoob.com/go/go-pointers.html), [channel](https://www.runoob.com/w3cnote/go-channel-intro.html))

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
  - BPMN: Business Process Model and Notation (i.e. Rappid)

- WWW standards
  - CSS
  - DOM: Document Object Model
  - HTML
  - SVG
  - XML

### System design

- If the system...
  - goes slow: **scalability**, performance
  - goes down: **resiliency** (SPOF: single point of failure), availability, stability

- Trade-offs:
  - Performance vs Scalability
  - Latency vs Throughput
  - Availability vs Consistency: Consistency, Availability, Partition tolerance (CAP)
    - CP vs AP (BASE: Basically Available Soft state Eventual consistency)

- Cases:
  1. Web crawler
      - BFS & DFS (Overhead time) by Scheduler (Priority queue stores URLs that have been discovered but not yet downloaded)
      - Page analysis and URL extraction (parsing Javascript)
      - URL table (In the case of thousands of servers: 明确每台下载服务器的分工，向散列表发送询问判断URL是否下载)

  2. Search engine
      - PageRank
      - Search Engine Optimizer

  3. URL shortening
      - Distributed ID Generator
      - Key-value store
      - URL redirection (302)

  4. Twitter / Feed
      - // TODO
  
  5. Messenger service (feature → architecture)
      - One to one text
      - Sent / Delivered / Read
      - Push notification

  6. Yelp
      - // TODO

  7. Uber
      - // TODO

  8. EC platform
      - // TODO

- References
  - [服务端高并发分布式架构演进之路](https://segmentfault.com/a/1190000018626163)

### Practice

- Programming style
  - [Java Style](https://google.github.io/styleguide/javaguide.html)
  - [Python Style](https://google.github.io/styleguide/pyguide.html)

- WBS: Work breakdown structure
  - RfQ: Request for quotation
  - POC: Proof of concept
  - Feature (list) & [User story](http://www.myagilediary.com/the-art-of-story-writing-in-agile/)
    - Who, What, Why, Acceptance Criteria (AC)
  - Website wireframe design (i.e. Adobe XD)
  - Software architecture design
  - Coding, testing, pull request, release
  - Maintenance & Iterative and incremental development

- Methodology
  - Waterfall
  - [Agile](http://cheatsheetworld.com/programming/agile-development-cheat-sheet/)

- Development Approach
  - FDD: Feature-Driven
  - TDD: Test-Driven
  - BDD: Behavior-Driven
  - DDD: Domain-Driven
