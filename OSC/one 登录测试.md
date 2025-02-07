#osc 

> 开通 gitee-one 空间权限，通过 gitee-one 获取代码仓库的代码，根据 package.json 进行 npm install 依赖

1. 通过企业邮箱进行 VPN 账号申请
2. 获取 .OPEN 文件以便 VPN 跨域
3. 运行 cookie-proxy
4. 通过 [OPENVPN](https://openvpn.net/) 打开 Profiles 文件，开启跨域
5. 打开域名 [ningbo-one](http://ningbo.bank.dev.gitee.work/login)
7. 通过账号：ningbo-admin  密码：admin2020 进行登录
8. 获取对应的 cookie，copy pasta 去 cookie-proxy 进行登录

## 打包

one 通过 [流水线](https://osc.gitee.work/xly-poc/ONE/new-ipipe/pipelines/16754/history/1940298/stages/2699474/tasks/58205189?versions=497-1747950%2C979-1818381%2C1808-1940298&groupId=&viewId=ALL&projectUuid=&tabs=outputs) 那进行打包打出来的产物还要通过 docker pull 下来并生成产物
