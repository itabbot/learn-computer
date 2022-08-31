# 设置 Git 提交前必须通过 ESLint 检查

为了避免没有通过 Lint 的代码误提交到仓库中，可以使用 [pre-commit](https://www.npmjs.com/package/pre-commit) 工具结合 `package.json` 中的脚本来进行控制。它的原理是为 Git 添加钩子，提交代码之前执行指定的脚本（通常是 Lint 脚本），如果脚本没有通过则拦截提交。使用方法如下：

先使用下方命令安装 `pre-commit`，因为只是在开发过程中使用到它，所以添加 `--save-dev` 选项。

```shell
npm install --save-dev pre-commit
```

然后在 `package.json` 中设置 Lint 脚本，同时添加到 `pre-commit` 节点中就大功告成了。以下是示例：

```JSON
{
  "scripts": {
    "lint": "eslint ./src --fix"
  },
  "pre-commit": [
    "lint"
  ]
}
```
