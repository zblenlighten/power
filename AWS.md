# Devops memo

[A practical guide](https://github.com/open-guides/og-aws)

## Contents

- [CLI](#CLI-command-line-interface)
- [IMA](#IMA)
- [EC2](#EC2)
- [CodeCommit, Code build](#codeCommit-codeBuild)
- [Container](#Elastic-Kubernetes-Service-EKS-elastic-container-registry-ECR-elastic-container-service-ECS)
- [WAF, Shield](#WAF-Shield)
- [CloudFront](#CloudFront)
- [Route53](#Route53)
- [VPC](#VPC)
- [API Gateway, Elastic Load Balancing](#API-gateway-Elastic-Load-Balancing)
- [Lambda](#Lambda)
- [Batch](#Batch)
- [SES, SNS](#simple-email-service-SES-simple-notification-service-SNS)
- [CloudTrail](#CloudTrail)
- [CloudWatch](#CloudWatch)
- [S3](#S3)
- [Database](#RDS-DynamoDB-Quantum-Ledger-Database-QLDB)
- [Cache](#Redis-ElastiCache)
- [Amazon MQ](#Amazon-MQ)
- [Kinesis](#Kinesis)
- EMR

## CLI (Command Line Interface)

## IMA

&emsp; IAM enables you to control who can do what in your AWS account

## EC2

### ssh connect EC2 from local macbook

- launch a new instance on EC2

  > Amazon Linux 2 AMI (HVM), SSD Volume Type

  Settings: memory, VPC, disk, security group...  
  Then get <strong>key</strong> file (put in .ssh/).

- set <strong>security group</strong>

  Protocol, port Range, source(IP: {IP}/{8-32})...

- connect instance from local

  <pre><code>cd ~
  cd .ssh
  chmod 600 key.pem
  cd ~
  ssh ec2-user@{IPv4 Public IP} -i key.pem</code></pre>

- initial setting of EC2

  <pre><code>sudo su
  yum update
  yum install git
  git --version
  yum -y install zsh
  zsh
  yum install util-linux-user</code></pre>

  [set theme](https://qiita.com/jesus_isao/items/f440d5980832f3628567)

  <pre><code>vim ~/.zshrc
  export LC_ALL=C
  source ~/.zshrc
  chsh -s /bin/zsh
  echo $SHELL</code></pre>

  [why "LC_ALL=C"](http://tihiro.hatenablog.com/entry/2017/10/12/075555)

  alternative:
  <pre><code>cat /etc/shells
  sudo chsh ec2-user
  /bin/zsh</code></pre>

- Mysql on EC2

  [delete mysql in linux](https://help.cloud66.com/maestro/how-to-guides/databases/shells/uninstall-mysql.html)

  <pre><code>rpm -qa | grep -i "mysql"
  yum localinstall -y https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
  yum install -y mysql-community-server
  mysqld --version
  systemctl start mysqld.service
  systemctl enable mysqld.service</code></pre>

  [password setting](https://qiita.com/ymasaoka/items/7dc131dc98ba10a39854)

- connect from local (DBeaver)

  <pre><code>mysql_upgrade
  service mysqld status
  mysql -u root -p
  CREATE USER 'root'@'{IP}' IDENTIFIED BY '{password}';
  GRANT ALL PRIVILEGES ON *.* TO 'root'@'{IP}' WITH GRANT OPTION;
  FLUSH PRIVILEGES;
  SELECT Host, User, Password FROM mysql.user;</code></pre>

- set go environment (beego)

  <pre><code>yum install gcc</code></pre>

  1. install go
  2. <span style="color:Teal">edit go env GOPATH:</span>
  need to export GOENV_DISABLE_GOPATH=1 before eval "$(goenv init -)" [(reference)](https://github.com/syndbg/goenv/issues/72)
  3. then install beego and just run!

- install npm & yarn

  <pre><code>yum install -y gcc-c++ make
  yum install nodejs
  npm -v
  curl --silent --location https://dl.yarnpkg.com/rpm/yarn.repo | sudo tee /etc/yum.repos.d/yarn.repo
  rpm --import https://dl.yarnpkg.com/rpm/pubkey.gpg
  yum install yarn
  yarn --version
  </code></pre>

  [npm "hello world" (with express)](https://medium.com/@adnanrahic/hello-world-app-with-node-js-and-express-c1eb7cfa8a30)

## CodeCommit, CodeBuild

## Elastic Kubernetes Service (EKS), Elastic Container Registry (ECR), Elastic Container Service (ECS)

## WAF, Shield

## CloudFront

&emsp;  mitigation

## Route53

&emsp; domain name management and router allocation

## VPC

1. serverless(edit yml file) - vpc(check network of lambda after deploy) - API Gateway(test)
2. connect the private network by putty ppk file from EC2

## API Gateway, Elastic Load Balancing

1. APIs: resources (to find which lambda)
2. APIs - stages - invoke url(endpoint)

## Lambda

&emsp; Serverless: Functions - trigger (connect DB)

## Batch

1. job queues:
2. batch - code build - ECR(docker) - Jenkins(pipeline & shell script)

## Simple Email Service (SES), Simple Notification Service (SNS)

## CloudTrail

&emsp; Trails, data events - S3

## CloudWatch

&emsp; Logs (also enter from lambda)

## S3

&emsp; bucket

## RDS, DynamoDB, Quantum Ledger Database (QLDB)

1. clusters: Cluster endpoint(server) (database of RDS)
2. instance: (under the cluster) security group - inbound (like firewall)
3. snapshot: recovery

## Redis, ElastiCache

## Amazon MQ

## Kinesis

&emsp; kafka
