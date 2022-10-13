# 请求（Request）<!-- omit in toc -->

[官方原文](https://koajs.com/#request)

## 学习理解<!-- omit in toc -->

Koa 的请求对象是在 Node.js 的请求对象之上进行封装的，提供了对日常 HTTP 服务开发有用的附加功能。

- [1. 请求标头相关](#1-请求标头相关)
- [2. URL 相关](#2-url-相关)
- [3. 其他](#3-其他)

### 1. 请求标头相关

- `request.header`：获取**或设置**请求标头对象，它还有一个别名是 `request.headers`。
- `request.length`：获取请求标头 `Content-length` 的值（数值类型），不存在该标头则返回 `undefined`。
- `request.type`：获取请求内容的类型，取自 `Content-Type` 请求标头，但不包含 charset 参数。
- `request.charset`：获取请求内容的字符集，取自 `Content-Type` 请求标头，若不存在则返回 `undefined`。
- `request.fresh`：通过请求标头和响应标头来检查客户端缓存的响应是否新鲜。Koa 使用了 [fresh](https://github.com/jshttp/fresh) 模块来实现，基于 `If-None-Match`、`ETag`、`If-Modified-Since` 以及 `Last-Modified` 等 HTTP 标头。
- `request.stale`：与 `request.fresh` 相反。
- `request.ip`：获取客户端的 IP 地址。当 koa 应用启用代理时（app.proxy = true），将获取 `X-Forwarded-For` 请求标头的值。
- `request.ips`：当 koa 应用启用代理（app.proxy = true）且存在 `X-Forwarded-For` 请求标头时，将返回该标头携带的 IP 数组，否则返回一个空数组。为了避免恶意攻击者伪造请求标头，koa 提供了[几种方法来避免 >>](./Application.md#3-代理相关设置)。
- `request.is(types...)`：检查请求是否包含 `Content-Type` 标头，并且是否包含给定的 mime 类型。如果没有请求正文返回 `null`，如果没有内容类型或者匹配失败则返回 `false`，否则返回匹配的内容类型。
- `request.accepts(types)`：通过识别 `Accept` 请求标头，检查给定的内容类型是否可以被客户端接受，如果为真则返回最佳匹配，否则返回 `false`。该 types 值可以是一个或多个 mime 或扩展名字符串。如果未提供任何类型，则返回所有可接受的类型。koa 使用了 [accepts](https://github.com/jshttp/accepts) 模块来实现此功能。
- `request.acceptsEncodings(encodings)`：通过识别 `Accept-Encoding` 请求标头，检查给定的编码是否可以被客户端接受，无法被接受时返回 `false`，否则返回最佳匹配的编码。当没有给出参数时，所有接受的编码都作为数组返回。
- `request.acceptsCharsets(charsets)`：通过识别 `Accept-Charset` 请求标头，检查给定的字符集是否可以被客户端接受，无法被接受时返回 `false`，否则返回最佳匹配的字符集。当没有给出参数时，所有接受的字符集都作为数组返回。
- `request.acceptsLanguages(langs)`：通过识别 `Accept-Language` 请求标头，检查给定的语言是否可以被客户端接受，无法被接受时返回 `false`，否则返回最佳匹配的语言。当没有给出参数时，所有接受的语言都作为数组返回。
- `request.get(field)`：获取给定的请求标头值。给定的请求表头字段名不区分大小写。

以下是示例：

```javascript
const Koa = require("koa");
const app = new Koa();
app.proxy = true;
app.use(async (ctx) => {
  const { request, response } = ctx;
  response.body = {
    headers: request.headers,
    length: request.length,
    type: request.type,
    charset: request.charset,
    fresh: request.fresh,
    stale: request.stale,
    ip: request.ip,
    ips: request.ips,
    is: request.is(),
    accepts: request.accepts(),
    acceptsEncodings: request.acceptsEncodings(),
    acceptsCharsets: request.acceptsCharsets(),
    acceptsLanguages: request.acceptsLanguages(),
    getContentType: request.get("content-type"),
  };
});
app.listen(3000);
```

运行上述代码后使用 Postman 请求 `http://127.0.0.1:3000/aaa/bbb?a=1&b=2` 返回以下内容：

```json
{
  "headers": {
    "content-type": "application/json",
    "user-agent": "PostmanRuntime/7.29.2",
    "accept": "*/*",
    "cache-control": "no-cache",
    "postman-token": "73b5decf-9194-49e6-b59d-bfea009c71a6",
    "host": "127.0.0.1:3000",
    "accept-encoding": "gzip, deflate, br",
    "connection": "keep-alive",
    "content-length": "2"
  },
  "length": 2,
  "type": "application/json",
  "charset": "",
  "fresh": false,
  "stale": true,
  "ip": "::ffff:127.0.0.1",
  "ips": [],
  "is": "application/json",
  "accepts": ["*/*"],
  "acceptsEncodings": ["gzip", "deflate", "br", "identity"],
  "acceptsCharsets": ["*"],
  "acceptsLanguages": ["*"],
  "getContentType": "application/json"
}
```

### 2. URL 相关

- `request.url`：获取**或设置**请求的 url，不包含请求协议和主机。
- `request.URL`：获取解析后的请求 [URL](https://nodejs.org/docs/latest-v16.x/api/url.html) 对象。
- `request.originalUrl`：获取请求的来源 url，不包含请求协议和主机。
- `request.origin`：获取请求来源，包含请求协议和主机。
- `request.href`：获取完整的请求地址。
- `request.path`：获取**或设置**请求的路径。
- `request.query`：获取**或设置**请求的查询参数解析对象，查询参数名为属性名，查询参数值为属性值。没有查询参数时返回空对象。
- `request.querystring`：获取**或设置**请求的查询字符串，不包含连接的 “?” 符号。
- `request.search`：获取**或设置**请求的查询字符串，包含连接的 “?” 符号。
- `request.host`：获取请求的主机，包含主机名和端口号。当 Koa 应用启用代理时（app.proxy = true），将获取 `X-Forwarded-Host` 请求标头的值，否则获取 `Host` 请求标头的值。
- `request.hostname`：获取请求的主机名，实现方式同 `request.host`。
- `request.protocol`：获取请求的协议，“http” 或 “https”。当 Koa 应用启用代理时（app.proxy = true），将获取 `X-Forwarded-Proto` 请求标头的值。
- `request.secure`：用于检查请求是否通过安全协议发出的，是 `ctx.protocol == "https"` 的简写形式。
- `request.subdomains`：返回子域数组，默认情况下，koa 认为子域是指主机名以 “.” 分隔后排除右侧两部分后剩下的部分，可以通过 `app.subdomainOffset` 来设置右侧需要排除的部分数。

以下是示例：

```javascript
const Koa = require("koa");
const app = new Koa();
app.proxy = true;
app.use(async (ctx) => {
  const { request, response } = ctx;

  // 获取URL对象所有属性
  const URL = {};
  for (const key in request.URL) {
    if (typeof request.URL[key] !== "function") {
      URL[key] = request.URL[key];
    }
  }

  response.body = {
    url: request.url,
    URL,
    originalUrl: request.originalUrl,
    origin: request.origin,
    href: request.href,
    path: request.path,
    query: request.query,
    querystring: request.querystring,
    search: request.search,
    host: request.host,
    hostname: request.hostname,
    protocol: request.protocol,
    secure: request.secure,
    subdomains: request.subdomains,
  };
});
app.listen(3000);
```

运行上述代码后使用 Postman 请求 `http://127.0.0.1:3000/aaa/bbb?a=1&b=2` 返回以下内容：

```json
{
  "url": "/aaa/bbb?a=1&b=2",
  "URL": {
    "href": "http://127.0.0.1:3000/aaa/bbb?a=1&b=2",
    "origin": "http://127.0.0.1:3000",
    "protocol": "http:",
    "username": "",
    "password": "",
    "host": "127.0.0.1:3000",
    "hostname": "127.0.0.1",
    "port": "3000",
    "pathname": "/aaa/bbb",
    "search": "?a=1&b=2",
    "searchParams": {},
    "hash": ""
  },
  "originalUrl": "/aaa/bbb?a=1&b=2",
  "origin": "http://127.0.0.1:3000",
  "href": "http://127.0.0.1:3000/aaa/bbb?a=1&b=2",
  "path": "/aaa/bbb",
  "query": {
    "a": "1",
    "b": "2"
  },
  "querystring": "a=1&b=2",
  "search": "?a=1&b=2",
  "host": "127.0.0.1:3000",
  "hostname": "127.0.0.1",
  "protocol": "http",
  "secure": false,
  "subdomains": []
}
```

### 3. 其他

- `request.method`：获取**或设置**请求方法。
- `request.idempotent`：检查请求是否幂等。
- `request.socket`：返回请求套接字。
