# Kubernetes<!-- omit in toc -->

[官方网站](https://kubernetes.io) | [中文文档](https://kubernetes.io/zh-cn/docs/home/) | [GitHub](https://github.com/kubernetes)

## 目录<!-- omit in toc -->

- [1. 概述](#1-概述)
  - [1.1. 特性](#11-特性)
  - [1.2. 结构和组件](#12-结构和组件)

## 1. 概述

Kubernetes，也称为 K8s，是一个开源的容器编排引擎，是云原生计算基金会（[CNCF](https://www.cncf.io/)） 的毕业项目。用来对容器化应用进行自动化部署、扩缩和管理。它将组成应用程序的容器组合成逻辑单元，以便于管理和服务发现。

Kubernetes 这个名字源于希腊语，意为 “舵手” 或 “飞行员”。k8s 这个缩写是因为 k 和 s 之间有八个字符的关系。

### 1.1. 特性

- 自动装箱：根据资源需求和其他限制自动放置容器，同时避免影响可用性。将关键性的和尽力而为性质的工作负载进行混合放置，以提高资源利用率并节省更多资源。

- 水平扩缩：使用一个简单的命令、一个 UI 或基于 CPU 使用情况自动对应用程序进行扩缩。

- 为扩展性设计：无需更改上游源码即可扩展你的 Kubernetes 集群。

- IPv4/IPv6 双协议栈：为 Pod 和 Service 分配 IPv4 和 IPv6 地址。

- 自动化上线和回滚（[Deployments](https://kubernetes.io/zh-cn/docs/concepts/workloads/controllers/deployment/)）：Kubernetes 会分步骤地将针对应用或其配置的更改上线，同时监视应用程序运行状况以确保你不会同时终止所有实例。如果出现问题，Kubernetes 会为你回滚所作更改。

- 服务发现与负载均衡（[Service](https://kubernetes.io/zh-cn/docs/concepts/services-networking/service/)）：使用 Kubernetes，你无需修改应用程序即可使用不熟悉的服务发现机制。Kubernetes 为 Pod 提供自己的 IP 地址，并为一组 Pod 提供相同的 DNS 名，并且可以在它们之间进行负载均衡。

- 自我修复（[ReplicaSet](https://kubernetes.io/zh-cn/docs/concepts/workloads/controllers/replicaset/#replicationcontroller-%e5%a6%82%e4%bd%95%e5%b7%a5%e4%bd%9c)）：重新启动失败的容器；在节点死亡时替换并重新调度容器；杀死不响应用户定义的健康检查的容器；并且在它们准备好服务之前不会将它们公布给客户端。

- 存储编排（[Persistent Volume](https://kubernetes.io/zh-cn/docs/concepts/storage/persistent-volumes/)）：自动挂载所选存储系统，包括本地存储、诸如 AWS 或 GCP 之类公有云提供商所提供的存储或者诸如 NFS、iSCSI、Ceph、Cinder 这类网络存储系统。

- Secret 和配置管理（[Secret](https://kubernetes.io/zh-cn/docs/concepts/configuration/secret/)）：部署和更新 Secret 和应用程序的配置而不必重新构建容器镜像，且不必将软件堆栈配置中的秘密信息暴露出来。

- 批量执行（[Job](https://kubernetes.io/zh-cn/docs/concepts/workloads/controllers/job/)）：除了服务之外，Kubernetes 还可以管理你的批处理和 CI 工作负载，在期望时替换掉失效的容器。

### 1.2. 结构和组件

如下图所示，左侧是主节点，其中的各类组件对集群进行全局的控制，k8s 称之为 “控制平面”。右侧是工作节点，可以是物理机器或者虚拟机，它会运行容器化的应用程序。开发人员通过命令行工具 kubectl 来操作控制平面从而管理集群，而终端用户则通过开放的互联网入口来访问用应用程序。

<img src="./imgs/k8s结构和组件.svg" width="800" alt="k8s结构和组件"/>

以下分别介绍其中的每个组件：

- 控制平面组件

  - kube-apiserver

  - etcd

  - kube-scheduler

  - kube-controller-manager

- 工作节点组件

  - kubelet

  - kube-proxy

  - 容器运行时

  - Pod
