
> node.js plugin 可以在调用 node 运行文件时，弹出内容，获取文件所需参数 [NPM](https://www.npmjs.com/package/prompt)


## install

```shell
npm install prompt -D
npm install prompt --save
npm install prompt --save-dev
```

## 基础用法

简单的使用 prompt 库。
  ```js
  var prompt = require('prompt');

  //
  // Start the prompt
  //
  prompt.start();

  //
  // Get two properties from the user: username and email
  //
  prompt.get(['username', 'email'], function (err, result) {
    //
    // Log the results.
    //
    console.log('Command-line input received:');
    console.log('  username: ' + result.username);
    console.log('  email: ' + result.email);
  });
```

## method

### start

```js
const prompt = require('prompt');

prompt.start();
```

开始进行方法使用

### get

```js
const prompt = require('prompt');

prompt.start();

prompt.get(['username', 'email'], function (err, result) {
    //
    // Log the results.
    //
    console.log('Command-line input received:');
    console.log('  username: ' + result.username);
    console.log('  email: ' + result.email);
  });
```

out

```shell
$ node examples/simple-prompt.js
  prompt: username: some-user
  prompt: email: some-user@some-place.org
  Command-line input received:
    username: some-user
    email: some-user@some-place.org
```

