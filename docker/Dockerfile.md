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

环境变量将会替换整个指令中的每个变量使用的值。

```dockerfile
ENV abc=hello
ENV abc=bye def=$abc
ENV ghi=$abc
```

`def` 的值是 `hello`，而不是 `bye`，然而 `ghi` 的值就会变成 `bye`，因为它不是将 `abc` 设置为 `bye` 的一部分指令。
## [.dockerignore file](https://docs.docker.com/engine/reference/builder/#dockerignore-file)


