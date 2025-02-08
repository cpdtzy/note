
> [docker o命令行指令](https://docs.docker.com/engine/reference/commandline/rmi/)

## Docker run

`--detach` or `-d` 分离模式
`--publish` or `-p` 端口映射 `8080:80` 8080 是外部端口 80 为 container 端口
`-i` 
`-t`
`-v` 

```shell
docker run -d -p 8080:80 [IMAGE]
```

## Docker rmi

移除一个或多个 image.

```shell
 docker rmi [OPTIONS] IMAGE [IMAGE...]
```

Refer to the [options section](https://docs.docker.com/engine/reference/commandline/rmi/#options) for an overview of available [`OPTIONS`](https://docs.docker.com/engine/reference/commandline/rmi/#options) for this command.

## Docker stop

停止容器.

```shell
docker stop [container]
```

## Docker commit

通过 container 创建一个 Image 镜像

```shell
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
```

## 查看 container IP

```
docker inspect --format '{{ .NetworkSettings.IPAddress }}' [container-name]
```

`[container-name]` - 容器名称