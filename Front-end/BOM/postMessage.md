> postMessage 主要用于通信， iframe、浏览器标签等之类的通信操作。
> 也可用于 Worker 通信，进行数据处理。[MDN](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage)


## 语法

```javascript
postMessage(message, targetOrigin)
postMessage(message, targetOrigin, transfer)
```

## 参数

==message== 
发送给其他窗口的数据。这数据结构为[结构化克隆算法](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) 

==targetOrigin==
可以使用通配符 `"*"` 来作为路由。不过这有个缺点，任意人员只要内嵌该也没都可以进行通信操作，具有高危性。可以使用对应项目中的通信路由来作为该参数，如果 URI 不匹配则无法进行正常通信，将无法接受到对应信息。

==transfer== *(boolean)*
该配置项决定，发送方将数据全权交由接收方，发送方将不可再用。

## 返回值

None(`undefined`)

## dispatched 事件

==window.onmessage== 
`window` 监听事件，来获取信息：

```javascript
window.addEventListener(
  "message",
  (event) => {
    if (event.origin !== "http://example.org:8080") return;

    // …
  },
  false
);
```

### 事件对应属性

==data== 
接收到的数据。

==origin==
来源方的域名、IP、端口。主要用于信息安全来识别，传来的信息方。
来源方例子：`https://example.org` 、`http://example.net` 和 `http://example.com:8080`

==source==
发送信息的 `window` 对象，可以用这个来实现两个不同来源的窗口之间的通信。