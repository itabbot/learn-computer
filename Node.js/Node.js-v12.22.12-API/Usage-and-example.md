# 用法与示例（Usage and example）

[官方原文](https://nodejs.org/docs/latest-v12.x/api/synopsis.html) | [中文网译文](http://nodejs.cn/api-v12/synopsis.html)

## 学习理解

本章节演示了在命令行启动一个简单的 Web 服务。大概有以下步骤：

1. 下载并安装 Node.js。

2. 创建文件 `hello-world.js`。

3. 保存以下内容：

```javascript
const http = require("http");

const hostname = "127.0.0.1";
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader("Content-Type", "text/plain");
  res.end("Hello, World!");
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

4. 命令行执行 `node hello-world.js`。输出以下内容表示启动成功：`Server running at http://127.0.0.1:3000/`。

5. 浏览器打开 `http://127.0.0.1:3000`，出现以下字样表示成功：`Hello, World!`。
