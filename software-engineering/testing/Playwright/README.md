# Playwright<!-- omit in toc -->

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

[官方网站](https://playwright.dev) | [官方文档](https://playwright.dev/docs/intro) | [API 参考](https://playwright.dev/docs/api/class-playwright) | [GitHub](https://github.com/microsoft/playwright)

### 1.2. 定义

Playwright 是一个由 Microsoft 开发的开源自动化测试工具，是专门为满足 Web 应用程序端到端测试的需求而创建的。具有以下特点：

- 跨浏览器支持： 支持 Chromium、Firefox 和 WebKit 渲染引擎，允许开发人员在不同的浏览器上执行测试。
- 跨平台： 支持在 Windows、macOS 和 Linux 等不同操作系统上运行测试。
- 支持多种语言： 可以使用多种编程语言（如 JavaScript、TypeScript、Python、.NET、Java）编写测试脚本。
- 自动化能力： 能够模拟用户的操作行为（如点击、填写表单等），且支持无头模式（headless，无可见浏览器界面），以进行全面的自动化测试。
- 录制能力： 可以记录用户在浏览器上的操作（如点击、输入、导航等），然后生成对应的代码脚本。这样，就能够在录制操作后回放这些操作，或者根据需要进行调整并进一步完善自动化测试脚本。
- 调试能力： 提供丰富的调试功能，帮助开发人员快速定位和解决测试脚本中的问题。
- 回溯能力： 运行过程中可以生成页面截图和录制视频，便于对测试用例进行视觉验证。
- 支持移动端： 可以进行移动端应用的自动化测试。

### 1.3. 背景

随着 Web 技术的迅猛发展，特别是浏览器引擎的多样化和复杂化，Microsoft 意识到需要一种能够适应这种变化的自动化测试工具。因此，他们决定开发一种全面支持跨浏览器、跨平台的自动化测试工具，以满足开发人员对现代 Web 应用程序测试的需求。

Playwright 最初是在 2019 年发布的，经过多年的研发和改进，逐渐成为了一种广泛受到欢迎的自动化测试解决方案。它不断扩展功能，提高稳定性，与开发人员和测试人员的真实需求保持紧密联系。同时，它还不断加强与现有测试框架的集成和对移动端自动化测试的支持，使得它成为一个功能强大、灵活且易于使用的工具。

### 1.4. 应用场景

Playwright 在以下典型场景中广泛应用：

- 浏览器自动化测试： 用于编写和运行端到端测试、集成测试和单元测试，以验证 Web 应用程序在不同浏览器和设备上的行为。
- 网页截图和 PDF 生成： 用于捕获网页截图和生成 PDF，可用于创建报告、监视页面状态和调试。
- 数据爬取（Web scraping）： 可用于构建自动化的数据爬取工具，从网页上提取信息并进行自动化处理。
- 性能监测： 可以用于模拟用户行为，对 Web 应用程序的性能进行监测和分析。
- 跨浏览器测试： 通过支持多种浏览器，可以进行跨浏览器的测试和验证，确保 Web 应用在不同浏览器上的兼容性。

### 1.5. 尝试

- [初始化 Playwright 项目，并体验其基本功能](https://github.com/itabbot/learn-playwright/tree/main/quick-start/init)

## 2. 按需学习

## 3. 系统学习
