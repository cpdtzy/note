#osc 

> 开通 gitee-one 空间权限，通过 gitee-one 获取代码仓库的代码，根据 package.json 进行 npm install 依赖

1. 通过企业邮箱进行 VPN 账号申请
2. 获取 .OPEN 文件以便 VPN 跨域
3. 通过 [OPENVPN](https://openvpn.net/) 打开 Profiles 文件，开启跨域
4. 打开域名 [nbcb-dev](http://nbcb-dev.gitee.work/login)
5. 通过账号：osc-admin  密码：admin2020 进行登录
6. 获取对应的 cookie，copy pasta 去 `src/setupProxy.js` 进行替换登录

## 打包

one 通过 [流水线](https://osc.gitee.work/xly-poc/ONE/new-ipipe/pipelines/16754/history/1940298/stages/2699474/tasks/58205189?versions=497-1747950%2C979-1818381%2C1808-1940298&groupId=&viewId=ALL&projectUuid=&tabs=outputs) 那进行打包打出来的产物还要通过 docker pull 下来并生成产物
导出产物 `docker save -o xxx.tar images`

### 流水线配置

| **代码库**                        | **分支名**          |
| ------------------------------ | ---------------- |
| `gitee-one-front`              | 选对应分支            |
| `ad-adapter-front`             | `release/ningbo` |
| `gitee-one-front-docker-build` | `master`         |
| `theme-fronted`                | `FB_ningbo_poc`  |

## 本地调试

src/setupProxy.js 修改里面的 cookie 来进行代理操作