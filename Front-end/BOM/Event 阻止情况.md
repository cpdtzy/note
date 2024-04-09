#Bom  #event

当前有3种事件监听的属性，来对 event 事件进行干预

1. [e.stopImmediatePropagation](https://developer.mozilla.org/zh-CN/docs/Web/API/Event/stopImmediatePropagation) 同类型同元素的事件类型，事件触发后，之后的其他监听不会调用
2. [e.preventDefault](https://developer.mozilla.org/zh-CN/docs/Web/API/Event/preventDefault) 取消事件的默认行为
3. [stopPropagation](https://developer.mozilla.org/zh-CN/docs/Web/API/Event/stopPropagation) 阻止 `event` 事件冒泡和捕获行为，阻止事件的进一步传播

