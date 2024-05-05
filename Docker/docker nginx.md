想要在服务器上使用 nginx 服务，服务器有个 docker 使用 docker 运行，通过 image 去创建 container（容器）。
我们可以通过 docker create 和 docker pull 来拉取 docker 对应的 nginx 镜像包，来安装我们需要的 nginx 的环境。

1. `docker pull nginx:latest` 拉取 ==docker nginx== 镜像包
```
REPOSITORY                TAG       IMAGE ID       CREATED         SIZE
nginx                     latest    eb4a57159180   6 weeks ago     187MB
```

下载完成后通过 `docker images` 显示以上信息

2. 运行 ==images==
```shell
$ docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]

docker run -d -p 8080:80 nginx
```
会通过 ==nginx== 镜像创建一个 ==nginx== 的容器，对应的端口映射为 8080（8080的端口映射为 `container` 容器的端口 80）。

3. 进入容器

`docker attach` 可以进入容器终端，但退出时会导致，`container` 停止运行.
使用 `docker exec` 并不会导致 `container` 停止运行。

```shell
docker exec -it [container] /bin/bash
```

4. 退出容器使用 `exit` ==container==，或按键 ==ctrl + c== 退出 `container` 时，`container` 仍然在后台运行。

### 其余辅助指令 

1. `docker cp` 负责从 container 中 copy 文件出来，或者 copy 文件进去
2. `nginx -t` 查看 nginx 配置文件路径，并且可以查看配置文件是否正确
3. 路径 
 - `/usr/share/nginx/html` 默认文件路径
 - `/etc/nginx/` 配置文件

#### 1. docker cp

```shell
docker cp /mnt/d/default.conf [container]:/etc/nginx/config.d
```
会把对应的 ==D盘== 中的文件 `default.conf` 上传至 `container` 对应的 `/etc/nginx/config.d` 文件夹下

#### 2. nginx -t
在 ==容器== 内部，通过指令 `nginx -t` 会测试你的 ==nginx== 配置文件是否配置正确

```shell
$ nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

#### 3. 映射 ==nginx== 目录

将nginx容器的配置日志资源等目录映射到本地主机目录下，需要在启动容器时，使用到 `-v` 命令，如：

```shell
docker run -d --name nginx \
-p 8080:80 \
-v /usr/nginx/html:/usr/share/nginx/html \
-v /usr/nginx/log:/var/log/nginx \
-v /usr/nginx/nginx.conf:/etc/nginx/nginx.conf \
nginx
```

在用 ==Docker== 配置 ==Nginx== 时，有两个主要的配置文件可以使用： `/etc/nginx/nginx.conf` 和 `/etc/nginx/conf.d/default.conf`。

#### 4. 打包运行的 ==container== 为 ==images==

通过指令 `docker commit` 可以打包 ==container== 去 ==images== 生成对应的镜像

```shell
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
```