[https://cloud.tencent.com/developer/article/2359685](https://cloud.tencent.com/developer/article/2359685)

1. `pull wordpress`
2. `pull mysql`
3. `run wordpress and mysql`
4. config `wordpress`

## 1. pull wordpress

```
docker pull wordpress
```

## 2. pull mysql

```
docker pull mysql
```

## 3. run wordpress and mysql

```shell

// 映射80端口出来，对应本地的8088端口
docker run -d --name wordpress -p 8088:80 wordpress 

// 运行 mysql & 设置 root 密码为 123456
docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=123456 mysql

// 查看 mysql 容器的网络 ip 地址
docker inspect --format '{{.NetworkSettings.IPAddress}}' mysql
```