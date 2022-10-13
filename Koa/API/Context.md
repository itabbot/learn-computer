# 上下文（Context）<!-- omit in toc -->

[官方原文](https://koajs.com/#context)

## 学习理解<!-- omit in toc -->

Koa 为每个请求创建一个上下文对象，并传递给中间件，上下文对象中包含了 Node.js 的原始 req 和 res 对象，以及 Koa 自身的 request 和 response 对象等：

```Javascript
app.use(async (ctx) => {
  // 上下文变量
  ctx;

  // Node.js 的请求对象和响应对象
  ctx.req;
  ctx.res;

  // Koa 的请求对象和响应对象
  ctx.request;
  ctx.response;
});
```

以下是其他更多：

- [1. ctx.state](#1-ctxstate)
- [2. ctx.app](#2-ctxapp)
- [3. ctx.cookies](#3-ctxcookies)
- [4. ctx.throw](#4-ctxthrow)
- [5. ctx.assert](#5-ctxassert)
- [6. 请求对象别名](#6-请求对象别名)
- [7. 响应对象别名](#7-响应对象别名)

### 1. ctx.state

`ctx.state` 可用于为中间件和视图文件传递信息，可参考 [koa-views](https://github.com/queckezz/koa-views/blob/e7b8e4d50160a94ccc9eef2d4fe6488d297b5dde/README.md#example)。

### 2. ctx.app

`ctx.app` 是 Koa 应用实例的引用。

`ctx.app.emit` 是 Koa 应用扩展的内部 [EventEmitter](https://nodejs.org/dist/latest-v16.x/docs/api/events.html)，它发出一个类型由第一个参数定义的事件，可以设置处理函数来侦听事件。比如：

```Javascript
app.use(async (ctx) => {
  ctx.app.emit('foo', 'bar.');
});

app.on('foo', (...args) => {
  console.log('foo: ', ...args);
});
```

### 3. ctx.cookies

`ctx.cookies` 是 [cookies](https://github.com/pillarjs/cookies) 模块 Cookies 类的一个实例对象，Koa 通过它来提供相应的能力。

主要有两个实用的方法：`ctx.cookies.set` 用于设置 cookie，`ctx.cookies.get` 用于获取 cookie。详细的用法请参阅 [cookies](https://github.com/pillarjs/cookies) 模块的相关说明。

特别的是：Koa 在实例化 `ctx.cookies` 时，会将 `app.keys` 作为选项传入，作为签名 cookie 的密钥。在设置和获取 cookie 时通过 `signed` 选项来设置是否进行签名或验签。比如：

```Javascript
// 设置 cookie 的签名密钥
app.keys = [
  'OEK5zjaAMPc3L6iK7PyUjCOziUH3rsrMKB9u8H07La1SkfwtuBoDnHaaPCkG5Brg',
  'MNKeIebviQnCPo38ufHcSfw3FFv8EtnAe1xE02xkN1wkCV1B2z126U44yk2BQVK7',
];

app.use(async (ctx) => {
  // 设置 cookie
  ctx.cookies.set('foo', 'bar', { signed: true });

  // 获取 cookie
  ctx.body = {
    foo: ctx.cookies.get('foo', { signed: true }),
  };
});
```

### 4. ctx.throw

使用 `ctx.throw` 将抛出一个错误。Koa 使用了 [http-errors](https://github.com/jshttp/http-errors) 来创建错误对象。以下是使用示例：

```Javascript
app.use(async (ctx) => {
  ctx.throw(400);
  ctx.throw(400, 'name required');
  ctx.throw(400, 'name required', { foo: bar });
});
```

### 5. ctx.assert

`ctx.assert` 执行一次断言，Koa 使用了 [http-assert](https://github.com/jshttp/http-assert) 模块来实现，它类似 Node.js 的 [assert](https://nodejs.org/dist/latest-v16.x/docs/api/assert.html) 模块，不同的是，http-assert 模块断言不通过时抛出的是使用 [http-errors](https://github.com/jshttp/http-errors) 来创建错误对象。

### 6. 请求对象别名

以下访问器和方法是 Koa 请求对象的别名，这样做的目的是为了更加方便地使用。

- ctx.header
- ctx.headers
- ctx.method
- ctx.method=
- ctx.url
- ctx.url=
- ctx.originalUrl
- ctx.origin
- ctx.href
- ctx.path
- ctx.path=
- ctx.query
- ctx.query=
- ctx.querystring
- ctx.querystring=
- ctx.host
- ctx.hostname
- ctx.fresh
- ctx.stale
- ctx.socket
- ctx.protocol
- ctx.secure
- ctx.ip
- ctx.ips
- ctx.subdomains
- ctx.is()
- ctx.accepts()
- ctx.acceptsEncodings()
- ctx.acceptsCharsets()
- ctx.acceptsLanguages()
- ctx.get()

### 7. 响应对象别名

以下访问器和方法是 Koa 响应对象的别名：

- ctx.body
- ctx.body=
- ctx.status
- ctx.status=
- ctx.message
- ctx.message=
- ctx.length=
- ctx.length
- ctx.type=
- ctx.type
- ctx.headerSent
- ctx.redirect()
- ctx.attachment()
- ctx.set()
- ctx.append()
- ctx.remove()
- ctx.lastModified=
- ctx.etag=
