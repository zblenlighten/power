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
    - Cons: agility, scalability, fault tolerance, single framework
  - Microservices (Evolutionary architecture)
    - Pros: single capabilities, independent as product, decoupling, continuous delivery, componentization, autonomy, scalability
    - When not to use: small, intermingled functionality or data, performance sensitive, quick and dirty, no planned updates
    - Style
      - A suite of small services
      - Bare minimum of centralized management of these services
    - Service Mesh
      - Istio
      - Data Plane - Control Plane
    - Protocol
      - Service discovery (SDP)
  - Serverless
    - AWS Lambda (FaaS)
      - Principles: Invisible infrastructure, Automatic scaling, No paying for unused CPU cycles

- Distributed system (storage + computation + messaging)
  - Three-phase commit protocol (3PC): for solving atomic commit
  - Paxos: for solving consensus in a network (Chubby, ZooKeeper)
  - RPC
    - Dubbo (tcp)
    - gRPC (http2)
  - Hadoop ecosystem
    - Hadoop Distributed File System (HDFS)
      - DataNode
      - NameNode
    - Yarn
    - MapReduce (distributed computation: input, split, map, shuffle, reduce, output)
    - Spark (Livy)
      - MapReduce: Scatter/gather paradigm
      - Resilient Distributed Dataset (RDD)
    - Pig, Hive, HBase
    - Apache Ambari
    - Oozie (workflow scheduler), ZooKeeper
    - Data ingestion: Sqoop, Flume, Kafka
    - Hue
    - External Data Storage - Query Engine

