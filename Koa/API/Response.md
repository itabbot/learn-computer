# 响应（Response）<!-- omit in toc -->

[官方原文](https://koajs.com/#response)

## 学习理解<!-- omit in toc -->

Koa 的响应对象是在 Node.js 的响应对象之上进行封装的，提供了对日常 HTTP 服务开发有用的附加功能。

- [1. 响应标头相关](#1-响应标头相关)
- [2. 其他](#2-其他)

### 1. 响应标头相关

- `response.header`：获取所有响应标头。它还有一个别名是 `response.headers`。
- `response.length`：获取**或设置**响应内容长度。获取其值是通过识别 `Content-Length` 响应头的值，或从 `ctx.body` 推断，或 `undefined`。
- `response.get(field)`：获取不区分大小写的响应头字段值。
- `response.has(field)`：判断当前是否已经设置了给定的响应头。标头名称匹配不区分大小写。
- `response.set(field, value)`：设置给定的单个响应头。
- `response.set(fields)`：设置给定的多个响应头。
- `response.append(field, value)`：追加给定的响应头。
- `response.remove(field)`：移除给定的响应头。
- `response.type`：获取**或设置**响应头内容类型，不包含字符集。是通过识别和处理 `Content-Type` 响应标头来实现的。
- `response.is(types...)`：检查响应类型是否是提供的类型之一，类似于 `ctx.request.is()`。
- `response.redirect(url, [alt])`：重定向到给定的 url。是通过设置 `Location` 响应标头来实现的，且 `response.status` 响应头默认设置为 `302`。
- `response.attachment([filename], [options])`：通过设置 `Content-Disposition` 响应标头来向客户端发出提示下载的信号。Koa 通过 [content-disposition](https://github.com/jshttp/content-disposition) 模块来实现此功能。
- `response.headerSent`：检查是否已发送响应标头。
- `response.lastModified`：获取**或设置** `Last-Modified` 响应标头的值（Date 类型）。
- `response.etag`：**设置** `ETag` 响应标头值。
- `response.vary(field)`：**设置** `Vary` 响应标头值，用于告知代理服务器应该采取什么样的缓存策略。Koa 使用 [vary](https://github.com/jshttp/vary) 模块来实现此功能。
- `response.flushHeaders()`：刷新所有设置的响应标头，然后开始正文。这也意味着后续的任何响应标头操作都将被忽略。

以下是示例：

```javascript
const Koa = require("koa");
const app = new Koa();
app.use(async (ctx) => {
  const { response } = ctx;

  response.remove("Content-Type");
  response.set("Content-Type", "applicaiton/json");
  // response.append('Content-Type', 'text/plain');
  response.vary("Content-Type");
  response.flushHeaders();

  response.body = {
    headers: response.headers,
    length: response.length,
    getContentType: response.get("content-type"),
    hasContentType: response.has("content-type"),
    type: response.type,
    isJson: response.is("applicaiton/json"),
    headerSent: response.headerSent,
    lastModified: response.lastModified,
    etag: response.etag,
  };
});
app.listen(3000);
```

运行上述代码后使用 Postman 请求 `http://127.0.0.1:3000/aaa/bbb?a=1&b=2` 返回以下内容：

```json
{
  "headers": {
    "content-type": "applicaiton/json",
    "vary": "Content-Type"
  },
  "getContentType": "applicaiton/json",
  "hasContentType": true,
  "type": "applicaiton/json",
  "isJson": "applicaiton/json",
  "headerSent": true,
  "etag": ""
}
```

### 2. 其他

- `response.socket`：获取响应套接字对象。
- `response.status`：获取**或设置**响应状态（HTTP 状态码）。默认值是 `404`。
- `response.message`：获取**或设置**响应状态消息。默认情况下，它与 `response.status` 关联。
- `response.body`：获取**或设置**响应内容。其值可以是 string、Buffer、Stream、Object、null 或 undefined。
  - `string`：此时 `Content-Type` 响应头默认设置为 `text/html` 或 `text/plain`，两者都具有 `utf-8` 的默认字符集。`Content-Length` 响应头也将被自动设置。
  - `Buffer`：此时 `Content-Type` 响应头默认设置为 `application/octet-stream`，`Content-Length` 响应头也将被自动设置。
  - `Stream`：此时 `Content-Type` 响应头默认设置为 `application/octet-stream`。
  - `Object`：此时 `Content-Type` 响应头默认设置为 `application/json`。
  - `null` 或 `undefined`：此时 `response.status` 将会被默认自动设置为 `204`。

以下是示例：

```javascript
const Koa = require("koa");
const app = new Koa();
app.use(async (ctx) => {
  const { response } = ctx;
  response.body = {
    status: response.status,
    message: response.message,
  };
});
app.listen(3000);
```

运行上述代码后使用 Postman 请求 `http://127.0.0.1:3000/aaa/bbb?a=1&b=2` 返回以下内容：

```json
{
  "status": 404,
  "message": "Not Found"
}
```
