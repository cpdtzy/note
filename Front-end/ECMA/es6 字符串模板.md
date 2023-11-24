
ES6 字符串共有两种不同的形式模板

1. 一种是模板字面量形式
2. 一种是函数字面量

## 模板字面量

```javascript
let word = 'world';
let text = `Hello ${word}!`;

console.log(text);
```

## 函数字面量

```javascript
function foo(strinty, ...args) {
  console.log(strinty);
  console.log(args);
}

let world = 'world';
foo`Hello ${world}!`;

// ['Hello ', '!']
// ['world']
```

> 可用于字符串拼接，并对相对应的字符串进行处理