- DevOps
  - Version control: Git (branch, tag)
  - **Load balancer**
    - Hardware LB - Software LB: HAProxy
    - Algorithms: Round Robin, Round Robin with weighted server, Least connections, Least response time, Source IP hash, URL hash
    - Nginx ([入门](https://yq.aliyun.com/articles/423970))
  - Continuous integration / Continuous delivery (CI/CD)
    - Jenkins
  - Container
    - [Docker](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
    - Kubernetes (K8s)
      - Pod
      - Replica set
      - Deployment
      - Service
      - Storage class
      - Persistent Volume Claim
      - Rancher + Helm charts - KEDA
  - Configuration
    - Ansible ([YAML](http://www.ruanyifeng.com/blog/2016/07/yaml.html)): IT automation, configuration management, automatic deployment
    - Puppet
  - Monitor
    - Logging
      - Collection → Transport → Storage → Analysis → Alerting
      - ELK (Elastic)
        - Elasticsearch: Data Store
        - Logstash (Fluentd): Data collection pipeline
        - Kibana: Viewer with filter capabilities
        - Beats: Log shipping
    - Metric ([types](https://prometheus.io/docs/concepts/metric_types/))
    - Tracing
    - Applications
      - Prometheus (service oriented)
      - Zabbix (ip oriented)
      - ~~Dapper (APM: Application performance management)~~
  - Others
    - Terraform
    - OpenStack
    - Firebase (BaaS)
    - VirtualBox + Vagrant
  - Single vs Multi-tenant

- API ([Directory](https://www.programmableweb.com/))
  - Manager: [WSO2](https://docs.wso2.com/display/AM260/Key+Concepts), Kong, Tyk, Zuul
  - Gateway
    - Core: portal features, security, load balancing, protocol transformation, routing, orchestration
    - Admin: API lifecycle (draft, publish, upgrade, etc)
    - Monitor: logging for analytics and monitoring
  - Swagger (OpenAPI Specification)
  - REST client tool (i.e. Postman)

### Modes of dataflow

- Rolling upgrades
  - Backward compatibility: newer code read data that was written by older code (vs: Forward compatibility)
  - Serialization: from data structures in memory to self-contained sequence of bytes (i.e. JSON document) write to file or send over network (vs: Parsing / Deserialization) ([Java: serialization](https://www.geeksforgeeks.org/serialization-in-java/), [Python: pickle](https://www.liaoxuefeng.com/wiki/1016959663602400/1017624706151424))
  - Binary schema driven formats

- Scenarios
  - Database: sending a message to your future self
  - Service calls (RPC vs REST API)
  - Asynchronous message passing (via message broker or actor)

- Message broker (Message-oriented middleware: MOM)
  - Type
    - Advanced Message Queuing Protocol (AMQP)/Java Message Service (JMS) style message broker
    - Log based message broker
  - Message queue: decoupling
    - Examples: RabbitMQ, ZeroMQ, ActiveMQ
  - Kafka (real time analysis, streams, no cluster required)
    - Use cases (Perfect for data intensive scenarios): Messaging, Activity Tracking, Metrics Gathering, Log Aggregation, Stream Processing, Decoupling of System Dependencies
    - Core APIs: Producer, Consumer, Streams, Connector (Record: key, value, timestamp)
    - Reasons to fast:
      - Avoids Random Disk Access (sequential write)
      - Memory Mapped Files (mmap)
      - Zero Copy ([原理](https://www.jianshu.com/p/2581342317ce))
      - Batch Data in Chunks
      - Can Scale Horizontally
    - Topic partitioning: What if a topic gets too big for one computer or one computer is not reliable
    - Kafka Stream (Kafka: data pipeline, Kafka Stream: stream processing, [details](https://www.knowledgehut.com/blog/big-data/kafka-vs-spark))

- Extract (**ETL**: Extract - Transform - Load)
  - Batch: raw logs, files, assets, etc.
  - Stream: events, metrics, etc. (event time, state, deployment, correctness)
    - Windowing: slicing data into chunks
    - Watermarks - Trigger - Accumulators (discarding, accumulating, retracting)
    - Streaming SQL
  - Applications
    - Airflow (web server + scheduler + metadata database + executor + worker)
      - Directed Acyclic Graph (DAG)
      - Operator: action, transfer, sensor
      - Executor: Sequential, Local, Celery, K8s (get the tasks to run from its internal queue and specify how to execute it)
      - CI/CD pipeline with Airflow image containing DAGs: Github repo → Jenkins → K8s → Pod
      - Metrics: counters, gauges, timers (TIG: Telegraf, InfluxDB, Grafana))
    - Apache Storm
    - Apache Flink
  - ETL
    - Data validations: file validations & archival (data source → staging / data lake & data transformation)
    - Business validations: calculations & aggregations (staging → data warehouse - data mart)

### Data storage

- Knowledge
  - Data Volume & Retention period (delete or move to archive data store)
  - Engines
    - log-structure storage (SSTable → LSM Tree)
    - page-oriented storage (B tree)
  - Mutability
  - Filesystem ACL (file vs blob: binary large object)
    - blob storage: relational db, file system, object storage (Ceph), cloud storage
  - Concurrency control
    - Pessimistic locking
    - Optimistic locking
  - Partition([Shard](https://www.digitalocean.com/community/tutorials/understanding-database-sharding))
    - Read/Write Split (read/write master database and read-only slaves)
  - Index: ordered indexing, hash indexing
  - Connection pooling

- RDBMS (each record has fixed schema, vertically scalable)
  - [ORM](http://www.ruanyifeng.com/blog/2019/02/orm-tutorial.html): Object-relational mapping
  - SQL query → Server connector → Parser (parse tree) → Optimization → Execution (i.e. InnoDB, MyIsam, [区别](https://www.zhihu.com/question/20596402))
  - PrepareStatement
    - Get pre compiled and access plan cached in database
    - Prevent SQL Injection attacks
  - Database normalization
  - Database transaction
    - Atomicity
      - ~~Two-Phase Commit (2PC)~~
      - ~~Try-Confirm/Cancel (TCC)~~
    - Consistency
    - Isolation
      - Serializable
      - Repeatable reads
      - Read committed
      - Read uncommitted
    - Durability

- [NoSQL](https://en.wikipedia.org/wiki/NoSQL) (schemas are dynamic, horizontally scalable, designed to be scaled across multiple servers)
  - Key-value: LevelDB, Dynamo, Redis ([点赞功能](https://juejin.im/post/5bdc257e6fb9a049ba410098))
    - Fast & light: caching stores, managing user sessions, ad servicing, recommendations
  - Document: MongoDB, CouchDB, Elasticsearch
    - Schema flexibility: managing user profiles (XML or JSON documents)
    - [Elasticsearch](http://www.ruanyifeng.com/blog/2017/08/elasticsearch.html)
      - Search engine: **Solr** (Lucene)
        - Inverted index
      - Scheme-free JSON documents (Distributed)
      - HTTP web interface (Rest API)
  - Wide-column: Cassandra, HBase
    - Reduce disk resources & fast querying and processing: big-data analysis
  - Graph
  - References
    - [MongoDB vs Elasticsearch](https://mindmajix.com/mongodb-vs-elasticsearch)

- Data Warehouse
  - Analytic systems (OLAP: online analytical processing)
    - Column-oriented
    - Database (Data warehouse): Teradata, Redshift, Hive, Greenplum
      - Star schema (vs: 3NF schema)
        - Fact table: grain
        - Dimension table
      - Snowflake schema
      - [Star Schema vs Snowflake Schema](http://www.ssglimited.com/blog/data-warehouse-design-star-schema-vs-snowflake-schema/)
    - High availability and low latency
    - Business Intelligence: optimization for analytic access patterns
    - On-premises vs Cloud data warehouses (i.e. Ads Data Hub)
  - Transaction processing systems (OLTP: online transaction processing)
    - Row-oriented
    - Database: Oracle, Mysql, PostgreSQL
  - References
    - [Inmon vs Kimball](https://www.zentut.com/data-warehouse/kimball-and-inmon-data-warehouse-architectures/)

- Cache
  - Types
    - Application server cache: placing a cache on request layer node enables the local storage of response data
    - Distribute cache: each of its nodes own part of cached data, the cache is divided up using a consistent hashing function
    - Global cache: all nodes use the same single cache space
    - Content delivery network (**CDN**): first request ask the CDN for data, if not, CDN will query the backend servers
  - Cache coherence / invalidation
    - Writing policies
      - Write-through cache: data is written to cache & DB at the same time, this minimizes the risk of data loss, but higher latency for write 
      - Write-around cache: data is written directly to DB, this reduces flooded write operations, but creates a cache miss
      - Write-back cache: data is written to cache alone, this results in low latency & high throughput, but comes with the risk of data loss in case of crash
    - Distributed lock manager (DLM)
  - [Cache replacement policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)

- Customer data platform (CDP)
  - [Segment](https://segment.com/)
  - Treasure Data
    - Engines
      - Presto: interactive designed for latency & agility
      - Hive: batch designed for throughput & reliability
    - Schemaless Time-based Columnar Data store
      - Schema on read (vs: Schema on write)
        - Checks while reading the data
        - Writes are fast
      - Streaming insert + access
      - Decoupled Storage & Compute
      - Resource pool support
    - Workflows: Digdag (vs: Airflow)
    - Realtime Segment & Batch Segment

### Backend

- Server Content
  - Static sites: CDN
  - Dynamic sites: CGI, Servlet/JavaServer Pages (JSP)
    - Servlet
      - Life cycle: init → service (request & response) → destroy
      - Container: Apache Tomcat (services provided by the Servlet container)
      - Info & Config
    - Session management in HTTP
    - Listener (Event): changing the state of an object
    - Filter (authentication, log, ...)

- Design patterns
  - Object oriented programming (OOP): Polymorphism
  - Creational Patterns: Factory, Singleton
  - Structural Patterns: Decorator, Adapter, Facade, Composite, Proxy
  - Behavioral Patterns: Observer, Command, Template, Iterator, State
  - J2EE Patterns: Compound (**MVC**: Model, View, Controller)
  - Principles (SOLID)
    - Open Close Principle
    - Dependence Inversion Principle
    - Liskov Substitution Principle
    - Single Responsibility Principle
    - Interface Segregation Principle

- Java ([stack frame](https://www.artima.com/insidejvm/ed2/jvm2.html), [field](http://tutorials.jenkov.com/java-reflection/fields.html), jar & war)
  - JVM
    - Architecture: Class Loader - JVM Memory - Execution Engine
    - Application program - Tomcat container - **JVM** process - Operating system - Physical server
  - Spring
    - Core
      - Inversion of Control (IoC) Container
        - Bean life cycle: bean instantiated → dependencies injected → internal Spring processing → custom init method → destroy (except for the "prototype" scoped bean)
      - Annotation: Spring configuration (vs: XML)
        - Inversion of Control: Component
        - Dependency Injection: Autowired, Qualifier, Value, Bean, Configuration, PropertySource
        - Bean scope & life cycle: Scope, PostConstruct, PreDestroy
        - Spring MVC: Controller, RequestMapping, RequestParam, ModelAttribute
        - Hibernate (ORM): Entity, Table, Id, GenerateValue, OneToOne, ManyToOne, OneToMany, ManyToMany
        - Data Access Object (DAO) & Service: Repository, Service, Transactional
    - Spring Aspect oriented programming (AOP)
      - Web layer - Service layer - Repository layer
      - Use cases: logging, security, transaction, exception handling, API management
      - Support: Method-level join points & Run-time code weaving (vs: AspectJ)
      - Annotation: Aspect, Before, AfterReturning, AfterThrowing, After, Around, Pointcut
    - Spring Security (Servlet filter)
      - [Secure a Spring Boot REST API with JSON Web Token](https://medium.com/better-programming/secure-a-spring-boot-rest-api-with-json-web-token-reference-to-angular-integration-e57a25806c50)
    - Spring REST
      - Annotation: RestController, PathVariable, ExceptionHandler, ControllerAdvice, RequestBody
    - Spring Boot (initializr [link](https://start.spring.io/))
      - Solution: perform auto-configuration, provide an embedded HTTP server, resolve dependency conflicts
      - Actuator (endpoints [list](https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html#production-ready-endpoints))
      - Property (properties [list](https://docs.spring.io/spring-boot/docs/current/reference/html/appendix-application-properties.html))
    - DAO techniques
      - Hibernate API
        - Fetch: lazy vs eager
      - Standard Java Persistence API (JPA)
      - Spring Data JPA (→ Spring Data REST: HATEOAS)
    - Spring Cloud
    - Projects: [link](https://spring.io/projects)

- Go ([pointer](https://www.runoob.com/go/go-pointers.html), [channel](https://www.runoob.com/w3cnote/go-channel-intro.html))

- Node.js

### Frontend

- WWW standards
  - CSS ([animation](https://animate.style/))
  - DOM: Document Object Model ([HTML DOM 事件](https://www.runoob.com/jsref/dom-obj-event.html))
  - HTML
  - SVG
  - XML

- Single-page application (vs: multiple-page application)
  - Vue.js
    - Vue Instance - Virtual DOM - DOM
    - VueResource, VueRouter, Vuex
      - Model–view–viewmodel (MVVM): two-way data bindings([双向绑定](https://www.liaoxuefeng.com/wiki/1022910821149312/1109527162256416))
    - Developer Tools: Vue.js devtools
  - AngularJS
  - Webpack
    - Lazy Loading

- Applications
  - UI component: Bootstrap, Ant Design
  - Rich Text Editor
  - BPMN: Business Process Model and Notation (i.e. Rappid)

### System design

- Distributed System Trade-offs
  - Performance vs Scalability
  - Latency vs Throughput
  - Availability vs Consistency (CAP theorem: Consistency, Availability, Partition tolerance)
    - CP vs AP (BASE: Basically Available Soft state Eventual consistency)

- If the system...
  - goes slow: scalability, performance
  - goes down: resiliency (SPOF: single point of failure), availability, stability

- Performance ([techempower](https://www.techempower.com/benchmarks/))
  - Testing
    - Latency (Response time)
    - Number of concurrent sessions/users
    - Throughput: hps, tps, qps (number of HTTP requests/Transactions/Queries per second)
    - Internal metrics: CPU (interrupts per second), Memory, Network (bandwidth, connection state), Disk I/O, etc.
  - Optimization
    - Global Data Center
    - Hardware
    - Operating system (Linux: transparent huge page)
    - JVM
    - Infrastructure: web container, database connection pooling, MVC framework
    - Architecture: cache (read-through vs cache-aside), message broker, clustered architecture
    - Programming: algorithms, data structure, design pattern, asynchronous I/O

- Availability
  - Redundancy backup: Load balancing, database with multi master replication
  - Fault and latency tolerance: Hystrix, message broker
  - Flow control & degrade
  - Global server load balancing (GSLB)

- The Architecture Process
  - Understand the System’s Requirements
  - Understand the Non-Functional Requirements (NFR, SLA: Service-level agreement)
  - Map the Components (logic diagram, technical diagram, physical diagram)
  - Select the Technology Stack
  - Design the Architecture
  - Write Architecture Document
  - Support the Team

- Cases:
  1. Web crawler
      - BFS & DFS (Overhead time) by Scheduler (Priority queue stores URLs that have been discovered but not yet downloaded)
      - Page analysis and URL extraction (parsing Javascript)
      - URL table (In the case of thousands of servers: 明确每台下载服务器的分工，向散列表发送询问判断URL是否下载)

  2. URL shortening
      - Distributed ID Generator
      - Key-value store
      - URL redirection (302)

  3. Messenger service (feature → architecture)
      - One to one text
      - Sent / Delivered / Read
      - Push notification

- References
  - [服务端高并发分布式架构演进之路](https://segmentfault.com/a/1190000018626163)

### Practice

- Code review
  - Programming style
  - Code review best practice
    - [what to look for](https://blog.jetbrains.com/upsource/tag/what-to-look-for/)
    - Human reviewers should be doing what cannot be automated (automate everything you can)
    - Understand the constraints
    - Knowledge sharing (focus on how to understand the code easily)
    - Gateway type code review: should have a list of specific checks (not right time for: design patterns, SOLID, reusability)
    - Reviews should be small
    - Reviewing respond in a timely fashion
    - Comments with Why, When and What

- Project Management
  - Systems development life cycle (SDLC): requirement analysis → design → development and testing → implementation → documentation → evaluation
  - [Agile](http://cheatsheetworld.com/programming/agile-development-cheat-sheet/)
  - Scrum: Transparency, Inspection, Adaptation
  - Kanban
  - Waterfall: System and software requirements → Analysis → Design → Coding → Testing → Operations
  - Project Management Committee ([PMC](https://www.apache.org/foundation/how-it-works.html))

- WBS: Work breakdown structure
  - RfQ: Request for quotation
  - PoC: Proof of concept & SoW: Statement of work
  - Feature (list) & [User story](http://www.myagilediary.com/the-art-of-story-writing-in-agile/)
    - Who, What, Why, Acceptance Criteria (AC)
  - Website wireframe design (i.e. Adobe XD)
  - Software architecture design
  - Coding, testing, release
  - Maintenance & Iterative and incremental development

- Development Approach
  - FDD: Feature-Driven
  - TDD: Test-Driven
  - BDD: Behavior-Driven
  - DDD: Domain-Driven

- Tools
  - Team Collaboration: Jira, Confluence, Asana, Miro, ...
