Shadow DOM API 的 **`ShadowRoot`** 接口是一个 DOM 子树的根节点，它与文档的主 DOM 树分开渲染。
你可以通过使用一个元素的 [`Element.shadowRoot`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/shadowRoot) 属性来检索它的参考，假设它是由 [`Element.attachShadow()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/attachShadow) 创建的并使 `mode` 设置为 `open`.

Note: 可以通过 `Element.attachShadow()` 来生成一个元素的 `ShadowRoot`