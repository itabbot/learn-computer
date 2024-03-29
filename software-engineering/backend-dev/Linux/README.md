# Linux<!-- omit in toc -->

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

[内核官网](https://www.kernel.org/) | [内核文档](https://docs.kernel.org) | [内核维基](https://www.wiki.kernel.org) | [内核源码](https://github.com/torvalds/linux) | [GNU](https://www.gnu.org)  
[Ubuntu](https://ubuntu.com/) | [Fedora](https://fedoraproject.org/) | [Arch](https://archlinux.org/) | [Mint](https://linuxmint.com/) | [Debian](https://www.debian.org/) | [Red Hat](https://www.redhat.com/) | [OpenSUSE](https://www.opensuse.org/) | [SUSE](https://www.suse.com/)

### 1.2. 定义

Linux 通常是指 “_Linux 操作系统_”，它是一个基于 “_Linux 内核_” 并加上支撑内核的系统工具和库所构成的自由、开源的 “[类 Unix](../../../glossary/类Unix操作系统.md)” 操作系统。通常情况下，Linux 被打包成供不同使用场景的 Linux 发行版。

- Linux 内核： 是 Unix 操作系统的克隆，由 [Linus Torvalds](https://github.com/torvalds) 在网络上松散的黑客团队的协助下从头开始编写。它旨在符合 POSIX 和单一 UNIX 规范。
- Linux 发行版： 为不同使用场景预先集成好的 Linux 操作系统。一般在直接安装后只需小幅度更改设置就可以使用。常见的发行版有 Ubuntu、Fedora、Arch、Mint、Red Hat、OpenSUSE、SUSE 等等。

### 1.3. 背景

发展历程：

- UNIX 操作系统： 是美国 AT&T 公司贝尔实验室在 1969 年完成的操作系统，于 1971 年首次发布。Unix 最初是自由和开放源代码的操作系统，在贝尔实验室内部和学术界广泛使用和传播。随着 Unix 的商业化和市场化，贝尔实验室开始将 Unix 作为专有产品销售，法律上不允许用户对其进行修改。
- Minix 操作系统： Minix 由计算机科学教授 Andrew S. Tanenbaum 创建的类 UNIX 操作系统，于 1987 年发布。它是为了教授操作系统原理而设计的，只面向学生和其他想要学习操作系统原理的人，不允许被用作任何商业使用。
- GNU 计划： 1983 年，Richard Stallman 创立 GNU 计划。这个计划的目标是发展一个完全自由的类 Unix 操作系统。Richard Stallman 在 1985 年发起自由软件基金会，并于 1989 年编写了 GNU 通用公共许可证（GNU GPL）。到了 20 世纪 90 年代初期，操作系统中所需的许多程序（例如库、编译器、文本编辑器、命令行 shell 和窗口系统）已经完成。但是诸如设备驱动程序、守护程序和称为 GNU Hurd 的内核都停滞不前且不完整。Linus Torvalds 曾说过如果 GNU 内核在 1991 年时可以用，他就不会自己去写一个。
- Linux 创立： Linux 的开发始于 1991 年，当时 Linus Torvalds 是一名赫尔辛基大学的计算机科学学生，他一直在使用 Minix 操作系统进行学习和工作，但是，他对 Minix 的一些限制和局限感到不满，例如 Minix 的代码无法自由地修改和分发，而且 Minix 功能相对较为简单。于是，Linus Torvalds 决定着手开发一个自己的操作系统，以满足自己的需求。他使用 Minix 操作系统作为参考和基础，但在设计上采用了自己的思路和方法。
- Linux 的发展： 尽管早期版本的功能有限，Linux 仍迅速获得了开发者和用户。Linus Torvalds 于 1992 年发起将其原始许可证（禁止商业再分发）转换为 GNU 通用公共许可证 (GPLv2)，使得 Linux 成为一个真正意义上的自由和开放源代码的操作系统。GNU 项目很快也采用了 Linux 内核，当时的 BSD 尚未摆脱法律束缚，也没有参与免费操作系统内核的竞争。1992 年底，GNU 项目的开发者们开始将 GNU 工具集移植到 Linux 内核上，并在短时间内取得了一些成功。接着，他们开始将更多的 GNU 工具集和应用程序移植到 Linux 内核上，最终形成了一个完整的自由 Unix 操作系统。1993 年初，GNU/Linux 项目正式发布了第一个版本，即 Debian 0.91。
- Linux 现状： 如今，在 Linus Torvalds 的带领下，众多开发人员共同参与开发和维护 Linux 内核。Richard Stallman 领导的自由软件基金会，继续提供大量支持 Linux 内核的 GNU 组件。一些个人和企业开发的第三方的非 GNU 组件也提供对 Linux 内核的支持。Linux 社区或企业都推出一些重要的 Linux 发行版。Linux 已经成为了全球最流行的服务器操作系统之一。

命名：

- 最初 Linus Torvalds 称这个内核的名称为 “Freax”，意思是自由（free）和奇异（freak）的结合字，并且附上 “X” 以配合所谓的类 Unix 的系统。但是 FTP 服务器管理员 Ari Lemmke 并不认为 “Freax” 是一个好名字，因此他在没有咨询 Torvalds 的情况下将服务器上的项目命名为 “Linux”。后来 Torvalds 也同意了 “Linux”。
- 由于支持用户空间的系统工具和库主要由 GNU 计划提供，自由软件基金会提议将其组合命名为 GNU/Linux，但 Linux 不属于 GNU 计划，这个名称并没有得到社群的一致认同。

### 1.4. 应用场景

Linux 操作系统具有广泛的应用场景，以下是其中一些典型的应用场景：

- 服务器： Linux 作为服务器操作系统的应用非常广泛，包括 Web 服务器、数据库服务器、邮件服务器、文件服务器等。Linux 服务器具有高度的稳定性、可靠性和安全性，而且支持大量的并发用户和请求，可以满足高性能、高可用和高可扩展性的需求。
- 超级计算机： Linux 是用于超级计算机的主流操作系统，它可以提供高性能和高并发的计算能力，支持复杂的科学计算和仿真任务。Linux 还支持 InfiniBand 和其他高速网络技术，可以实现高速数据传输和分布式计算。
- 移动设备： Linux 也被广泛应用于移动设备，包括智能手机、平板电脑、嵌入式设备等。Linux 内核支持多种处理器架构和移动设备的硬件，而且具有良好的电池寿命和性能表现。
- 桌面计算机： 虽然 Linux 在桌面计算机上的应用相对较少，但也有很多人使用 Linux 作为桌面操作系统，尤其是在科学计算、软件开发、网络安全等领域。Linux 桌面操作系统具有高度的自定义性和可扩展性，而且可以免费获取和使用。
- 嵌入式系统： Linux 还被广泛应用于嵌入式系统，包括智能家居、工业自动化、医疗设备、车载娱乐等。Linux 内核可以针对不同的硬件进行定制和优化，而且具有灵活的驱动程序和系统组件，可以满足多样化的嵌入式应用需求。
- 虚拟化： Linux 提供了多种虚拟化技术，包括 KVM、Xen、VirtualBox、Docker 等，可以实现虚拟化服务器、虚拟化桌面、容器化应用等。Linux 虚拟化技术具有高效、可靠、安全等优点，可以提高 IT 资源的利用率和灵活性。
- 云计算： Linux 作为云计算基础设施的重要组成部分，可以提供云服务器、云存储、云数据库、云安全等服务。Linux 还支持多租户、弹性扩展、自动化管理等特性，可以满足云计算的高效、可靠、安全等需求。

### 1.5. 尝试

- [在 Windows 中使用 Docker 安装 Linux 操作系统](https://github.com/itabbot/learn-linux/tree/main/quick-start/install-linux-docker-win)
- [完全使用 Linux 操作系统进行开发和工作](https://github.com/itabbot/learn-linux/tree/main/quick-start/develop-work-with-linux)

## 2. 按需学习

- [问题：蓝灯无法自动管理系统代理](https://github.com/itabbot/learn-linux/tree/main/on-demand/cannot-manage-proxy)

## 3. 系统学习
