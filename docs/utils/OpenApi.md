# 面板开放接口

## 1.1. API 接口说明

- 接口基准地址：`http://127.0.0.1:5678/openApi`
- 服务端已开启 CORS 跨域支持
- API认证统一使用 Token 认证
- 需要授权的 API ，必须在请求头中使用 `api-token` 字段提供 `openApiToken`的值
- 使用 HTTP Status Code 标识状态
- 数据返回格式统一使用 JSON

### 1.1.1. 支持的请求方法

- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
- DELETE（DELETE）：从服务器删除资源。
- HEAD：获取资源的元数据。
- OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。

### 1.1.2. 通用返回状态说明

| *状态码* | *含义*                | *说明*                                              |
| -------- | --------------------- | --------------------------------------------------- |
| 200      | OK                    | 请求成功                                            |
| 201      | CREATED               | 创建成功                                            |
| 204      | DELETED               | 删除成功                                            |
| 400      | BAD REQUEST           | 请求的地址不存在或者包含不支持的参数                |
| 401      | UNAUTHORIZED          | 未授权                                              |
| 403      | FORBIDDEN             | 被禁止访问                                          |
| 404      | NOT FOUND             | 请求的资源不存在                                    |
| 422      | Unprocesable entity   | [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误 |
| 500      | INTERNAL SERVER ERROR | 内部错误                                            |
------

### 1.1.3.业务代码说明

| *状态码* | *含义*                | *说明*                                              |
| -------- | --------------------- | --------------------------------------------------- |
| 0        | fail                 | 请求错误
| 1        | success              | 请求成功
| 403/4403 | openApi 认证失败       | 注意，新版本将'cookieApiToken'改名为'openApiToken',请及时重置修改密码重置此token                                            |
------

### 1.1.4. 通用返回内容

| 参数名   | 参数说明    | 备注            |
| -------- | ----------- | --------------- |
| code       | 业务代码    | 参考 `1.1.3.业务代码说明`|
| data      | 返回结果 |                 |
| msg       | 结果消息   |                 |
| desc      | 结果描述 |                 |

## 1.2. 基础接口

### 1.2.2. 账号添加或者更新接口

- 请求路径：updateCookie
- 请求方法：post
- 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| ptPin | cookie值   | 不能为空 |
| userMsg | 备注     | 可以为空 |

- 响应参数

| 参数名   | 参数说明    | 备注            |
| -------- | ----------- | --------------- |


- 响应数据

```json
{
  "data": null,
  "code": 1,
  "msg":"success"
}
```

### 1.2.1. 账号添加或者更新接口(Wskey+Cookie 二合一)

- 请求路径：addOrUpdateAccount
- 请求方法：post
- 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| ptPin | pt_pin   | 不能为空 |
| ptKey | pt_key     | 可以为空,如果为空则不更新 |
| wsKey | ws_key   | 不能为空 |
| remarks | 备注     | 可以为空 默认为`ptPin`的值|

- 响应参数

| 参数名   | 参数说明    | 备注            |
| -------- | ----------- | --------------- |


- 响应数据

```json
{
  "data": null,
  "code": 1,
  "msg":"success"
}
```