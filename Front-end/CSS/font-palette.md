[font-palette](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-palette) 使用字体其他的颜色属性（调色盘）。

## 语法

```css
/* 使用字体定义的调色板 */
font-palette: normal;

/* 使用用户定义的调色板 */
font-palette: --one;
```

## 值

`normal` 
	默认的颜色样式

`light` 
	指定字体中第一个与“light”匹配的调色板，并作用于当前字体。如果一个字体没有该元数据，则 `light` 值的表现等同于 `normal`。

`dark` 
	指定字体中第一个与“dark”匹配的调色板，并作用于当前字体。如果一个字体没有该元数据，则该值的表现等同于 `normal`。

`<palette-identifier>` 
	允许使用 [[@font-palette-values]] (en-US) @ 规则指定字体调色板的自定义值。

## 特性

- 是继承属性
- 初始值是 `normal`

## 使用方式

主要与 [[@font-palette-values]] 结合使用。