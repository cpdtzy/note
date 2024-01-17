> Node Version Manager [github](https://github.com/nvm-sh/nvm#installing-and-updating)

## install

To **install** or **update** nvm, you should run the [install script](https://github.com/nvm-sh/nvm/blob/v0.39.7/install.sh). To do that, you may either download and run the script manually, or use the following cURL or Wget command:

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

## 安装版本

安装版本需要获取管理权限

```
nvm install 14.20.0
```

## 指令

获取版本
`nvm -v`

获取最新版本
```
nvm install latest
```

安装 lts 版本

```
nvm install lts
```

获取node 版本信息

```
nvm list available
```

![获取node版本](https://chinese.freecodecamp.org/news/content/images/2022/08/image-11.png)

安装特定版本

```
nvm install 14.20.0
```