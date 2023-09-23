# Vite<!-- omit in toc -->

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

[官方网站](https://vitejs.dev) | [中文官网](https://cn.vitejs.dev) | [官方教程](https://vitejs.dev/guide) | [配置参考](https://vitejs.dev/config) | [常用插件](https://vitejs.dev/plugins)  
[GitHub](https://github.com/vitejs) | [Awesome-Vite](https://github.com/vitejs/awesome-vite)

### 1.2. 定义

Vite（法语意为 “快速的”，发音 `/vit/`，发音同 “veet”）是一个面向 Web 开发的构建工具，旨在于提供快速的开发体验和优化的生产构建。

- 快速的开发体验： 内置开发服务器并通过快速冷启动、模块热更新（ES Module HMR）、浏览器缓存等机制，提供即时的开发体验。
- 优化的生产构建： 通过代码压缩、按需加载、浏览器兼容、自动预加载等机制，输出用于生产的高度优化过的静态资源。

### 1.3. 背景

Vite 是[尤雨溪](https://github.com/yyx990803)（英文名 Evan You；Vue 的作者）创建的。那时的 Vue.js 还处在 2.x 版本阶段，尤雨溪发现在开发过程中，由于传统的打包工具（如 webpack）需要进行耗时的构建操作，开发者在每次修改代码后需要等待较长时间的重新构建过程，这对于开发效率产生了一定的影响。为了解决这个问题，尤雨溪在 2019 年开始尝试构思一个新的开发模式和构建工具。他首先创建了一个名为 “Playground” 的原型项目，用于尝试新的构建思路。这个原型项目后来发展成了 Vite。

主要阶段：

- Vite 1.x： Vite 的第一个版本（1.x）于 2020 年底发布。Vite 1.x 使用了基于浏览器原生 ES 模块的开发模式，通过利用浏览器的原生模块加载能力，实现了快速的冷启动和热模块重载。Vite 1.x 主要用于 Vue.js 3.x 的开发。
- Vite 2.x： Vite 2.x 在 2021 年初发布，除了继续支持 Vue.js，还增加了对 React 和 Preact 等框架的支持。Vite 2.x 引入了 Rollup 作为构建引擎，并在构建性能和稳定性方面进行了改进。
- 社区支持和发展： Vite 在发布后得到了广泛的关注和认可，吸引了大量的开发者使用和贡献。Vite 社区积极推动插件生态的发展，提供了丰富的插件来扩展 Vite 的功能。

### 1.4. 应用场景

- Vue.js 应用开发： Vite 最初是为 Vue.js 设计的，因此在开发 Vue.js 应用时，Vite 是一个理想的选择，它提供了内置的 Vue.js 支持。
- 其他框架应用开发： Vite 也提供了对 React、Preact、Lit、Svelte、Solid 等框架的支持。
- 静态网站生成器： Vite 可以与静态网站生成器如 VuePress、Gridsome 等配合使用，用于构建快速、现代化的静态网站。Vite 的快速构建能力可以提高静态网站生成过程的效率。
- 原型开发和快速迭代： 由于 Vite 的快速冷启动和热模块重载功能，它非常适合用于原型开发和快速迭代。开发者可以快速创建原型，实时查看和调试变化，并迅速迭代和验证设计概念。

### 1.5. 尝试

- [使用官方脚手架创建一个最简单的 Vite 项目](https://github.com/itabbot/learn-vite/tree/main/quick-start/simplest-vite)
- [使用官方脚手架创建一个 Vite + React 项目](https://github.com/itabbot/learn-vite/tree/main/quick-start/vite-react)

## 2. 按需学习

## 3. 系统学习
