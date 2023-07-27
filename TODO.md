> 需要我们去做的事，最好处理掉这个情况，不然后期非常不方便

- [ ] 通过其他链接进来有时候会丢失
	1. 主要问题是 ==one== 重定向因为 `localstorage.getItem('companyUrl')` 没有对应的值，直接丢弃了当前的路由。
	2. `checkSystemInfo` 检测系统对应内容，报错后跳转页面。
	3. `src/common/utils/guard.js` 对应内容 ==33 line== 主要是 `getMainAccountLoginUrl` 函数，返回的路由，通过 `localstorage.getItem('companyUrl')` 后，为 `null` 所以不会添加重定向内容。

