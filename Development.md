# Knowledge Memo

## Contents

- [Practice](#practice)
- [Infrastructure](#infrastructure)
- [Database](#database)
- [Backend](#backend)
- [Frontend](#frontend)
- [System design](#system-design)

## Development

### Practice

- WBS: Work breakdown structure
  - Feature (list)
  - User story
    - What - Why - Acceptance Criteria (AC)
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
  - <s>Monolithic</s>
  - Microservice
    - Kubernetes
    - Docker
  - Serverless
    - AWS Lambda (FaaS)
- API Gateway
- Service Function
  - Message broker (Message queue)
    - Kafka
    - ActiveMQ
  - Search engine
    - Elasticsearch (Solr)
      - Lucene (Inverted index)
      - Restful API (HTTP)
      - Distributed (Master - slave)
  - Log monitoring
    - ELK: Elasticsearch, Logstash, Kibana
- Distributed
  - Zookeeper
  - Data Replicate Center
- DevOps
  - CI/CD
    - Jenkins
  - Version control
- <s>Tools</s>
  - Terraform (?)
  - Swagger
  - WireMock
  - Google Analysis
  - [Vim](http://www.ruanyifeng.com/blog/2018/09/vimrc.html)

### Database

- SQL DB
  - ORM: Object-relational mapping
  - <strong>Tuning</strong>
- Cache
  - Redis

### Backend

- Server Content
  - Static sites
    - CDN: Content delivery network
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
  - CSP: [Content Security Policy](http://www.ruanyifeng.com/blog/2016/09/csp.html)

### System design

- trade-offs:
  - Performance vs scalability
  - Latency vs throughput
  - Availability vs consistency
    - CAP: Consistency, Availability, Partition tolerance

- Case:

  1. Web Crawler
      - BFS & DFS (Overhead time) by Scheduler (Priority queue stores URLs that have been discovered but not yet downloaded)
      - Page analysis and URL extraction (parsing Javascript)
      - URL table (In the case of thousands of servers: 明确每台下载服务器的分工，向散列表发送询问判断URL是否下载)

  //TODO
