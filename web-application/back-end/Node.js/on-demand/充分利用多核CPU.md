# 充分利用多核 CPU<!-- omit in toc -->

- [1. 场景](#1-场景)
- [2. 方案](#2-方案)
- [3. 尝试](#3-尝试)

## 1. 场景

Node.js 使用的是单线程模型，无法充分利用多核 CPU 的计算能力，限制了应用程序的整体性能：

- 应用阻塞： 当执行长时间运行的操作（如计算密集型任务或大量的同步 I/O 操作）时，单线程的 Node.js 应用可能会被阻塞，导致其他请求无法及时得到响应。
- 并发限制： Node.js 单线程模型的特性意味着只能发挥单个 CPU 的计算能力，限制了并发连接数。
- 异常影响： 在单线程模型下，一个未捕获的异常可能会导致整个应用程序的崩溃。

## 2. 方案

Node.js 的单线程事件循环模型在处理 I/O 密集型任务方面非常高效。只有在处理计算密集型任务或需要更高并发处理能力时，才需要考虑利用多个 CPU 核心。选择合适的方法取决于应用程序的需求和特点，需要根据实际情况选择最适合的方式：

- Cluster 模块： Node.js 的 Cluster 模块允许创建一个基于多进程的集群环境。它可以创建多个子进程来并行处理请求，并通过负载均衡将请求分配给不同的子进程。每个子进程可以运行一个独立的 Node.js 实例，共享服务器的端口。这种方式在处理高并发的应用程序情况下特别有效。
- Child Process 模块： Node.js 的 Child Process 模块允许创建和管理子进程。通过创建多个子进程，每个子进程可以运行一个独立的 Node.js 实例，从而实现并行处理。可以使用 Child Process 模块中的 fork 方法来创建子进程，并通过进程间通信实现任务分配和协同工作。
- Worker Threads 模块： Node.js 的 Worker Threads 模块允许创建和管理多个线程。可以使用 Worker Threads 模块来将 CPU 密集型的任务分配给多个线程并行执行，从而利用多个 CPU 核心。这在需要进行大量计算的情况下特别有用。
- 进程管理工具： 还可以使用一些进程管理工具，如 PM2，来运行和管理多个 Node.js 实例。这些工具可以自动创建多个 Node.js 实例，并根据负载情况进行负载均衡，从而充分利用多个 CPU 核心。
- 多线程库： 尽管 Node.js 是单线程的，但可以使用一些允许多线程的库来利用多个 CPU 核心。例如，Node.js 中的 `node-addon-api` 和 `N-API` 允许开发者使用 C/C++ 编写扩展模块，在扩展模块中可以创建和管理多个线程。

## 3. 尝试

- [最简单的 Cluster 模块应用程序](https://github.com/itabbot/learn-nodejs/tree/main/on-demand/simplest-cluster-app)
- [最简单的 PM2 应用实践](https://github.com/itabbot/learn-nodejs/tree/main/on-demand/simplest-pm2-practice)
