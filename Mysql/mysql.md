[mysql 教程](https://www.runoob.com/mysql/mysql-connection.html)

1. `mysql -u root -p` 登录数据库
2. `show databases;` 查看多少个数据库
3. `create databsase xxx` 创建库

## test 数据库 地址是否通的

`telnet xxx port`

```
telnet xxx port
telnet 192.168.3.4 3123
```

表示成功

```
Trying 192.168.3.4...
Connected to 192.168.3.4.
Escape character is '^]'.
Connection closed by foreign host.
```