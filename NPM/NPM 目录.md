## Init

`npm init` 创建 `package.json` 文件
可以自定义 `npm init` 初始化的问题，通过文件`.npm-init.js` 可以自定义问题

```node
module.exports = prompt("what's your favorite flavor of ice cream, buddy?", "I LIKE THEM ALL");

module.exports = {
  customField: 'Example custom field',
  otherCustomField: 'This example field is really cool'
}
```

具体关于 `npm init` 自定义问题的用法 [init-package-json GitHub repository](https://github.com/npm/init-package-json).

## 插件包发布

- [[发布插件库]]
- [[弃用插件包]]

## Plugins

1. [[express]]
2. [[prompt]]