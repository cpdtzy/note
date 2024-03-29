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

- `ARG` 是唯一能够在 `Dockerfile` 优先于 `FROM` 的指令。
- `FROM` 可以在单个 `Dockerfile` 中出现多次，以创建多个映像或使用一个构建阶段作为另一个构建阶段的依赖项。只需记下每个新 `FROM` 指令之前提交所输出的最后一个映像 ID。每个 `FROM` 指令都会清除先前指令创建的任何状态。
- （可选）可以通过将 `AS name` 添加到 `FROM` 指令来为新的构建阶段指定名称。该名称可以在后续的 `FROM` 和 `COPY --from=<name>` 指令中使用，以引用此阶段构建的镜像。
- `tag` 或 `digest` 是可选的。如果省略其中任何一个，构建器默认采用 `latest`。如果构建器找不到标记值，则会返回错误。

如果 `FROM` 引用多平台映像，可选的 `--platform` 标志可用于指定映像的平台。例如，`linux/amd64`、`linux/arm64` 或 `windows/amd64`。默认情况下，使用构建请求的目标平台。全局构建参数可以在此标志的值中使用，例如自动平台 `ARG` 允许您将阶段强制到本机构建平台 (`--platform=$BUILDPLATFORM`)，并使用它来交叉编译到内部的目标平台阶段。

### [了解 ARG 和 FROM 如何交互](https://docs.docker.com/engine/reference/builder/#understand-how-arg-and-from-interact)

`FROM` 指令支持由第一个 `FROM` 之前出现的任何 `ARG` 指令声明的变量。

```dockerfile
ARG  CODE_VERSION=latest
FROM base:${CODE_VERSION}
CMD  /code/run-app

FROM extras:${CODE_VERSION}
CMD  /code/run-extras
```

在 `FROM` 之前声明的 `ARG` 不在构建阶段，因此不能在 `FROM` 之后的任何指令中使用它。要使用在第一个 `FROM` 之前声明的 `ARG` 的默认值，请使用在构建阶段内不带值的 `ARG` 指令：

```Dockerfile
ARG VERSION=latest
FROM busybox:$VERSION
ARG VERSION
RUN echo $VERSION > image_version
```

## [RUN](https://docs.docker.com/engine/reference/builder/#run)

RUN 有两个形式：

1. `RUN <command>`（shell 形式，命令在 shell 中运行，默认情况下在 Linux 上为 /bin/sh -c 或在 Windows 上为 cmd /S /C）
2. `RUN ["executable", "param1", "param2"]`` (执行形式)

`RUN` 指令将在当前映像之上的新层中执行任何命令并提交结果。生成的提交映像将用于 `Dockerfile` 中的下一步。

在 *shell* 你可以用 `\` 在下一行继续写单行命令

```dockerfile
RUN /bin/bash -c 'source $HOME/.bashrc && \
echo $HOME'
```

或者运行一整行

```dockerfile
RUN /bin/bash -c 'source $HOME/.bashrc && echo $HOME'
```

要使用除“/bin/sh”之外的其他 shell，请使用 exec 形式传入所需的 shell。例如：

```dockerfile
RUN ["/bin/bash", "-c", "echo hello"]
```

> Note
> exec 形式被解析为 JSON 数组，这意味着您必须在单词周围使用双引号 (“)，而不是单引号 (‘)。

与 *shell* 形式不同，*exec* 形式不调用命令 shell。这意味着不会发生正常的 shell 处理。例如，`RUN [ "echo", "$HOME" ]` 不会对 `$HOME` 进行变量替换。如果您想要 shell 处理，则可以使用 shell 形式或直接执行 shell，例如：`RUN [ "sh", "-c", "echo $HOME" ]`。当使用 exec 形式并直接执行 shell 时，就像 shell 形式一样，是 shell 进行环境变量扩展，而不是 docker。
