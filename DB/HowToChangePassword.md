### 查看缺省密码
```
$ cat /var/log/mysqld.log | grep "temporary password"
```
返回结果
```
2017-06-26T04:28:05.537965Z 1 [Note] A temporary password is generated for root@localhost:

 ca!wB/i+l7eL
```
### 用缺省密码登陆
```
mysql -uroot -pca\!wB\/i+l7eL
```
### 修改密码
```
ALTER USER USER() IDENTIFIED BY 'Pas$word123'
```

