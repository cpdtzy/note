---
aliases:
  - 画中画
tags:
  - api
  - 画中画
Date: 2025-01-16
---
实现 文档中画中画的效果，永远悬浮于浏览器之上。
主要通过 [`documentPictureInPicture.requestWindow()`](https://developer.mozilla.org/zh-CN/docs/Web/API/DocumentPictureInPicture/requestWindow) 来唤起画中画。

*当前兼容性不是很好，仅 chrome 116 支持* 

返回 Primise 格式的 window 对象，对内容进行控制

