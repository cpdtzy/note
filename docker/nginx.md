想要在服务器上使用 nginx 服务，服务器有个 docker 使用 docker 运行，image 去创建 container（容器）。

1. `docker pull nginx:latest` 拉取 docker nginx 镜像包

运行 images
```shell
docker run 
```

进入容器

`docker attach` 可以进入容器终端，但退出时会导致，`container` 停止运行.
使用 `docker exec` 并不会导致 `container` 停止运行

```shell
docker exec -it [container] /bin/bash
```

exit container

可以输入 exit 或按键 ctrl + c 退出 container 时，container 仍然在后台运行。