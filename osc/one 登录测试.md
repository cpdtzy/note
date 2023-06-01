> osc 开通 gitee-one 空间权限，通过 gitee-one 获取代码仓库的代码，根据 package.json 进行 npm install 依赖

1. 通过企业邮箱进行 VPN 账号申请
2. 获取 .OPEN 文件以便 VPN 跨域
3. 运行 cookie-proxy
4. 通过 [OPENVPN](https://openvpn.net/) 打开 Profiles 文件，开启跨域
5. 打开域名 [ningbo-one](http://ningbo.bank.dev.gitee.work/login)
7. 通过账号：ningbo-admin  密码：admin2020 进行登录
8. 获取对应的 cookie，copy pasta 去 cookie-proxy 进行登录

### 打包 one 文件并 deploy

> 在项目目录下进行 npm build 打包，打包文件会在项目文件根目录生产 build 文件夹，打包后的产物在这个文件夹里

1. 有个压缩文件 ningbo-poc.zip 文件，进行解压
2. build 里的文件内容，替换 ningbo-poc 文件夹中 `/html/fas/assets` 里的所有文件，和 `html/fas/` 下的 *html* 文件
3. 在 `html` 目录下开启 docker 并执行 `sh bale.sh` 指令进行打包
4. 打包后的产物是 `poc-one.*.tgz` 打包文件
5. *copy* 去虚拟机中，进行 docker 文件上传并进行 k8s 镜像文件替换



