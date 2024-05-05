
> 需要我们去做的事，最好处理掉这个情况，不然后期非常不方便

## 笔记

- [ ] 把浏览器的 bookmark 转移至 obsidian 中

## 公司

- [ ] 通过其他链接进来有时候会丢失
	1. 主要问题是 ==one== 重定向因为 `localstorage.getItem('companyUrl')` 没有对应的值，直接丢弃了当前的路由。
	2. `checkSystemInfo` 检测系统对应内容，报错后跳转页面。
	3. `src/common/utils/guard.js` 对应内容 ==33 line== 主要是 `getMainAccountLoginUrl` 函数，返回的路由，通过 `localstorage.getItem('companyUrl')` 后，为 `null` 所以不会添加重定向内容。

## App 练习

- [ ] 移动端开发
	- [设计](https://dribbble.com/shots/21095629-Booking-Service-Mobile-App-design-iOS-Android-ux-ui-designer)
	- 开发框架待选定

## Animation

[25种 canvas 动画](https://webdesign.tutsplus.com/21-ridiculously-impressive-html5-canvas-experiments--net-14210a)

## 库

- [ ] [gsap](https://www.npmjs.com/package/gsap) [官网](https://greensock.com/) 动画

## 了解

- [ ] 了解一下 [AntV-G6](https://g6.antv.antgroup.com/)
- [ ] 了解一下 [AntV-X6](https://x6.antv.antgroup.com/)

## 新的css属性

scroll-snap css 轮播图


## 源码共读


[https://juejin.cn/post/7079706017579139102](https://juejin.cn/post/7079706017579139102)


iife ? 
umd ?

[Next](https://www.nextjs.cn/docs/basic-features/data-fetching) 搭配 wordpress [github](https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress)