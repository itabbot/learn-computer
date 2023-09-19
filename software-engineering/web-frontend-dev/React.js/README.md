# React.js<!-- omit in toc -->

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

[官方网站](https://react.dev) | [中文官网](https://zh-hans.react.dev/) | [官方教程](https://react.dev/learn) | [官方参考文档](https://react.dev/reference/react) | [GitHub](https://github.com/facebook/react)

### 1.2. 定义

React（也称为 React.js 或 ReactJS）是一个免费且开源的前端 JavaScript 工具库，用于构建基于组件的用户界面。它由 Meta（以前称为 Facebook）和由个人开发者和公司组成的社群维护。需要注意的是，React 本身只关注用户界面层，它并不是一个完整的应用程序框架。因此，通常需要配合其他库或框架（如 React Router、Redux 等）来构建完整的应用程序。

React 的核心思想是使用声明式的语法来描述用户界面的状态和行为。开发人员可以通过创建 React 组件来定义界面的不同部分，每个组件封装了自己的状态和行为逻辑。这种组件化的开发模式使得代码更加模块化、可维护性更高，并且可以方便地重用组件。

React 采用了虚拟 DOM（Virtual DOM）的概念，它是一个轻量级的表示实际 DOM 结构的 JavaScript 对象树。React 使用虚拟 DOM 来跟踪界面的状态变化，并高效地更新实际 DOM，以提供快速且高效的用户界面渲染。

### 1.3. 背景

React 是由 Facebook 的软件工程师 Jordan Walke 在 2011 年创建的。那时，Facebook 面临着构建复杂、高性能用户界面的挑战，传统的前端开发方式在处理大规模数据更新时效率较低，因为每次更新都需要重新操作实际的 DOM 元素。为了提高性能并改善开发体验，Jordan Walke 开始尝试使用一种新的方式来构建用户界面。他基于 XHP（一种 PHP 扩展）的思想和功能，创建了一个 JavaScript 库，最初命名为 “FaxJS”，后来改名为 React。

发展历程：

- 内部版本： React 在 2011 年首次部署在 Facebook 的 News Feed 上，随后于 2012 年部署在 Instagram 上。初始版本的 React 主要关注于解决 Facebook 内部的前端需求，并采用了虚拟 DOM 的概念来提高性能和渲染效率。
- 开源化： 2013 年 5 月，React 在 JSConf US 宣布开放源代码。React 在开源社区中获得了广泛的关注和采用。这促使了更广泛的贡献者参与其中，为 React 的发展和改进做出了贡献。
- React Native： 2015 年，Facebook 推出了 React Native，这是一个用于构建跨平台移动应用程序的框架。React Native 利用了 React 的组件化思想和虚拟 DOM，使开发人员能够使用 React 的编程模型来构建原生移动应用程序，同时共享大部分代码逻辑。
- Fiber 架构： 2017 年，React 引入了名为 Fiber 的新的内部架构。Fiber 架构的目标是提高 React 的渲染性能和并发能力，以更好地支持交互式应用程序和复杂用户界面。Fiber 架构通过引入异步渲染和协调器的概念，使得 React 能够更好地处理大规模的界面更新和交互。
- Hooks： 2018 年，React 引入了 Hooks API，这是一个重要的改进，使得在函数组件中使用状态和其他 React 功能变得更加简洁和直观。Hooks 允许开发人员在无需编写类组件的情况下，使用和管理 React 的状态、生命周期等特性。
- Concurrent Mode： 2020 年，React 推出了 Concurrent Mode（并发模式），这是一个实验性的特性，旨在进一步提高 React 的并发能力和响应性。Concurrent Mode 允许 React 应用程序在处理大量工作时更好地保持响应，并提供了更细粒度的控制和优先级管理。
- ...

### 1.4. 应用场景

### 1.5. 尝试

## 2. 按需学习

## 3. 系统学习
