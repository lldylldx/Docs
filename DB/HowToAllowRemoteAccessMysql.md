#### 登陆MySQL
```
mysql -uroot -p
```
#### 使用'mysql'数据库
```
use mysql
```
#### 查询'user'
```
select 
```
#### 更新'user'表
```
update user set host='%’ where host = ‘localhost’ and user=‘root’ 

flush privileges; 
```

#### 如果不能远程连接，请关闭防火墙尝试
CentOS 7.0默认使用的是firewall作为防火墙
```
systemctl stop firewalld.service 
 
systemctl disable firewalld.service
```

#### 卸载mysql
```
rpm -qa | grep mysql
rpm -qa | grep mariadb
rpm -e [软件标识]
```

#### 非多实例配置及启动
```
初始化 
 
mysql_install_db --user=centralight --datadir=/cl/data/mysql/percona3311
 
启动 
 
mysqld_safe --user=centralight --datadir=/cl/data/mysql --defaults-file=/cl/dist/conf/mysql/my.cnf 
```

#### 多实例配置及启动
```
chown -R centralight /cl/data/mysql/percona3311
 
mysql_install_db --datadir=/cl/data/mysql/percona3311 --user=centralight
```

#### 默认配置文件路径 /etc/my.cnf,修改成如下
```
[client] 
 
user = root 
 
password = 123 
 
# Here follows entries for some specific programs 
 
[mysqld_multi] 
 
mysqld = /usr/bin/mysqld_safe
 
mysqladmin = /usr/bin/mysqladmin
 
[mysqld3311] 
 
socket = /var/lib/mysql/mysql3311.sock 
 
port = 3311 
 
datadir = /cl/data/mysql/percona3311
 
pid-file = /var/lib/mysql/hostname.pid3311 
 
user = centralight 
 
skip-external-locking 
 
key_buffer_size = 16M 
 
max_allowed_packet = 1M 
 
table_open_cache = 64 
 
sort_buffer_size = 512K 
```

#### 启动
```
mysqld_multi --defaults-file=/etc/my.cnf --log=/cl/log/mysql/mysql.log start 3311
```

#### 报告状态
```
mysqld_multi --defaults-file=/etc/my.cnf report 3311
```

#### 设置密码
```
mysql> UPDATE user SET Password=password("123") WHERE user='root' and host='%’; 
 
mysql> flush privileges; 
```
#### MySQL的Java驱动
```
mysql-connector-java-5.1.46-bin.jar 点击打开链接
```
