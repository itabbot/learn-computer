# JavaScript 代码规范

关于 JavaScript 的代码风格/规范，目前并没有统一的标准，但有几个是比较流行的，分别是：[Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)、[JavaScript Standard Style](https://github.com/standard/standard) 和 [Google JavaScript Style Guide](https://github.com/google/eslint-config-google)。

相关的工具也有好几个，分别是：[ESLint](https://github.com/eslint/eslint)、[JSHint](https://github.com/jshint/jshint) 和 [JSLint](https://github.com/jslint-org/jslint)。目前来看，ESLint 是最受欢迎的，本人也推荐使用它，而且上述罗列的三个流行代码风格也都提供了相应的 ESLint 插件。

## ESLint

[官方网站](https://eslint.org/) | [Github](https://github.com/eslint/eslint) | [NPM](https://www.npmjs.com/package/eslint) | [中文网](https://cn.eslint.org/)  
[官方文档](https://eslint.org/docs/latest/user-guide/) | [中文文档](https://cn.eslint.org/docs/user-guide/) | [文档快照](./snapshoot/ESLintUserGuide/2022-08-29/)

以下学习 ESLint 的基本使用，后续必要之时再按需查阅文档。

- [快速安装（选装流行的代码风格配置）](./ESLint/快速安装.md)
- [基本使用](./ESLint/基本使用.md)
- [使用 VS Code 的 ESLint 插件](./ESLint/使用VSCode的ESLint插件.md)
- [设置 Git 提交前必须通过 ESLint 检查](./ESLint/设置Git提交前必须通过ESLint检查.md)

# Prettier

[官方网站](https://prettier.io/) | [Github](https://github.com/prettier/prettier) | [NPM](https://www.npmjs.com/package/prettier) | [中文网](https://www.prettier.cn/)

还有一个非常流行的工具不得不提，那就是 Prettier，它在代码格式方面几乎面面俱到，就像它的名字一样，可以让代码变得更加漂亮。

值得注意的是，Prettier 跟一些流行的代码风格/规范存在部分规则冲突，但是还好，产生冲突的都是格式相关的规则，不会造成代码质量问题。针对这些冲突的规则，通常的做法是：选择使用 Prettier。在使用 ESLint 工具时，可以再安装一个 `eslint-config-prettier` 工具，它会关闭所有不必要或可能与 Prettier 冲突的规则。[使用方法>>](./Prettier/关闭不必要或可能冲突的规则.md)

另外，还可以给 ESLint 安装一个 `eslint-plugin-prettier` 插件，将 Prettier 作为 ESLint 的规则运行，并将差异报告为 ESLint 问题。这样就可以统一错误来源，方便使用和处理。[使用方法>>](./Prettier/作为ESLint规则运行.md)
