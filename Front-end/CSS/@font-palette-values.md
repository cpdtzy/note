[@font-palette-values](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-palette-values) 允许你自定义字体的默认属性，通过 [[font-palette]] 来使用。

[兼容性](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-palette-values#browser_compatibility)

## 语法

```css
@font-palette-values --identifier {
  font-family: Bixa;
}
.my-class {
  font-palette: --identifier;
}
```

## 属性

`font-family` 字体名称

`base-palette` 基础的调色名称

`override-colors` 覆盖基本颜色

## 例子

```css
@import url(https://fonts.googleapis.com/css2?family=Bungee+Spice);
p {
  font-family: "Bungee Spice";
  font-size: 2rem;
}
@font-palette-values --Alternate {
  font-family: "Bungee Spice";
  override-colors:
    0 #00ffbb,
    1 #007744;
}
.alternate {
  font-palette: --Alternate;
}
```



