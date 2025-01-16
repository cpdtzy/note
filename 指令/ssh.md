---
tags:
  - SSH
日期: 2025-01-16
描述: SSH 链接可以省略，使用账号密码，直接进行登录。
---
## config 文件

有两个路径
1. 用户配置文件 (~/.ssh/config)
2. 系统配置文件 (/etc/ssh/ssh_config)

### Host 

标识的配置。
`ssh`配置项参数值可以使用通配符：`*`代表0～n个非空白字符，`?`代表一个非空白字符，`!`表示例外通配。

### Hostname

指定远程主机名，可以直接使用数字IP地址。如果主机名中包含 ‘%h’ ，则实际使用时会被命令行中的主机名替换。

### IdentityFile

指定密钥认证使用的私钥文件路径。默认为 ~/.ssh/id_dsa, ~/.ssh/id_ecdsa, ~/.ssh/id_ed25519 或 ~/.ssh/id_rsa 中的一个。文件名称可以使用以下转义符：

```ruby
'%d' 本地用户目录
'%u' 本地用户名称
'%l' 本地主机名
'%h' 远程主机名
'%r' 远程用户名
```

### 例子

``` ruby
$ vim ~/.ssh/config
Host sshtest
    HostName ssh.test.com
    User user
    Port 2200
    IdentityFile ~/.ssh/id_rsa_test

Host ssttest2
    HostName ssh.test2.com
    User user2
    Port 2345
    IdentityFile ~/.ssh/id_rsa_test2
```

### Port

指定远程主机端口号，默认为 22 。

### User

指定登录用户名。


## 根据私钥找回公钥

```ruby
 ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
```

注意这样生成的公钥是没有注释的，一般在后面补上 空格+用户名@主机名 更好。