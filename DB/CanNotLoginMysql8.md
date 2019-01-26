#### ERROR 1045 (28000): Access denied for user 'appadmin'@'localhost' (using password: YES)
```
其中有人说到“mysql.user 表中有另外一些记录产生了作用，最有可能的就是已经有一条''@localhost记录，就是用户名是空，主机字段是localhost的记录。”
```
```
grant select,insert,update,delete on test.* to appadmin@"localhost" identified by "password";
```
情况一解决方案：修改本地数据库密码
1. 情况一解决方案：修改本地数据库密码
首先登录MySQL
格式：
```
mysql> set password for 用户名@localhost = password('新密码');
```
例子：
```
mysql> set password for root@localhost = password('123');
```

2. 用mysqladmin
格式：
```
mysqladmin -u用户名 -p旧密码 password 新密码
```
例子：
```
mysqladmin -uroot -p123456 password 123
```

3. 用UPDATE直接编辑user表
首先登录MySQL
```
mysql> use mysql;
mysql> update user set password=password('123') where user='root' and host='localhost';
mysql> flush privileges;
```

4. 在忘记root密码的时候，可以这样

#### 远程授权
1. 先用localhost登录（进入MySQL）     
```
mysql -u root -p
Enter password:  （输入密码）
```
2. 执行授权命令
```
mysql> grant all privileges on *.* to root@'%' identified by '123';  （注意语句后面的“；”）
Query OK, 0 rows affected (0.07 sec)
```
3. 退出再试：  
```
mysql> quit
```
4. 再试登录：    
```
mysql -u root -h 192.168.194.142 -p
  Enter password:
 结果显示：Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
表示成功
```
#### 如何给用户授权

1. 给来自10.163.225.87的用户joe分配可对数据库vtdc的employee表进行select,insert,update,delete,create,drop等操作的权限，并设定口令为123。
```
mysql> grant select,insert,update,delete,create,drop on vtdc.employee to joe@10.163.225.87 identified by ‘123′;
```
2. 给来自10.163.225.87的用户joe分配可对数据库vtdc所有表进行所有操作的权限，并设定口令为123。
```
mysql> grant all privileges on vtdc.* to joe@10.163.225.87 identified by ‘123′;
```

3. 给来自10.163.225.87的用户joe分配可对数据库vtdc所有表进行所有操作的权限，并设定口令为123。
```
mysql> grant all privileges on *.* to joe@10.163.225.87 identified by ‘123′;
```

4. 给来自10.163.225.87的用户joe分配可对数据库vtdc所有表进行所有操作的权限，并设定口令为123。
```
mysql> grant all privileges on *.* to joe@localhost identified by ‘123′;
```
#####################################################################
1. 停止mysql数据库
/etc/init.d/mysqld stop

2. 执行如下命令
mysqld_safe --user=mysql --skip-grant-tables --skip-networking &

3. 使用root登录mysql数据库
mysql -u root mysql

4. 更新root密码
mysql> UPDATE user SET Password=PASSWORD('newpassword') where USER='root';
#最新版MySQL请采用如下SQL：
mysql> UPDATE user SET authentication_string=PASSWORD('newpassword') where USER='root';

5. 刷新权限
mysql> FLUSH PRIVILEGES;

6. 退出mysql
mysql> quit

7. 重启mysql
/etc/init.d/mysqld restart

8. 使用root用户重新登录mysql
mysql -uroot -p
Enter password: <输入新设的密码newpassword>

#### 另一种ssh登陆的方法
```
（1）SSH登录root管理员账户

（2）登录MySql

# mysql -u root -p
Enter password:
（3）执行授权命令

mysql> grant all privileges on *.* to root@'localhost' identified by '密码';
mysql> flush privileges;
或

mysql> grant all privileges on *.* to root@'%' identified by '密码';
mysql> flush privileges;
（4）退出再试

mysql> quit
Bye
（5）再次登录

然后，问题就解决了~
```
#### 修改my.cnf, 绕过密码输入
```
# vi /etc/my.cnf

[mysqld]
default_authentication_plugin = mysql_native_password
```
#### mysql slave 复制冲突的解决

监控发现 mysql slave 延迟了不少，登陆mysql slave 查看复制状态
```
mysql> show slave status\G
```
会有类似的错误提示 Slave:Error “Duplicate entry ‘1’ for key 1” on query…..

再查看master 的 status，验证下
```
mysql> show master status;
```
在 mysql slave 上设置
```
mysql> stop slave;
mysql> set global sql_slave_skip_counter=1;
mysql> start slave;
```
如果仍然提示错误，重复上面的步骤

[有用的链接1:](https://blog.csdn.net/lhl1124281072/article/details/80277163)
