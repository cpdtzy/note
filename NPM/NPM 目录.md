## Init

`npm init` 创建 `package.json` 文件
可以自定义 `npm init` 初始化的问题，通过文件`.npm-init.js` 可以自定义问题

```shell
module.exports = prompt("what's your favorite flavor of ice cream, buddy?", "I LIKE THEM ALL");

module.exports = {
  customField: 'Example custom field',
  otherCustomField: 'This example field is really cool'
}
```

具体关于 `npm init` 自定义问题的用法 [init-package-json GitHub repository](https://github.com/npm/init-package-json).
[配置的格式](https://github.com/npm/promzard)
### 创建默认的 `package.json`

使用 `npm init` command with the `--yes` or `-y` flag. 

```shell
npm init --yes
```

#### 当前文件夹创建 `package.json` 的默认值

- `name`: 文件夹的名称
- `version`: always `1.0.0`
- `description`: info from the README, or an empty string `""`
- `scripts`: by default creates an empty `test` script
- `keywords`: empty
- `author`: empty
- `license`: [`ISC`](https://opensource.org/licenses/ISC)
- `bugs`: information from the current directory, if present
- `homepage`: information from the current directory, if present

#### Setting config options for the init command

```shell
> npm set init-author-email "example-user@example.com"
> npm set init-author-name "example_user"
> npm set init-license "MIT"
```

## 插件包发布

- [[发布插件库]]
- [[弃用插件包]]

## Plugins

1. [[express]]
2. [[prompt]]