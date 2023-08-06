[`ResizeObserver`](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver) 接口监视 `Element` 内容盒或边框盒，也包括 `SVGElement` 边界的尺寸变化。

> **备注：** 内容盒是盒模型放置内容的部分，这意味着边框盒减去内边距和边框的宽度就是内容盒。边框盒包含内容、内边距和边框。

# [构造函数](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver#构造函数)

[`ResizeObserver()`](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver/ResizeObserver "ResizeObserver()")

创建并返回一个新的 `ResizeObserver` 对象。

## [属性](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver#属性)

无。

## [方法](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver#方法)

[`ResizeObserver.disconnect()`](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver/disconnect)

取消特定观察者目标上所有对 [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 的监听。

[`ResizeObserver.observe()`](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver/observe)

开始对指定 [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 的监听。

[`ResizeObserver.unobserve()`](https://developer.mozilla.org/zh-CN/docs/Web/API/ResizeObserver/unobserve)

结束对指定 [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 的监听。

## 例子

```js
const domWrap = document.getElementById('test');
const checkbox = document.getElemetById('check');
const resizeObserver = new ResizeObserver((entries, observer) => {
  // 每当 domWrap 宽度或高度（尺寸盒子尺寸变化时调用）
  console.log(entries, observer);
  // observer 时对自身的引用，可以在达到某个特定条件下，取消对观察者的监听
});

resizeObserver.observer(domWrap); // 开始对 domWrap 元素的监听
checkbox.addEventListener('onchange', () => {
  if (checkbox.checked) {
    resizeObserver.observer(domWrap); 
  } else {
    resizeObserver.unobserver(domWrap); // 取消对 domWrap 元素的监听
  }
});
```