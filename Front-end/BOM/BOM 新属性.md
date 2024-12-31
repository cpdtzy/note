
1. [URL](https://developer.mozilla.org/en-US/docs/Web/API/URL#constructor)  创建 `URL` 对象实例

## DOM3 Events

1. [MutationObserver](https://developer.mozilla.org/zh-CN/docs/Web/API/MutationObserver) 接口提供了监视对 `DOM` 树所做更改的能力。
2. [[ResizeObserver]] 接口监视 `Element` 内容盒或边框盒 尺寸变化。
3. [IntersectionObserver](https://developer.mozilla.org/zh-CN/docs/Web/API/IntersectionObserver) 提供了一种异步观察目标元素与其祖先元素或顶级文档[视口](https://developer.mozilla.org/zh-CN/docs/Glossary/Viewport)（viewport）交叉状态的方法。

## Worker

1. [Web Work](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers) 最基本的多个线程，线程里可以请求接口，但不能访问 window（浏览器） 相关的内容
2. [SharedWorker](https://developer.mozilla.org/en-US/docs/Web/API/SharedWorker) 共享空间，几个浏览器 tab 共享
3. [ServiceWorker](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorker) 服务空间，主要拿来做接口缓存使用，特别是在没有网络的时候，可以用。