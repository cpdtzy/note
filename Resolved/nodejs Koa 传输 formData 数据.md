## 起因

前端传递 formData 数据格式，在后台无法正常收到

## 前端

`content-type` 没有设置成 `application/x-www-form-urlencoded` 或者 `multipart/form-data` 

### 后端

- 设置 `application/x-www-form-urlencoded` 需要使用 bodyParser 解析
- 设置 `multipart/form-data` 需要使用 `multer` 或 `koa-multer` 解析
	接收方案之一是利用nodejs中间件：`multiparty`，`multiparty` 是 nodejs `框架express` 推荐的中间件。

