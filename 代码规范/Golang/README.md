# Golang 代码规范

代码格式（风格）问题是最有争议但最不重要的问题。开发人员虽然可以适应不同的格式风格，但是他们更希望看到和自己风格相同的代码。如果每个人都能坚持相同的风格，那么总体花在代码风格规范上面的时间就会更少。究竟如何在没有冗长的规范性风格指南的情况下接近这个乌托邦呢？

Go 采用了一种不同寻常的方法，让机器处理大多数格式化问题。Go 提供了 [gofmt](https://pkg.go.dev/cmd/gofmt) 程序（或使用 [go fmt](https://pkg.go.dev/cmd/go#hdr-Gofmt__reformat__package_sources)）以包（packages）的维度来格式化代码。

## 使用 VS Code 插件

如果使用 Visual Studio Code 编辑器，可以安装 “[Go for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=golang.go)” 扩展程序，默认会在保存时等操作场景下自动调用 gofmt 来格式化代码。（当然，也支持配置其他的格式化程序）。

## Google 的 Go 风格指南

[官方网站](https://google.github.io/styleguide/go/) | [GitHub](https://github.com/google/styleguide/tree/gh-pages/go)

Google 开源了其内部的[代码风格指南](https://google.github.io/styleguide/)，其中就包含了 Go。
