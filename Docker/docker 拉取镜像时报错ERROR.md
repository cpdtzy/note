国内外环境有差，要找国内镜像地址

配置文件地址
```
C:\Users\用户名\.docker
```

文件名
daemon.json 文件

```json
{
  "registry-mirrors": [
   "http://hub-mirror.c.163.com",
   "https://docker.mirrors.ustc.edu.cn/"
],
  "insecure-registries": [],
  "debug": false,
  "experimental": false,
  "features": {
    "buildkit": true
  }
}
```