# Knowledge Memo

## Blogs

- [top 100 on GitHub](https://twosigmaventures.com/open-source-index/)
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
  - Application Landscape
    - Monolith
      - Cons: agility, scalability, fault tolerance, single framework
    - Multitier architecture (N-tier): an MVC design is often implemented using an 3-tier architecture
    - Service-oriented architecture (SOA)
    - Microservices
      - Pros: single capabilities, independent as product, decoupling, continuous delivery, componentization, autonomy, scalability
      - When not to use: small, intermingled functionality or data, performance sensitive, quick and dirty, no planned updates
      - Reactive system (vs: Declarative system)
      - Service Mesh
        - Istio
        - Data Plane - Control Plane
      - Service discovery (SDP)
      - Challenges
        - Design and runtime complexity
        - Network are slow compared to monolith
    - Serverless (run in stateless compute containers that are event triggered)
      - Principles: Invisible infrastructure, Automatic scaling, No paying for unused CPU cycles
      - Function as a Service
        - AWS Lambda 
        - Google Cloud Functions
      - Backend as a Service
        - Firebase
    - Peer-to-peer
  - Application Structure
    - Command query responsibility segregation (CQRS) & event sourcing
    - References
      - [Microservices Patterns](https://microservices.io/patterns/)
      - [Azure Cloud Design Patterns](https://docs.microsoft.com/en-us/azure/architecture/patterns/)
  - Distributed system (storage + computation + messaging)
    - Three-phase commit protocol (3PC): for solving atomic commit
    - Paxos: for solving consensus in a network (Chubby, ZooKeeper)
    - RPC
      - gRPC (http/2)
      - Thrift
  - Load balancer
    - Hardware LB - Software LB: HAProxy
    - Algorithms: Round Robin, Round Robin with weighted server, Least connections, Least response time, Source IP hash, URL hash
    - Nginx ([入门](https://yq.aliyun.com/articles/423970))
  - User Interface (UI)
    - MVC: Model-view-controller
    - MVVM: Model–view–viewmodel
  - Single vs Multi-tenant

- DevOps
  - Version control
    - Git: branch, tag
  - Infrastructure as code (consider hardware: networks, servers, storage, etc.)
    - Terraform: Write → Plan → Apply
    - Ansible ([YAML](http://www.ruanyifeng.com/blog/2016/07/yaml.html))
    - Provision: Docker file / Puppet / Chef
  - Configuration (deploy and configure software: operating systems, applications, etc.)
    - Jenkins (CI/CD: Continuous integration / Continuous delivery / Continuous deployment)
    - ZooKeeper (central coordinator: manage state and hold configuration)
    - Automation and Orchestration
      - Automation refers to a single task
      - Orchestration refers to the management of many Automated tasks, often a complicated ordering with dependencies
  - DevSecOps
    - Static application security testing (SAST): Find Security Bugs
    - Dynamic application security testing (DAST): ZAP, WebInspect
    - Interactive application security testing (IAST)
    - Vulnerability scanning: OpenVAS
    - Others: sqlmap, Recon-ng, OWASP Glue
  - Container
    - [Docker](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
      - Manage kernel features
        - cgroups: processes
        - namespaces: networks
        - copy-on-write: unionfs
      - Docker components
        - Dockerfile → Docker Client → Docker Host (images, containers, volumes) → Docker Registry
        - Dockerfile: multi-stage builds
    - Kubernetes (Docker compose, Docker swarm)
      - [Do I need K8s?](https://mbird.biz/writing/do-i-need-kubernetes.html)
      - Pod
      - Replica set
      - Deployment
      - Service
      - Storage class
      - Persistent Volume Claim
      - Rancher + Helm charts - KEDA
    - Nvidia docker
  - Monitor
    - Synthetic check and uptime (is it working?)
    - Software component metrics
    - System metrics
    - App metrics
    - Performance
      - Application performance management (APM)
      - Real user monitoring (RUM)
    - Tools
      - Prometheus (service oriented)
        - Metric ([types](https://prometheus.io/docs/concepts/metric_types/))
        - Grafana
      - Zabbix (ip oriented)
      - Datadog
  - Logging
    - Collection → Transport → Storage → Analysis → Alerting
    - Centralized Logging
    - ELK (Elastic)
      - Elasticsearch: Search engine + document store (JSON)
      - Logstash (vs: Fluentd): Data collection pipeline
        - Filter plugin: Grok (log parser)
        - Input plugin: Twitter
      - Kibana: Viewer with filter capabilities
        - Kibana Query Language (KQL)
      - [Beats](https://www.elastic.co/guide/en/beats/libbeat/current/beats-reference.html): Data shipping
  - Reliability
    - Mean time to recovery (MTTR)
    - Mean time between failures (MTBF)
    - Chaos Monkey
    - Hystrix (Circuit Breaker pattern: cascading failures)
    - Profiler
  - Security
    - Penetration test
    - [Web Application Security Checklist](https://www.appsecmonkey.com/blog/web-application-security-checklist)
  - Testing
    - Code coverage
  - Others
    - OpenStack
    - Heroku (dynamic page)

- API
  - RPC: for actions (procedures / commands)
  - [REST API](http://www.ruanyifeng.com/blog/2014/05/restful_api.html): for modeling domain (resources / entities) & making CRUD
    - Uniform Resource Identifier (URI) = URL + URN
      - URL = &lt;**scheme**>://&lt;user>:&lt;password>@&lt;**host**>:&lt;port>/&lt;**path**>;&lt;params>?&lt;query>#&lt;fragment>
    - [Architectural constraints](https://restfulapi.net/rest-architectural-constraints/)
    - Versioning
      - Accept header
      - Resource URL
    - Media Type & Content-Type
    - Authentication (AuthN: who you are)
      - Basic authentication & Digest authentication
      - Login form, HTTP authentication, ...
      - Key management (cryptographic keys)
    - Authorization (AuthZ: what you can do)
      - Role-based access control (RBAC)
      - URL access controls, ...
      - Access control list (ACL)
        - Filesystem ACL
        - Network ACL
        - SQL ACL
  - Design of REST APIs
    - Identify participants
    - Identify activities
    - Break into steps
    - Create API definition
      - Identify the resources
        - Items resource: list, view, search, add, edit
      - Map activities to resource lifecycle (map actions to HTTP Nouns & Verbs)
        - Mapping: GET /items, GET /items/:id, GET /items?search=param, POST /items/, PUT /items/:id
      - Map remaining activities to custom actions
        - Relationships types: Independent, Dependent, Associative
    - Validate API
  - Tools
    - Manager: [WSO2](https://docs.wso2.com/display/AM260/Key+Concepts), Kong, Tyk, Zuul
    - Gateway
      - Core: portal features, security, load balancing, protocol transformation, routing, orchestration
      - Admin: API lifecycle (draft, publish, upgrade, etc.)
      - Monitor: logging for analytics and monitoring
    - Swagger (OpenAPI Specification)
    - REST client tool (e.g. Postman)
  - References
    - [API Directory](https://www.programmableweb.com/)

### Modes of dataflow

- Rolling upgrades
  - Backward compatibility: newer code read data that was written by older code (vs: Forward compatibility)
  - Serialization: from data structures in memory to self-contained sequence of bytes (e.g. JSON document) write to file or send over network (vs: Parsing / Deserialization) ([Java: serialization](https://www.geeksforgeeks.org/serialization-in-java/), [Python: pickle](https://www.liaoxuefeng.com/wiki/1016959663602400/1017624706151424))
  - Binary schema driven formats

- Scenarios
  - Database: sending a message to your future self
  - Service calls (RPC vs REST API)
  - Asynchronous message passing (via message broker or actor)

- Messaging (Message-oriented middleware: MOM)
  - Type
    - Advanced Message Queuing Protocol (AMQP)/Java Message Service (JMS) style message broker
    - Log based message broker
  - Message queue: decoupling
    - Examples: RabbitMQ, ZeroMQ, ActiveMQ
  - Kafka (real time analysis, streams, no cluster required)
    - Use cases (Perfect for data intensive scenarios): Messaging, Activity Tracking, Metrics Gathering, Log Aggregation, Stream Processing, Decoupling of System Dependencies
    - Core APIs: Producer, Consumer, Streams, Connector (Record: key, value, timestamp)
      - RTSP (Real time streaming protocol) producer
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
        - Celery: tasks queues to distribute work across threads or machines
      - CI/CD pipeline with Airflow image containing DAGs: Github repo → Jenkins → K8s → Pod
      - Metrics: counters, gauges, timers (TIG: Telegraf, InfluxDB, Grafana)
    - Apache Storm / Apache Flink
  - ETL
    - Data validations: file validations & archival (data source → staging / data lake & data transformation)
    - Business validations: calculations & aggregations (staging → data warehouse - data mart)

### Data storage

- Knowledge
  - Data Volume & Retention period (delete or move to archive data store)
  - Query Tuning
    - Index types
      - B tree
      - Bitmap
      - Hash
      - Specialized index
    - Joins (PostgreSQL: vacuum & analyze)
      - Nestloop
      - Hashjoin
      - Mergejoin
    - Partitioning / [Sharding](https://www.digitalocean.com/community/tutorials/understanding-database-sharding) (horizontal partitioning)
      - Range
      - List
      - Hash
    - Materialized view (vs: view)
  - Engines
    - log-structure storage (SSTable → LSM Tree)
    - page-oriented storage (B tree)
  - Filesystem ACL (file vs blob: binary large object)
    - blob storage: relational db, file system, object storage (Ceph), cloud storage
  - Concurrency control
    - Pessimistic locking
    - Optimistic locking
  - Connection pooling

- RDBMS (each record has fixed schema, vertically scalable)
  - [ORM](http://www.ruanyifeng.com/blog/2019/02/orm-tutorial.html): Object-relational mapping
  - SQL query → Server connector → Parser (parse tree) → Optimization → Execution (e.g. InnoDB, MyIsam, [区别](https://www.zhihu.com/question/20596402))
  - PrepareStatement
    - Get pre compiled and access plan cached in database
    - Prevent SQL Injection attacks
  - Database normalization
  - Database transaction (ACID, vs: BASE)
    - Atomicity
    - Consistency
    - Isolation
      - Serializable
      - Repeatable reads
      - Read committed
      - Read uncommitted
    - Durability

- [NoSQL](https://en.wikipedia.org/wiki/NoSQL) (schemas are dynamic, horizontally scalable, designed to be scaled across multiple servers)
  - Key-value (fast & light: caching stores, managing user sessions, ad servicing, recommendations)
    - LevelDB, Dynamo, Redis ([点赞功能](https://juejin.im/post/5bdc257e6fb9a049ba410098))
  - Document (schema flexibility: managing user profiles (XML or JSON documents) )
    - MongoDB
      - Document - Collection - Database
      - Replication sets: single master architecture
      - Support many indices (only one can be used for sharding): text search, geospatial
    - CouchDB
    - [Elasticsearch](http://www.ruanyifeng.com/blog/2017/08/elasticsearch.html)
      - Search engine: **Solr** (Lucene)
        - Inverted index
      - Scheme-free JSON documents (distributed)
  - Wide-column (reduce disk resources & fast querying and processing: big data store)
    - Cassandra
      - No master node → No single point of failure
      - Gossip protocol
      - CQL, CQLSH
      - DataStax: Spark + Cassandra
    - HBase
  - Graph
    - Neo4j
  - Ledger
    - Hyperledger

- Data Warehouse
  - Analytic systems (OLAP: online analytical processing)
    - Column-oriented
    - Database (Data warehouse): Hive, Teradata, Greenplum
    - Cloud data warehouse: Redshift, BigQuery, Ads Data Hub, Azure Synapse Analytics, Snowflake
    - Databricks
      - [Comparison of Delta Lake, Iceberg and Hudi](https://databricks.com/session_na20/a-thorough-comparison-of-delta-lake-iceberg-and-hudi)
    - Schemas
      - [Star Schema vs Snowflake Schema](http://www.ssglimited.com/blog/data-warehouse-design-star-schema-vs-snowflake-schema/)
    - High availability and low latency (business Intelligence: optimization for analytic access patterns)
  - Transaction processing systems (OLTP: online transaction processing)
    - Row-oriented
    - Database: MySql, PostgreSQL, Oracle

- Hadoop
  - **MapReduce** (distributed computation: input, split, map, shuffle, reduce, output)
  - Hadoop Distributed File System (**HDFS**: NameNode - DataNode)
  - Yarn
  - Spark (Livy)
    - MapReduce: Scatter/gather paradigm
    - Resilient Distributed Dataset (RDD)
    - Components: Spark Core, Spark Steaming, Spark SQL, MLLib, GraphX
  - Hive
    - HiveQL (easier OLAP query than Mapreduce in Java), scalable, interactive
    - High latency (not appropriate for OLTP), no transactions, no record (because under the hood there are no real database)
  - Pig
  - HBase ([Bigtable](https://en.wikipedia.org/wiki/Bigtable))
    - ZooKeeper
    - Access ways: HBase shell, Java API, Spark, Hive, Pig, Rest API, Thrift, Avro
  - Data ingestion: Sqoop (relational database), Flume, Kafka
  - External Data Storage - Query Engine

- Cache
  - Types
    - Application server cache: placing a cache on request layer node enables the local storage of response data
    - Distribute cache: each of its nodes own part of cached data, the cache is divided up using a consistent hashing function
    - Global cache: all nodes use the same single cache space
    - Content delivery network (**CDN**): first request ask the CDN for data, if not, CDN will query the backend servers
      - Fastly, Cloudflare vs Amazon CloudFront
      - Static page vs Dynamic page (CGI)
      - [CDN工作原理及其在淘宝图片业务中的应用](https://blog.csdn.net/taobaojishu/article/details/110458820)
  - Client-side cache: Varnish
  - Cache coherence / invalidation
    - Writing policies
      - Write-through cache: data is written to cache & DB at the same time, this minimizes the risk of data loss, but higher latency for write 
      - Write-around cache: data is written directly to DB, this reduces flooded write operations, but creates a cache miss
      - Write-back cache: data is written to cache alone, this results in low latency & high throughput, but comes with the risk of data loss in case of crash
    - Distributed lock manager (DLM)
  - [Cache replacement policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)

- References
  - Comparisons
    - [MongoDB vs MySQL](https://www.simform.com/mongodb-vs-mysql-databases)
    - [MongoDB vs Elasticsearch](https://mindmajix.com/mongodb-vs-elasticsearch)
    - [Inmon vs Kimball](https://www.zentut.com/data-warehouse/kimball-and-inmon-data-warehouse-architectures/)
  - Log
    - Mysql (binlog): replication / synchronization, data recovery
    - MongoDB (oplog)
  - How to Choose: Integration, Scaling, Support(security, budget, etc.), Simplicity
    - CAP theorem: Consistency, Availability, Partition tolerance
      - CP vs AP (BASE: Basically Available Soft state Eventual consistency)
  - Big data
    - Spark SQL
      - Broadcast join
    - Dask (Pandas)
  - Applications
    - [Amazon Redshift DISTKEY and SORTKEY](https://www.flydata.com/blog/amazon-redshift-distkey-and-sortkey/)
    - Clustered index: [Clustered table in BigQuery](https://cloud.google.com/bigquery/docs/clustered-tables)

### Backend

- Design patterns
  - Object oriented programming (OOP): Polymorphism
  - Creational Patterns: Factory, Singleton
  - Structural Patterns: Decorator, Adapter, Facade, Composite, Proxy
  - Behavioral Patterns: Observer, Command, Template, Iterator, State
  - J2EE Patterns: Compound (MVC)
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
      - Spring Data JPA (Spring Data REST)
    - Spring Cloud
    - Projects: [link](https://spring.io/projects)
  - Server Content
    - Servlet
      - Life cycle: init → service (request & response) → destroy
      - Container: Apache Tomcat (services provided by the Servlet container)
      - Info & Config
    - Session management in HTTP
    - Listener (Event): changing the state of an object
    - Filter (authentication, log, ...)

- Go ([pointer](https://www.runoob.com/go/go-pointers.html), [channel](https://www.runoob.com/w3cnote/go-channel-intro.html))

- Python
  - [cProfile](https://docs.python.org/3/library/profile.html)
  - [Packaging Projects](https://packaging.python.org/tutorials/packaging-projects/)
  - Concurrent and parallel programming: Celery, Pyro5, RPyC, mpi4py, PyCUDA

- Node.js
  - Express
  - [ES6 教程](https://wangdoc.com/es6/)

### Frontend

- Knowledge
  - WWW standards
    - CSS ([animation](https://animate.style/))
    - DOM
    - HTML
    - SVG
    - XML
  - Web
    - Vue.js
      - Vue Instance - Virtual DOM - DOM
      - VueResource, VueRouter, Vuex
        - MVVM: two-way data bindings([双向绑定](https://www.liaoxuefeng.com/wiki/1022910821149312/1109527162256416))
      - Developer Tools: Vue.js devtools
  - Mobile
    - SwiftUI
    - WeChat Mini Program
  - Desktop
    - Electron
  - Website audit
  - UI design (e.g. Figma, Adobe XD)
  - UI component: Bootstrap, Ant Design
  - Applications
    - Rich Text Editor
    - BPMN: Business Process Model and Notation (e.g. Rappid)

### System design

- Distributed System Trade-offs
  - Performance vs Scalability
  - Throughput vs Latency
  - Availability vs Consistency

- Performance
  - If the **system goes slow**: scalability, performance
  - Testing
    - Throughput = # tasks / time
      - hps, tps, qps: number of HTTP requests/Transactions/Queries per second
    - Latency = time / task
    - Number of concurrent sessions/users (Concurrency = throughput * latency)
    - Internal metrics: CPU (interrupts per second), Memory, Network (bandwidth, connection state), Disk I/O, etc.
  - Optimization
    - Global Data Center (multi-data center architecture)
    - Hardware
    - Operating system (Linux: transparent huge page)
    - JVM
    - Infrastructure: web container, database connection pooling, MVC framework
    - Architecture: cache (read-through vs cache-aside), message broker, clustered architecture
    - Programming: algorithms, data structure, design pattern, asynchronous I/O

- Availability
  - If the **system goes down**: resiliency (SPOF: single point of failure), availability, stability
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

- WBS (Work breakdown structure)
  - Problem statements: RfQ (Request for quotation), SoW (Statement of work)
  - PoC (Proof of concept)
  - **User story** & Feature list
    - An end user going through a domain-level process to achieve some valuable outcome
    - Who, What, Why, Acceptance Criteria (AC)
  - Architecture design
  - Coding, testing, release
  - Maintenance & Iterative and incremental development

- Development Approach
  - TDD (Test driven): state desired outcome as a test
  - BDD (Behavior driven): base tests on natural language descriptions of business functionality
  - FDD (Feature driven)
  - DDD (Domain driven)
    - Bounded Context
    - Reactive model (publish subscribe model, vs: Declarative model)
      - Entities communication
      - Message broker
    - Event storming: design a system that models the structure and flow of activities within the business itself

- Code Review
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
    - Conway's law
  - Scrum: Transparency, Inspection, Adaptation
    - Scrum master
  - Waterfall: System and software requirements → Analysis → Design → Coding → Testing → Operations
  - Project Management Committee ([PMC](https://www.apache.org/foundation/how-it-works.html))

- Team Management
  - [The Guerrilla Guide to Interviewing](https://www.joelonsoftware.com/2006/10/25/the-guerrilla-guide-to-interviewing-version-30/)
