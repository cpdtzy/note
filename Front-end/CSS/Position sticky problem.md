## 优点

不需要 js 进行，直接可以使用 sticky 进行占位，并置顶

## 问题

1. 要设置 position sticky 并且要设置 top
2. sticky 在滚动变化成 fixed 时，定位与父元素，所以父元素要是滚动元素
	- sticky 元素和父元素之间有其他元素，sticky 将会==失效== 
	