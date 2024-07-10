能够注册自定义属性，甚至可以在 animation 中进行 [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@property)

## 语法

```css
@property --property-name {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

### `syntax` 语法属性

语法属性有：`<length>`, `<number>`, `<percentage>`, `<length-percentage>`, `<color>`, `<image>`, `<url>`, `<integer>`, `<angle>`, `<time>`, `<resolution>`, `<transform-function>`, or `<custom-ident>` 或者一些数据列表类型和关键字类型

用 `|` 分割多个属性定义，`#` 表示预期的内容

### `inherits` 是否继承

### `initial-value` 初始内容

