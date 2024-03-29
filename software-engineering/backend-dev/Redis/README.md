# Redis<!-- omit in toc -->

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

[官方网站](https://redis.io) | [官方文档](https://redis.io/docs) | [指令参考](https://redis.io/commands) | [官方推荐资源](https://redis.io/resources/) | [GitHub](https://github.com/redis)

### 1.2. 定义

Redis，英文全称 Remote Dictionary Server，即远程字典服务。它是一个开源（采用 BSD 许可证）的内存数据结构存储系统，可用作键值数据库、缓存、消息代理和流引擎。具有以下核心能力：

- 支持的数据结构： 字符串、哈希表、列表、集合、带有范围查询的有序集合、位图、HyperLogLog、地理空间索引和流等等。
- 原子操作： Redis 的命令都是原子操作，即在执行期间，其他命令不会同时执行，从而保证了数据的完整性和一致性。
- 支持事务： 支持按顺序执行一组命令，并在期间不会执行其他的命令，保证了事务（一组命令）操作的原子性。但是不支持回滚。
- 支持持久化： 可以将所有写操作持久化到永久存储介质（多种级别），以便在重新启动和系统故障时恢复数据。
- 键驱逐机制： 在内存空间不足时，根据一定的策略自动淘汰一些键值对数据，以释放内存空间给新的数据使用。
- 可编程性： 使用 Lua 进行服务器端脚本编写和使用 Redis Functions 进行服务器端存储过程。
- 支持外部模块： 提供模块 API，用于在 C、C++和 Rust 中构建自定义的扩展 Redis 的功能。
- 高扩展性： 通过基于哈希的分片实现水平扩展性，在扩展集群时可以自动进行重新分片，从而实现扩展到数百万个节点的规模。
- 高可用性： 针对独立部署和集群部署，具备自动故障切换的复制功能。

Redis 拥有大多数编程语言的客户端库，可以与各种应用程序和系统集成。

Redis 采用 ANSI C 编写，适用于大多数 POSIX 系统，如 Linux、\*BSD 和 Mac OS X，且无需外部依赖。Linux 和 OS X 是 Redis 开发和测试最多的两个操作系统，官方推荐使用 Linux 进行部署。另外，官方没有对 Windows 版本进行支持。

### 1.3. 背景

Redis 是由意大利软件工程师 Salvatore Sanfilippo（昵称 [antirez](https://github.com/antirez)）于 2009 年创建，他的初衷是为了解决他的初创公司的一个日志收集系统 LLOOGG 的性能问题，后来慢慢就演变成了 Redis。发展阶段：

- 初始阶段： Redis 最初由 Salvatore Sanfilippo 作为个人项目开发和维护，他将其开源并在开源社区中获得了广泛的关注和采用。
- VMware 赞助： 2010 年 3 月，Sanfilippo 被 VMware 聘用并专注于 Redis 的开发。
- Pivotal 赞助： 2013 年 5 月，Redis 得到了 Pivotal Software（VMware 的衍生公司）的赞助，这为 Redis 的持续发展提供了支持。
- Redis Labs 赞助： 2015 年，Redis Labs 聘请了 Salvatore Sanfilippo。Redis Labs 是一家专注于 Redis 的商业公司，它为 Redis 提供了商业化支持、开发和推广，使其能够持续发展并提供各种增值功能和服务。尽管如此，Redis 仍然是一个开源项目，其源代码仍然可以在 GitHub 上进行访问和贡献。
- 作者离开： 2020 年 6 月，Salvatore Sanfilippo 辞去了 Redis 维护者的职务，而 Redis Labs 则持续支持 Redis 的治理等工作。

### 1.4. 应用场景

Redis 具有广泛的应用场景，比如：

- 缓存： Redis 作为内存数据库，具有快速读写速度，可用于缓存常用数据，从而提高应用程序的性能和响应速度。
- 消息队列： Redis 的发布订阅功能和列表数据结构可用于构建高效的消息队列系统，实现异步消息传递和解耦应用组件。
- 分布式锁： Redis 的原子操作和分布式特性使其成为实现分布式锁的理想选择，用于协调多个进程或服务之间的互斥访问。
- 实时统计和计数器： Redis 的计数器数据结构和持久化功能可用于实时统计和计数，如网站访问量统计、在线用户数等。
- 实时排行榜： Redis 的有序集合（Sorted Set）可以用于存储和更新实时排行榜数据，如游戏中的玩家积分排名、社交媒体的热门帖子等。
- 地理位置服务： Redis 的地理位置数据类型（Geospatial）可以用于存储和查询地理位置信息，如附近的商店、地点推荐等。
- 会话管理： Redis 可以用于存储和管理用户会话数据，如登录状态、购物车信息等，实现跨请求的会话共享。

### 1.5. 尝试

- [使用 Docker 安装 Redis](https://github.com/itabbot/learn-redis/tree/main/quick-start/install-in-docker)
- [使用 Redis 命令行界面体验最简单的 Redis 操作](https://github.com/itabbot/learn-redis/tree/main/quick-start/experience-with-reddiscli)
- [体验 Redis 官方可视化工具 RedisInsight](https://github.com/itabbot/learn-redis/tree/main/quick-start/experience-redisInsight)

## 2. 按需学习

## 3. 系统学习
