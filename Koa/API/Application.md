# 应用（Application）<!-- omit in toc -->

[官方原文](https://koajs.com/#application) | [中文网译文](http://koajs.cn/#application)

## 学习理解 <!-- omit in toc -->

- [1. 基本使用](#1-基本使用)
- [2. 级联中间件](#2-级联中间件)
- [3. 代理相关设置](#3-代理相关设置)
- [4. app.callback()](#4-appcallback)
- [5. app.context](#5-appcontext)
- [6. 错误事件](#6-错误事件)

### 1. 基本使用

使用 Koa 框架的第一步就是实例化一个 Koa 应用程序对象，最基本的用法：

```JavaScript
// 实例化一个 Koa 应用程序
const Koa = require('koa');
const app = new Koa();

// 注册一个最简单的中间件
app.use(async (ctx) => {
  // 响应一个字符串
  ctx.body = 'Hello World';
});

// 启动 HTTP 服务并监听端口
app.listen(3000);
```

详细步骤：

1. 创建目录然后初始化工程：`npm init -y`
2. 安装 Koa：`npm i koa`
3. 创建 index.js 文件并保存上述代码
4. 启动服务：`node index.js`
5. 浏览器访问 `http://127.0.0.1:3000`，页面显示 “Hello World” 字样表示成功

### 2. 级联中间件

Koa 通过级联中间件的方式来处理每个 HTTP 请求，请移步 [中间件实践>>](../最佳实践/中间件实践.md)

可以在 `app.middleware` 属性中看到所有已注册的中间件。

### 3. 代理相关设置

HTTP 代理服务或负载均衡在转发请求时通常会携带 `X-Forwarded-*` 相关的请求标头来标识原始的请求信息。相关标准可查阅 [RFC 7239](https://www.rfc-editor.org/rfc/rfc7239)。

如果 Koa 服务的上游存在代理或负载均衡，可以设置 `app.proxy` 为 `true`，Koa 将会识别 `X-Forwarded-*` 相关的请求标头。例如：

```JavaScript
// 启用代理
app.proxy = true;

app.use(async (ctx) => {
  ctx.body = {
    // 请求的主机信息
    // 启用代理时通过 X-Forwarded-Host 请求标头获取
    host: ctx.host,
    hostname: ctx.hostname,

    // 请求的协议
    // 启用代理时通过 X-Forwarded-Proto 请求标头获取
    protocol: ctx.protocol,

    // 请求的 IP 地址
    // 启用代理时通过 X-Forwarded-For 请求标头获取
    ip: ctx.ip,
    ips: ctx.ips,
  };
});
```

恶意攻击者可能会通过伪造 `X-Forwarded-For` 请求标头来伪造客户端 IP 地址，为了以防这种情况，可以通过设置 `app.proxyIpHeader` 来代替 `X-Forwarded-For` 请求标头。

通常情况下代理服务器会将自身的 IP 地址追加在 `X-Forwarded-For` 请求标头值的右侧，所以也可以设置 `app.maxIpsCount` 来指定实际存在的代理服务个数，Koa 将只会识别右侧指定个数的 IP 地址。

```JavaScript
app.proxyIpHeader = 'X-Real-IP';
app.maxIpsCount = 2;
```

### 4. app.callback()

`app.callback()` 返回一个适合 `http.createServer()` 处理的回调函数。

`app.listen(…)` 其实是以下的简写：

```JavaScript
http.createServer(app.callback()).listen(...);
```

这也意味着可以同时启动多个服务：

```JavaScript
const http = require('http');
const https = require('https');
const Koa = require('koa');
const app = new Koa();
http.createServer(app.callback()).listen(3000);
https.createServer(app.callback()).listen(3001);
```

### 5. app.context

`app.context` 是中间件 `ctx` 变量的原型，所以，可以通过为其添加属性来作用于所有的请求上下文：

```JavaScript
// 添加自定义属性
app.context.foo = 'bar';

app.use(async (ctx) => {
  ctx.body = {
    // 获取自定义属性
    foo: ctx.foo,
  };
});
```

### 6. 错误事件

可以通过监听应用的错误事件来捕捉错误：

```JavaScript
app.on('error', (error, ctx) => {
  console.error(error, ctx);
});
```
