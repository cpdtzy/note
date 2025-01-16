## 根据私钥找回公钥

```ruby
 ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
```

注意这样生成的公钥是没有注释的，一般在后面补上 空格+用户名@主机名 更好。