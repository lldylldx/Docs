## Installing Percona Server for MySQL from Percona yum repository
1. Install the Percona repository
```
$ sudo yum install https://repo.percona.com/yum/percona-release-latest.noarch.rpm
```
2. Enable the repository:
```
$ sudo percona-release setup ps80
```
3. Install the packages
```
 $ sudo yum install percona-server-server
```
## Running Percona Server for MySQL
1. Starting the service
```
$ sudo service mysql start
```
2. Confirming that service is running
```
$ sudo service mysql status
```
3. Stopping the service
```
$ sudo service mysql stop
```
4. Restarting the service
```
$ sudo service mysql restart
```
## Uninstalling Percona Server for MySQL
1. Stop the Percona Server for MySQL service:
`service mysql stop`
2. Remove the packages:
```
$ sudo yum remove percona-server*
```
3. Remove the data and configuration files
```
rm -rf /var/lib/mysql
rm -f /etc/my.cnf
```
## Status Variables
```
SHOW ENGINE INNODB STATUS
```

## Install MariaDB repo
Copy and paste it into a file under /etc/yum.repos.d/ (we suggest naming the file MariaDB.repo or something similar). 

```
# MariaDB 10.0 CentOS repository list - created 2019-01-23 07:40 UTC
# http://downloads.mariadb.org/mariadb/repositories/
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.0/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
```
## How to uninstall MariaDB

```
 centos 7 卸载 mariadb 的正确命令

#列出所有被安装的rpm package
rpm -qa | grep mariadb

#卸载

rpm -e mariadb-libs-5.5.37-1.el7_0.x86_64

错误：依赖检测失败：
        libmysqlclient.so.18()(64bit) 被 (已安裝) postfix-2:2.10.1-6.el7.x86_64 需要
        libmysqlclient.so.18(libmysqlclient_18)(64bit) 被 (已安裝) postfix-2:2.10.1-6.el7.x86_64 需要

#强制卸载，因为没有--nodeps

　　rpm -e --nodeps mariadb-libs-5.5.37-1.el7_0.x86_64
 ```
