# Docker<!-- omit in toc -->

[官方网站](https://www.docker.com/) | [入门指引](https://docs.docker.com/get-started/overview/) | [参考文档](https://docs.docker.com/reference/) | [GitHub](https://github.com/docker)

# 目录<!-- omit in toc -->

- [1. 概述](#1-概述)
- [2. 底层技术](#2-底层技术)
- [3. 架构](#3-架构)
- [4. 常用操作](#4-常用操作)
- [5. Containerd](#5-containerd)

## 1. 概述

Docker 是一个开源的、用 Go 编程语言编写的容器引擎（有时也泛指整个 Docker 项目）。它让开发者可以打包他们的应用程序以及依赖包到一个镜像中，然后在任何流行的 Linux 或 Windows 操作系统的机器上以容器的形式运行。Docker 容器有以下特点：

- 可移植：可以将镜像从一个计算环境传输到另一个计算环境运行，支持 Linux 和 Windows 操作系统。
- 一致性：由于容器的标准化，它们始终以相同的方式运行，无视基础设施（计算机环境等）的差异。
- 多实例：在一台机器上可以运行多个容器。
- 隔离性：容器在运行时相互独立互不干扰。
- 可分配：可以给容器分配指定的计算机资源。
- 轻量级：相较于虚拟机来说，启动速度更快，占用的资源更少。

因为容器的各种优点，所以它为软件开发提供了非常多的便利：

- 在 Windows 环境开发时，可以使用 Docker 安装一些 Linux 支持较好的组件。
- 当团队有新成员加入时，可以共享开发环境配置，新加入的成员也可以快速地配置开发环境。
- 可以让开发、测试以及生产环境保存一致，避免环境差异造成的故障。
- 提高部署效率，一次配置多个环境可复用。
- 可以在本地允许多个容器进行试验，结束后还可以快速销毁，而不用担心破坏宿主环境。
- 容器的轻量级特性，支持我们可以动态、频繁地进行部署更新。
- 容器的轻量级特性，也使我们可以高效地进行扩缩容。
- 通过多个容器，一台机器可以跑多个服务，因此在本机就可以模拟出微服务架构。

## 2. 底层技术

Docker 容器以一种特殊进程的方式运行于宿主机上，它依赖于 liunx 内核特性：namespace（名字空间进行资源的隔离）和 cgroups（限制、记录任务组所使用的物理资源）。

- NameSpace：我们知道 Linux 中的 PID、IPC、网络等资源是全局的，而 NameSpace 机制是一种资源隔离方案，在该机制下这些资源就不再是全局的了，而是属于某个特定的 NameSpace，各个 NameSpace 下的资源互不干扰，这就使得每个 NameSpace 看上去就像一个独立的操作系统一样。
- Control groups：虽然有了 NameSpace 技术可以实现资源隔离，但进程还是可以不受控的访问系统资源，比如 CPU、内存、磁盘、网络等，为了控制容器中进程对资源的访问，Docker 采用 control groups 技术（也就是 cgroup），有了 cgroup 就可以控制容器中进程对系统资源的消耗了，比如你可以限制某个容器使用内存的上限、可以在哪些 CPU 上运行等等。

Docker 容器和虚拟机具有类似的资源隔离和分配优势，但二者在原理上不同，因为容器是将操作系统层虚拟化，虚拟机则是虚拟化硬件。因此容器更具有便携性、高效地利用服务器。

- 容器镜像的大小往往只需要数十 MB，而虚拟机的副本通常达到数十 GB，
- 因为虚拟机包含了完整的操作系统，所以启动的速度也很慢（数分钟），而容器几乎是瞬时启动。
- 虚拟机运行时动辄几 G 的内存占用，容器运行时只需数 M 的内存空间。

## 3. 架构

Docker 使用 “客户端-服务器” 架构。Docker 客户端与 Docker 守护进程对话，后者负责构建、运行和分发 Docker 容器的繁重工作。Docker 客户端和守护进程可以在同一系统上运行，或者您可以将 Docker 客户端连接到远程 Docker 守护进程。Docker 客户端和守护进程使用 REST API 通过 UNIX 套接字或网络接口进行通信。另一个 Docker 客户端是 Docker Compose，它允许您处理由一组容器组成的应用程序。

- Docker 守护进程（dockerd）：侦听 Docker API 请求并管理 Docker 对象，例如镜像、容器、网络和卷。守护进程还可以与其他守护进程通信以管理 Docker 服务。
- Docker 客户端（docker）：是许多 Docker 用户与 Docker 交互的主要方式。当您使用诸如 `docker run` 之类的命令时，客户端会将这些命令发送到 dockerd，由后者执行。该 docker 命令使用 Docker API。Docker 客户端可以与多个守护进程通信。
- Docker 注册中心：存储 Docker 镜像。Docker Hub 是一个任何人都可以使用的公共注册中心，Docker 默认配置为在 Docker Hub 上查找镜像。您甚至可以运行自己的私有注册中心。
- 镜像：是一个只读模板，其中包含创建 Docker 容器的说明。您可以创建自己的镜像，也可以只使用其他人创建并在注册中心中发布的镜像。
  - 通常，一个镜像基于另一个镜像，带有一些额外的定制。例如，您可以构建一个基于镜像的 ubuntu 镜像，但安装 Apache Web 服务器和您的应用程序，以及使您的应用程序运行所需的配置详细信息。
  - 要构建您自己的镜像，您可以使用简单的语法创建一个 Dockerfile ，用于定义创建和运行镜像所需的步骤。Dockerfile 中的每条指令都会在镜像中创建一个层。当您更改 Dockerfile 并重建镜像时，只会重建那些已更改的层。与其他虚拟化技术相比，这是使镜像如此轻巧、小巧和快速的部分原因。
- 容器：是镜像的可运行实例。您可以使用 Docker API 或 CLI 创建、启动、停止、移动或删除容器。您可以将一个容器连接到一个或多个网络，将存储附加到它，甚至可以根据其当前状态创建一个新镜像。
  - 默认情况下，容器与其他容器及其主机隔离得相对较好。您可以控制容器的网络、存储或其他底层子系统与其他容器或主机的隔离程度。
  - 容器由其镜像以及您在创建或启动它时提供给它的任何配置选项定义。当容器被移除时，任何未存储在持久存储中的状态更改都会消失。
- Docker 桌面：是一个易于安装的应用程序，适用于您的 Mac、Windows 或 Linux 环境，使您能够构建和共享容器化应用程序和微服务。Docker 桌面包括 Docker 守护程序（dockerd）、Docker 客户端（docker）、Docker Compose、Docker Content Trust、Kubernetes 和 Credential Helper。

如下图所示，客户端发送 `docker build` 命令，生成镜像，还可以执行 `docker pull` 命令从注册中心下载他人共享的镜像。执行 `docker run` 命令，镜像运行起来后就是容器。

<img src="./imgs/Docker架构图.svg" width="800"  alt="Docker架构图"/>

## 4. 常用操作

- 镜像

  - 打包镜像：首先根据需要编写 [Dockerfile](https://docs.docker.com/engine/reference/builder/) 文件，其中包含构建镜像的所有指令，然后执行 [`docker build`](https://docs.docker.com/engine/reference/commandline/build/) 命令。

- 容器

  - 启动容器（运行镜像）：[`docker run`](https://docs.docker.com/engine/reference/commandline/run/)。

  - 列出容器：[`docker ps`](https://docs.docker.com/engine/reference/commandline/ps/)。会显示容器的 ID。默认只列出运行中的容器，可以添加 `--all, -a` 选项显示所有容器。

  - 停止容器：[`docker stop <容器ID>`](https://docs.docker.com/engine/reference/commandline/stop/)。

  - 移除容器：[`docker rm <容器ID>`](https://docs.docker.com/engine/reference/commandline/ps/)。当容器处于运行中状态时不允许移除，此时可以添加 `--force, -f` 选项进行强制移除。

  - 在容器中运行指令：[`docker exec <容器ID> <指令>`](https://docs.docker.com/engine/reference/commandline/exec/)。

- 卷

  - 创建卷：[` docker volume create <卷名>`](https://docs.docker.com/engine/reference/commandline/volume_create/)。

  - 查看卷信息：[`docker volume inspect <卷名>`](https://docs.docker.com/engine/reference/commandline/volume_inspect/)。

  - 列出卷：[`docker volume ls`](https://docs.docker.com/engine/reference/commandline/volume_ls/)。

  - 移除卷：[`docker volume rm <卷名>`](https://docs.docker.com/engine/reference/commandline/volume_rm/)。

- 网络

  - 创建网络：[` docker network create <网络名>`](https://docs.docker.com/engine/reference/commandline/network_create/)。

  - 连接网络：[`docker network connect <网络名> <容器ID>`](https://docs.docker.com/engine/reference/commandline/network_connect/)。

  - 断开网络：[`docker network disconnect <网络名> <容器ID>`](https://docs.docker.com/engine/reference/commandline/network_disconnect/)。

  - 查看网络信息：[`docker network inspect <网络名>`](https://docs.docker.com/engine/reference/commandline/network_inspect/)。

  - 列出网络：[`docker network ls`](https://docs.docker.com/engine/reference/commandline/network_ls/)。

  - 移除网络：[`docker network rm <网络名>`](https://docs.docker.com/engine/reference/commandline/network_rm/)。

## 5. Containerd

[官方网站](https://containerd.io/) | [GitHub](https://github.com/containerd)

2013 年 Docker 的推出开启了应用程序开发的一场革命，使软件容器大众化。随着历史的发展，Docker 将其核心的容器技术拆分出来为单独的项目 containerd，并于 2017 年将该项目捐赠给了云原生计算基金会（CNCF）。containerd 发展至今已成为一个行业标准的容器运行时，它强调简单性、坚固性和便携性，是 CNCF 的第五个毕业项目。

当然，containerd 仍然是 Docker 引擎的核心容器运行时。Docker 在其基础上提供了 docker CLI、docker hub、docker compose、docker swarm 以及 docker stack 等高级功能。以下是 containerd 架构图：

<img src="./imgs/containerd架构图.png" width="800"  alt="containerd架构图"/>
