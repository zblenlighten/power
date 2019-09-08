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

### Infrastructure

- Architecture
  - <s>Monolithic</s>
  - Microservice
    - Kubernetes
    - Docker
  - Serverless
    - AWS Lambda (Faas)
- API Gateway
- Service Function
  - Message broker
    - Kafka
    - ActiveMQ
  - Search engine
    - Elasticsearch (Solr)
      - Lucene (Inverted index)
      - Restful API (HTTP)
      - Distributed (Master - slave)
      - ELK: logs
- Distributed
  - Zookeeper
  - Data Replicate Center
- DevOps
  - CI/CD
    - Jenkins
  - Version control
- <s>Tools</s>
  - Swagger
  - WireMock
  - Google Analysis

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
  - Rich Text Editor (Froala)
  - SVG (Rappid)

### System design

- trade-offs:
  - Performance vs scalability
  - Latency vs throughput
  - Availability vs consistency
    - CAP: Consistency, Availability, Partition tolerance

- Case:

  1. 网络爬虫
      - BFS & DFS (Overhead time) by Scheduler (Priorirt queue存储已经发现但是尚未下载的URL)
      - 页面分析和URL提取 (解析Javascript)
      - URL表 (上千台服务器时：明确每台下载服务器的分工，向散列表发送询问判断URL是否下载)

  //TODO
