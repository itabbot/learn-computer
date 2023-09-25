# Go<!-- omit in toc -->

- [1. 概述](#1-概述)
- [2. 参考文档](#2-参考文档)
- [3. 入门](#3-入门)
- [4. 最佳实践](#4-最佳实践)

## 1. 概述

[官方网站](https://go.dev) | [官方文档](https://go.dev/doc/) | [GitHub](https://github.com/golang) | [搜索包和模块](https://pkg.go.dev/) | [在线沙箱](https://go.dev/play/)

Go（又称 Golang，是由于它以前的域名 golang.org）是 Google 开发的一种开源、[静态类型检查](../术语表/类型系统.md)、[强类型](../术语表/类型系统.md)、[编译型](../术语表/编译型语言.md)的编程语言。它具有垃圾回收、运行时反射和新颖的类型系统等功能，并内置并发性和强大的标准库，支持 Linux、macOS、Windows 等操作系统。

## 2. 参考文档

- [标准库](https://pkg.go.dev/std)
- [命令行](https://go.dev/doc/cmd)
- [模块参考](https://go.dev/ref/mod)
- [go.mod 文件参考](https://go.dev/doc/modules/gomod-ref)
- [内存模型](https://go.dev/ref/mem)
- [语言标准规范](https://go.dev/ref/spec)

## 3. 入门

- [Go 示例](./Go-by-Example)（[Go by Example](https://gobyexample.com)）
- [Go Web 示例](./Go-Web-Examples)（[Go Web Examples](https://gowebexamples.com)）

## 4. 最佳实践

- Web 框架：[Gin](../Gin)
- 项目结构参考：[golang-gin-example](https://github.com/gothinkster/golang-gin-realworld-example-app) / [insbiz](https://github.com/fooins/insbiz) / [go-gin-api](https://github.com/xinliangnote/go-gin-api) / [go-gin-example](https://github.com/eddycjy/go-gin-example)
- [Golang 代码规范](../代码规范/Golang)
- 日志处理：[zap](https://github.com/uber-go/zap) / [logrus](https://github.com/sirupsen/logrus) / [zerolog](https://github.com/rs/zerolog) / [apexlog](https://github.com/apex/log) / [glog](https://github.com/golang/glog) / [log](https://pkg.go.dev/log)
- 配置管理：[viper](https://github.com/spf13/viper) / [configor](https://github.com/jinzhu/configor) / [koanf](https://github.com/knadh/koanf)
- 错误处理：[opsmgt-backend](https://github.com/fooins/opsmgt-backend/tree/main/src/libraries/errors)
- 数据校验：[go-playground-validator](https://github.com/go-playground/validator) / [asaskevich-govalidator](https://github.com/asaskevich/govalidator) / [ozzo-validation](https://github.com/go-ozzo/ozzo-validation) / [thedevsaddam-govalidator](https://github.com/thedevsaddam/govalidator)
- 对象关系映射：[gorm](https://github.com/go-gorm/gorm) / [ent](https://github.com/ent/ent) / [sqlboiler](https://github.com/volatiletech/sqlboiler) / [gorp](https://github.com/go-gorp/gorp) / [upperdb](https://github.com/upper/db)
- 鉴权：[jwt.io](https://jwt.io/) / [golang-jwt](https://github.com/golang-jwt/jwt)
- 测试：[testify](https://github.com/stretchr/testify) / [goconvey](https://github.com/smartystreets/goconvey) / [ginkgo](https://github.com/onsi/ginkgo) / [go-cmp](https://github.com/google/go-cmp) / [httpexpect](https://github.com/gavv/httpexpect) / [testcontainers-go](https://github.com/testcontainers/testcontainers-go) / [godog](https://github.com/cucumber/godog)