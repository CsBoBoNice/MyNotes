安装mysql

sudo apt update

sudo apt install mariadb-server

sudo mysql -V

sudo mysql_secure_installation

安装提示选择，设置root密码等

卸载MySQL
1、停止服务：sudo service mysql stop

2、卸载MySQL：
	（1）sudo apt-get --purge remove mysql-server
	（2）sudo apt-get --purge remove mysql-client
	（3）sudo apt-get --purge remove mysql-common

3、清理残余
	（1）sudo apt-get autoremove
	（2）sudo apt-get autoclean
	（3）rm /etc/mysql/ -R
	（4）rm /var/lib/mysql/ -R


登陆 sudo mysql -u root -p

创建数据库 CREATE DATABASE exampledb;

创建本地用户

CREATE USER 'localuser'@'localhost' IDENTIFIED BY 'p1048576q';

远程可访问用户

CREATE USER 'remoteuser'@'%' IDENTIFIED BY 'p1048576q';

设置权限 *.*代表所有数据库的所有表

GRANT ALL PRIVILEGES ON *.* TO 'localuser'@'localhost';

GRANT ALL PRIVILEGES ON *.* TO 'remoteuser'@'%'; 
远程用户让他可以远程访问数据库

FLUSH PRIVILEGES;

6 重启数据库生效

sudo systemctl restart mysql


安装java 8

https://www.oracle.com/java/technologies/javase-jdk8-downloads.html

tar -zxvf  jdk-8u261-linux-arm64-vfp-hflt.tar.gz
sudo cp -r jdk1.8.0_371/ /usr/local/lib/
cd /usr/local/lib/
sudo mv jdk1.8.0_371/ jdk1.8

## 在文本末尾添加

sudo sed -i '$a \SOFT_HOME=/usr/local/lib' /etc/profile
sudo sed -i '$a \JAVA_HOME=$SOFT_HOME/jdk1.8' /etc/profile
sudo sed -i '$a \JRE_HOME=$SOFT_HOME/jdk1.8/jre' /etc/profile
sudo sed -i '$a \CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib' /etc/profile
sudo sed -i '$a \PATH=$JAVA_HOME/bin:$PATH' /etc/profile
sudo sed -i '$a \export SOFT_HOME PATH JAVA_HOME CLASS_PATH' /etc/profile
## 应用文件
source /etc/profile
## 查看环境
java -version



安装tomcat 8.5

https://tomcat.apache.org/download-80.cgi

tar -zxvf apache-tomcat-8.5.89.tar.gz
cd apache-tomcat-8.5.89/bin/
./startup.sh

http://localhost:8080/

cd apache-tomcat-8.5.63/bin/
#启动
./startup.sh
#关闭
./shutdown.sh

#查看tomcat进程信息
ps -ef | grep tomcat
#强制关闭某个进程
kill -9 [进程ID]
