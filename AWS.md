# Devops memo

## AWS EC2

## ssh connect EC2 from local macbook

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

  1. run node.js
