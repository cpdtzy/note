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

初始内容为 `*` 时，表示任何值相等于非必填

> **以上属性均为 必填属性，如果有属性没有，那么整个 @property 将失效**

## JS 语法

```js
window.CSS.registerProperty({
  name: "--item-color",
  syntax: "<color>",
  inherits: false,
  initialValue: "aqua",
});
```

使用 js 注册后，也同样可以直接在 css 中使用。