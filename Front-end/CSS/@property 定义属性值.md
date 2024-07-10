能够注册自定义属性，甚至可以在 animation 中进行

## 语法

```css
@property --property-name {
  syntax: "<color>";
  inherits: false;
  initial-value: #c0ffee;
}
```

### syntax 语法属性

`<length>`, `<number>`, `<percentage>`, `<length-percentage>`, `<color>`, `<image>`, `<url>`, `<integer>`, `<angle>`, `<time>`, `<resolution>`, `<transform-function>`, or `<custom-ident>`