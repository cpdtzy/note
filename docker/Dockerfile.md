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

在 docker CLI 将上下文发送到 docker 守护进程之前，它会在上下文的根目录中查找名为 `.dockerignore` 的文件。如果此文件存在，CLI 会修改上下文以排除与其中的模式匹配的文件和目录。这有助于避免不必要地将大型或敏感文件和目录发送到守护程序，并可能使用 `ADD` 或 `COPY` 将它们添加到映像中。

```dockerignore
# comment
*/temp*
*/*/temp*
temp?
```

`#` 注释信息

|Rule|Behavior|
|---|---|
|`# comment`|Ignored.|
|`*/temp*`|Exclude files and directories whose names start with `temp` in any immediate subdirectory of the root. For example, the plain file `/somedir/temporary.txt` is excluded, as is the directory `/somedir/temp`.|
|`*/*/temp*`|Exclude files and directories starting with `temp` from any subdirectory that is two levels below the root. For example, `/somedir/subdir/temporary.txt` is excluded.|
|`temp?`|Exclude files and directories in the root directory whose names are a one-character extension of `temp`. For example, `/tempa` and `/tempb` are excluded.|

搜索是用的 Go's [filepath.Match](https://pkg.go.dev/path/filepath#Match) 规则。
以 ! 开头的行（感叹号）可用于排除例外。
以下是使用此机制的 .dockerignore 文件示例：

```dockerignore
*.md
!README.md
```

除了 `README.MD` 以外的所有 markdown 文件.

## [FROM](https://docs.docker.com/engine/reference/builder/#from)

```
FROM [--platform=<platform>] <image> [AS <name>]
```

or 

```
FROM [--platform=<platform>] <image>[:<tag>] [AS <name>]
```

or

```
FROM [--platform=<platform>] <image>[@<digest>] [AS <name>]
```

`FROM` 指令初始化一个新的构建阶段并为后续指令设置基本映像。因此，有效的 Dockerfile 必须以 `FROM` 指令开头。该 Image 可以是任何有效的图像 - 从公共存储库中 **pulling an image** 尤其容易开始。