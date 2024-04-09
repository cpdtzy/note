> `Event.path` is a non-standard API that returns the event's path, which is an array of the objects on which listeners will be invoked. It is supported by Blink only, causing web compatibility issues. Web developers should switch to the equivalent standard API `Event.composedPath()`, which returns the same result.
> Event.path 不是常规的 API。

在低版本时，还能够使用，高版本就无法正常使用
已经从 dom 中移除

**已经在 v109 Desktop 和 v109 Android 移除**
webview 在 **v111** 进行移除

## Resolved

使用 `Event.composedPath()` 来替换 `Event.path`
