# Tools

## EC2

### ssh connect EC2

- conection from local

  > cd ~  
cd .ssh  
chmod 600 Asama-key.pem  
cd ~  
ssh <a>ec2-user@52.194.239.159</a> -i Asama-key.pem  

- initial setting of EC2

  > sudo su  
yum install git  
git --version  
yum update && yum -y install zsh  
zsh --version  
yum install util-linux-user  
cat /etc/shells  
sudo chsh ec2-user  
/bin/zsh  
vim ~/.zshrc  
source ~/.zshrc

  [set theme](https://qiita.com/jesus_isao/items/f440d5980832f3628567)  

- [Mysql on EC2](https://www.linode.com/docs/databases/mysql/how-to-install-mysql-on-centos-7/)

  > yum install mysql mysql-devel  
wget <a>http://repo.mysql.com/</a>  
mysql-community-release-el7-5.noarch.rpm  
sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm  
yum update  
yum install mysql-server  
systemctl start mysql.service  

- connect from local (DBeaver)

  > mysql_upgrade  
service mysql status  
mysql  
CREATE USER 'root'@'{IP address}' IDENTIFIED BY '{password}';  
GRANT ALL PRIVILEGES ON \*.* TO 'root'@'{IP address}' WITH GRANT OPTION;  
FLUSH PRIVILEGES;  
SELECT Host, User, Password FROM mysql.user;  

  then connected  

- set go environment

  > yum install gcc
