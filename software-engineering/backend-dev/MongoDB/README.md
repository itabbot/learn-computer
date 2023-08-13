# MongoDB<!-- omit in toc -->

- [1. 快速开始](#1-快速开始)
  - [1.1. 相关资源](#11-相关资源)
  - [1.2. 定义](#12-定义)
  - [1.3. 背景](#13-背景)
  - [1.4. 应用场景](#14-应用场景)
  - [1.5. 尝试](#15-尝试)
- [2. 按需学习](#2-按需学习)
- [3. 系统学习](#3-系统学习)

## 1. 快速开始

### 1.1. 相关资源

[官方网站](https://www.mongodb.com) | [官方文档](https://www.mongodb.com/docs) | [GitHub](https://github.com/mongodb)  
[开发者中心](https://www.mongodb.com/developer)

### 1.2. 定义

MongoDB 是一个开源的、跨平台的、[面向文档](../../../glossary/文档数据库.md)的[非关系型](../../../glossary/关系型与非关系型数据库.md)数据库管理系统。使用 C++、Go、JavaScript、Python 等语言编写。MongoDB 以其灵活性、高可扩展性和高性能而受到广泛关注和采用。

MongoDB 社区版是免费的，适用于 Windows、Linux 和 macOS。

MongoDB 的主要特点有：

- 面向文档的数据模型： MongoDB 使用文档模型来存储数据，而不是传统的行和列的关系模型，其中文档是以类似 JSON 的 BSON（二进制 JSON）格式表示的。
- 灵活的数据模式： MongoDB 的文档可以具有不同的结构，没有固定的模式要求。这意味着可以在运行时灵活地更改数据模式，而不需要事先定义表结构。
- 强大的查询功能： MongoDB 提供丰富的查询语言和灵活的查询功能，包括范围查询、条件查询、正则表达式匹配、文本搜索等。它还支持聚合框架，使得数据分析和聚合操作更加便捷。
- 高性能： MongoDB 的设计目标之一是提供高性能的数据存取和查询。它支持索引和查询优化功能，可以在大规模数据集上快速检索和操作数据。
- 高可用性： MongoDB 具有内置的复制和故障恢复机制，以保证数据的可用性和容错性。数据可在多个副本之间同步，当出现故障时能够自动进行切换和恢复。
- 高可扩展性： MongoDB 支持水平扩展，可以在集群中添加更多的服务器，以处理更大规模的数据和流量负载。它可以根据需求自动分片和负载均衡数据。

### 1.3. 背景

MongoDB 公司最初成立于 2007 年，当时名为 10gen，总部位于美国纽约。10gen 最初的目标是构建一个完全基于开源组件的平台即服务架构。然而，他们无法找到符合其云架构“原则”的现有数据库平台。因此，他们开始开发一个名为 MongoDB 的面向文档的数据库系统。

在意识到该软件本身的潜力后，10gen 的团队决定放弃其云平台，转而专注于维护 MongoDB。2009 年 2 月，10gen 将 MongoDB 作为开源项目发布。2013 年 8 月 27 日，10gen 宣布更名为 MongoDB Inc.，使其与最终成为其旗舰产品的 MongoDB 更加紧密地联系在一起。

MongoDB 公司于 2017 年 10 月 20 日首次公开发行股票，并于 2021 年 6 月 29 日进行二次发行。

### 1.4. 应用场景

- 物联网平台： MongoDB 适合物联网平台中的数据存储和实时处理。能够处理大规模的传感器数据和设备状态，并支持实时监控和分析。
- 电子商务平台： MongoDB 适用于电子商务平台的数据管理和实时分析。其可伸缩性和高性能使得能够处理大量的产品数据和用户交互数据，并支持实时的数据分析和个性化推荐。
- 社交媒体应用： MongoDB 适合存储和管理社交媒体应用中的数据，如用户信息、社交关系和动态消息。其灵活的数据模型和高性能查询功能使得可以轻松存储和检索复杂的社交数据，并支持实时推送和个性化推荐。
- 物流和供应链管理： MongoDB 适用于物流和供应链管理领域。它可以存储和管理供应链中的订单数据、库存信息和运输记录。MongoDB 的灵活的文档模型和高性能查询使得能够实时跟踪和分析物流数据，以提高供应链的效率和可见性。
- 游戏开发： MongoDB 适用于游戏开发和游戏后端服务。它可以存储和管理游戏数据、玩家配置和游戏状态。MongoDB 的高性能写入操作和复杂查询功能使得能够支持实时的游戏交互和玩家数据分析。
- 金融服务： MongoDB 适用于金融服务领域的数据管理和实时数据分析。它可以存储和处理金融交易数据、客户信息和风险评估。MongoDB 的可伸缩性和高性能使得能够处理大量的金融数据，并提供实时的交易分析和报告。

### 1.5. 尝试

- [使用 Docker 安装 MongoDB 社区版](https://github.com/itabbot/learn-mongodb/tree/main/quick-start/install-community-with-docker)
- [使用 MongoSH 体验 MongoDB 的基本操作](https://github.com/itabbot/learn-mongodb/tree/main/quick-start/experience-with-mongosh)

## 2. 按需学习

- [知识：Node.js 的 ODM 工具 Mongoose](https://github.com/itabbot/learn-mongodb/tree/main/on-demand/mongoose-for-nodejs)

## 3. 系统学习