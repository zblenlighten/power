# Devops memo

## AWS EC2

## ssh connect EC2 from local macbook

- launch a new instance on EC2:  
  <code>Amazon Linux 2 AMI (HVM), SSD Volume Type</code>

  Settings: memory, VPC, disk, security group...  
  Then get <strong>key</strong> file (put in .ssh/).

- connect instance from local

  > cd ~  
cd .ssh  
chmod 600 key.pem  
cd ~  
ssh <a>ec2-user@{IPv4 Public IP}</a> -i key.pem  

- initial setting of EC2

  > sudo su  
yum update  
yum install git  
git --version  
yum -y install zsh  
zsh  
yum install util-linux-user  

  [set theme](https://qiita.com/jesus_isao/items/f440d5980832f3628567)  

  > vim ~/.zshrc  
export LC_ALL=C  ([why](http://tihiro.hatenablog.com/entry/2017/10/12/075555))  
source ~/.zshrc  
chsh -s /bin/zsh  
echo $SHELL  

  alternative
  > cat /etc/shells  
sudo chsh ec2-user  
/bin/zsh  

- Mysql on EC2  

  [delete mysql in linux](https://help.cloud66.com/maestro/how-to-guides/databases/shells/uninstall-mysql.html)

  > rpm -qa | grep -i "mysql"  
yum localinstall -y <a>https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm</a>  
yum install -y mysql-community-server  
mysqld --version  
systemctl start mysqld.service  
systemctl enable mysqld.service  

  [password setting](https://qiita.com/ymasaoka/items/7dc131dc98ba10a39854)  

- connect from local (DBeaver)

  > mysql_upgrade  
service mysqld status  
mysql -u root -p  
CREATE USER 'root'@'{IP}' IDENTIFIED BY '{password}';  
GRANT ALL PRIVILEGES ON \*.* TO 'root'@'{IP}' WITH GRANT OPTION;  
FLUSH PRIVILEGES;  
SELECT Host, User, Password FROM mysql.user;  

- set go environment

  > yum install gcc  

  install go and <span style="color:Teal">edit go env GOPATH:</span>  
  > need to export GOENV_DISABLE_GOPATH=1 before eval "$(goenv init -)" [(reference)](https://github.com/syndbg/goenv/issues/72)

  then install beego and just run!
