Docker 可以通过读取 [Dockerfile](https://docs.docker.com/engine/reference/builder/) 中的指令自动构建镜像。 *Dockerfile* 是一个文本文档，其中包含用户可以在命令行上调用来组装映像的所有命令。

Dockerfile 中的以下指令列表支持环境变量：

- `ADD`
- `COPY`
- `ENV`
- `EXPOSE`
- `FORM`
- `LABEL`
- `STOPSIGNAL`
- `USER`
- `VOLUME`
- `WORKDIR`
- `ONBUILD`

```Dockerfile
FROM busybox
ENV FOO=/bar
WORKDIR ${FOO}   # WORKDIR /bar
ADD . $FOO       # ADD . /bar
COPY \$FOO /quux # COPY $FOO /quux
```

`\` 转义符和换行符
`ENV` 环境变量
## [.dockerignore file](https://docs.docker.com/engine/reference/builder/#dockerignore-file)


