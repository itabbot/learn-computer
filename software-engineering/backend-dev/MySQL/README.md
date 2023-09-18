# MySQL<!-- omit in toc -->

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

[官方网站](https://www.mysql.com) | [官方文档](https://dev.mysql.com/doc) | [官方开发者专区](https://dev.mysql.com) | [GitHub](https://github.com/mysql)

### 1.2. 定义

MySQL 是一种开源的[关系型数据库](../../../glossary/关系型与非关系型数据库.md)管理系统（RDBMS），使用 C 和 C++ 编写，使用结构化查询语言（SQL）进行数据管理。它的名字是其联合创始人 Michael Widenius 的女儿的名字 “My” 和结构化查询语言的缩写 “SQL” 的组合。MySQL 由于性能高、成本低、可靠性好，已经成为最流行的开源数据库之一，因此被广泛地应用在 Internet 上的中小型网站中；随着 MySQL 的不断成熟，它也逐渐用于更多大规模网站和应用。

### 1.3. 背景

- 创建： 1994 年，芬兰人 Michael Widenius（也称为 Monty）和瑞典人 David Axmark 为了满足他们自己在 Web 应用程序开发中的需求，共同创建了 MySQL 并创立了 MySQL AB 公司，总部位于瑞典的乌普萨拉（Uppsala）。
- 首个公开版本： 1995 年 5 月 23 日，MySQL 1.0 版本发布，成为第一个公开发布的 MySQL 版本。
- 商业许可版本： 2001 年，MySQL AB 公司推出了商业许可版本的 MySQL，为企业提供了额外的支持和服务。
- Sun 收购： 2008 年，Sun Microsystems 收购了 MySQL AB 公司，将 MySQL 纳入其产品线。
- Oracle 收购： 2010 年，Oracle Corporation 收购了 Sun Microsystems，继续承担 MySQL 的发展和维护工作。
- MariaDB 分支： 2010 年，Oracle Corporation 收购了 Sun Microsystems，这也包括了 MySQL。Monty 对 Oracle 对 MySQL 的掌控权表示担忧，担心 Oracle 可能会限制 MySQL 的开放性和发展。因此，他决定创建 MariaDB 作为 MySQL 的一个兼容分支，以保护 MySQL 的开源性和继续推动其发展。MariaDB 基于与 MySQL 服务器 5.5 相同的代码库，旨在保持与 Oracle 提供的版本的兼容性。
- 5.6 版本： 2013 年 2 月 5 日，MySQL 5.6 版本发布，带来了更高的性能、可扩展性和可靠性，包括 InnoDB 存储引擎的改进和新的复制特性等。
- 5.7 版本： 2015 年 10 月 21 日，MySQL 5.7 版本发布，引入了 JSON 数据类型、更强大的查询优化和性能改进、多源复制等功能。
- 8.0 版本： 2018 年 4 月 19 日，MySQL 直接跳过主版本号 6 和 7，发布了 8.0 版本，带来了许多重要的改进，包括更好的性能、事务持久性、JSON 支持和更强大的安全性特性等等。

### 1.4. 应用场景

MySQL 最典型的应用场景之一是作为 Web 应用程序的后端数据库：

- 网站和博客： MySQL 广泛用于存储和管理网站和博客的数据。它可以存储用户信息、文章内容、评论、标签和其他相关数据，并支持复杂的查询和搜索操作。
- 电子商务： 许多电子商务网站使用 MySQL 来管理产品目录、订单信息、用户账户、购物车和支付数据。MySQL 的稳定性和可靠性使其成为处理大量交易和数据的理想选择。
- 社交媒体平台： MySQL 被广泛用于社交媒体平台，如社交网络、论坛和社区网站。它用于存储用户信息、关系图谱、帖子、评论、消息和通知等数据。
- 内容管理系统（CMS）： 许多流行的 CMS，如 WordPress、Drupal 和 Joomla 等，使用 MySQL 作为其后端数据库来存储和管理网站的内容、用户、页面结构和配置信息。
- 在线论坛和协作平台： MySQL 用于存储和管理在线论坛、协作平台和知识库的帖子、评论、用户信息、权限和搜索索引等数据。
- 新闻和媒体网站： MySQL 被新闻和媒体网站用于存储和管理文章、新闻、图片、视频、评论和用户交互等数据。
- 基于位置的服务：MySQL 可用于存储和处理地理位置数据，使其成为基于位置的服务（如地图应用、定位服务和位置分析）的关键组成部分。

### 1.5. 尝试

- [使用 Docker 安装 MySQL](https://github.com/itabbot/learn-mysql/tree/main/quick-start/install-in-docker)
- [使用 MySQL 命令行界面体验最简单的 MySQL 操作](https://github.com/itabbot/learn-mysql/tree/main/quick-start/experience-with-cli)

## 2. 按需学习

## 3. 系统学习
