# 将 Prettier 作为 ESLint 的规则运行

[NPM](https://www.npmjs.com/package/eslint-plugin-prettier) | [Github](https://github.com/prettier/eslint-plugin-prettier)

`eslint-plugin-prettier` 是一个 ESLint 插件，将 Prettier 作为 ESLint 的规则运行，并将差异报告为 ESLint 问题。使用方法：

安装 `eslint-plugin-prettier`：

```shell
npm install --save-dev eslint-plugin-prettier
```

然后，添加 `"prettier"` 到 ESLint 配置文件中的 “plugins” 数组，并添加 `prettier/prettier` 规则。如下所示：

```JSON
{
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```
