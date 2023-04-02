# Vue.js<!-- omit in toc -->

## 1. 快速开始

### 1.1. 相关资源

[中文官网](https://cn.vuejs.org) / [官方文档](https://cn.vuejs.org/guide/introduction.html) / [API 参考](https://cn.vuejs.org/api) / [GitHub](https://github.com/vuejs)

[演练场](https://sfc.vuejs.org/) / [示例](https://cn.vuejs.org/examples/) / [互动教程](https://cn.vuejs.org/tutorial/)

### 1.2. 定义

Vue (发音为 /vjuː/，类似 view) 是一款用于构建用户界面的 JavaScript 框架。它基于标准 HTML、CSS 和 JavaScript 构建，并具有响应性、声明式和组件化等特点。

- 响应性：Vue 会自动跟踪 JavaScript 状态并在其发生变化时响应式地更新 DOM。
- 声明式：Vue 基于标准 HTML 拓展了一套模板语法，使得我们可以[声明式](../../../glossary/声明式与命令式编程.md)地描述最终输出的 HTML 和 JavaScript 状态之间的关系。
- 组件化：Vue 实现了自己的组件模型，使我们可以将 UI 划分为独立的、可重用的部分，并且可以对每个部分进行单独的思考，封装自定义内容与逻辑。

Vue 强调自己是一个 **渐进式的框架**，主要体现在 “灵活性” 和 “可以被逐步集成” 两个特点：

- 灵活性：Vue 的功能覆盖了大部分前端开发常见的需求，但你可以根据自己的需求场景，灵活的只选择使用 Vue 的部分功能。
- 可以被逐步集成：Vue 的核心知识在所有的功能中都是通用的。你可以根据实际的项目演进或个人能力进阶情况，逐步接入 Vue 的各项功能。

### 1.3. 背景

Vue 由尤雨溪（Evan You）创建，于 2014 年发布。尤雨溪之前在 Google 研究过 AngularJS，他声称自己的思路是提取 Angular 中为自己所喜欢的部分，构建出一款相当轻量的框架。

### 1.4. 应用场景

- 独立脚本：Vue 可以以一个单独 JS 文件的形式使用，无需构建步骤！如果你的后端框架已经渲染了大部分的 HTML，或者你的前端逻辑并不复杂，不需要构建步骤，这是最简单的使用 Vue 的方式。在这些场景中你可以将 Vue 看作一个更加声明式的 jQuery 替代品。另外，Vue 也提供了另一个更适用于此类无构建步骤场景的版本 [petite-vue](https://github.com/vuejs/petite-vue)。

- 作为 Web Component 嵌入：你可以用 Vue 来构建标准的 Web Component，这些 Web Component 可以嵌入到任何 HTML 页面中，无论它们是如何被渲染的。这个方式让你能够在不需要顾虑最终使用场景的情况下使用 Vue：因为生成的 Web Component 可以嵌入到旧应用、静态 HTML，甚至用其他框架构建的应用中。

- 单页面应用 (SPA)：一些应用在前端需要具有丰富的交互性、较深的会话和复杂的状态逻辑。构建这类应用的最佳方法是使用这样一种架构：Vue 不仅控制整个页面，还负责处理抓取新数据，并在无需重新加载的前提下处理页面切换。这种类型的应用通常称为单页应用 (Single-Page application，缩写为 SPA)。

- 服务端渲染 (SSR)：纯客户端的 SPA 在首屏加载和 SEO 方面有显著的问题，因为浏览器会收到一个巨大的 HTML 空页面，只有等到 JavaScript 加载完毕才会渲染出内容。Vue 提供了一系列 API，支持将一个 Vue 应用在服务端渲染成 HTML 字符串。这能让服务器直接返回渲染好的 HTML，让用户在 JavaScript 下载完毕前就看到页面内容。Vue 之后会在客户端对应用进行 “激活 (hydrate)” 使其重获可交互性。这被称为服务端渲染 (SSR)，它能够极大地改善应用在 Web 核心指标上的性能表现，如最大内容绘制 (LCP)。Vue 生态中有一些针对此类场景的、基于 Vue 的上层框架，比如 [NuxtJS](https://nuxt.com/)，能让你用 Vue 和 JavaScript 开发一个全栈应用。

- 静态站点生成 (SSG/JAMStack)：如果所需的数据是静态的，那么服务端渲染可以提前完成。这意味着我们可以将整个应用预渲染为 HTML，并将其作为静态文件部署。这增强了站点的性能表现，也使部署变得更容易，因为我们无需根据请求动态地渲染页面。Vue 仍可通过激活在客户端提供交互。这一技术通常被称为静态站点生成 (SSG)，也被称为 JAMStack。Vue 团队也维护了一个名为 [VitePress](https://vitepress.dev/) 的静态站点生成器，另外，[NuxtJS](https://nuxt.com/) 也支持 SSG。

- Web 之外：尽管 Vue 主要是为构建 Web 应用而设计的，但它绝不仅仅局限于浏览器。

  - 配合 [Electron](https://www.electronjs.org) 或 [Tauri](https://tauri.app) 构建桌面应用。
  - 配合 [Ionic Vue](https://ionicframework.com/docs/vue/overview) 构建移动端应用。
  - 使用 [Quasar](https://quasar.dev) 用同一套代码同时开发桌面端和移动端应用。
  - 使用 Vue 的自定义渲染 API 来构建不同目标的渲染器，比如 [WebGL](https://troisjs.github.io/) 甚至是[终端命令行](https://github.com/vue-terminal/vue-termui)！

### 1.5. 实践

## 2. 按需学习

## 3. 系统学习
