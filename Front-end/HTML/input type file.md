> 文件选择框

`type="file"` - 可选择文件 multiple 可获取多个文件
`webkitdirectory` - 可选择文件夹

对应的 `listenener` 可直接通过 `target.files` 获取对应的内容

```js
dir.addEventListener('change', (e) => {
  console.log(e.target.files); // 对应的文件格式
})
```