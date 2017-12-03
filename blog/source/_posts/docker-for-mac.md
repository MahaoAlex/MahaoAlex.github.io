---
title: macOS安装docker
date: 2017-12-02 21:41:44
tags: coding
---

# MacOS安装docker

## 版本差异

| Macos版本                         | 安装方式           |
| ------------------------------- | -------------- |
| Macos Yosemite 10.10.3 or above | Docker for Mac |
| Previos                         | Docker Toolbox |

> 为什么会有版本差异？
> 官方解释：[Docker for Mac vs. Docker Toolbox](https://docs.docker.com/docker-for-mac/docker-toolbox/)
> Docker ToolBox 实际上是使用VirtualBox在Mac中创建一个VM（default)，并通过docker-machine管理这个VM。这个VM运行的是boot2docker的Linux发行版。运行`docker`和`docker-compose`命令前需要通过执行`eval $(docker-machine env default)`命令指定对应的docker machine
>
> Docker for Mac 使用的是基于`Hypervisor.framework`开发的轻量级的虚拟化工具包`Hyperkit`。`Hypervisor.framework`是在macos 10.10.3之后才有的东西。

本次安装基于版本`macOS High Sierra 10.13.1`

## 安装步骤

- 软件获取[路径](https://store.docker.com/editions/community/docker-ce-desktop-mac),  大小:127M
- 安装步骤傻瓜式

{%asset_img docker-for-mac.png 傻瓜式安装 %}

{%asset_img docker-need-privileged.png 安装过程中需要输密码赋权限 %}

- 安装完成后，系统中增加了如下表所示的二进制文件

| 二进制名称                         | 二进制大致作用                                  |
| ----------------------------- | ---------------------------------------- |
| docker                        | A self-sufficient runtime for containers。The base command for Docker CLI |
| docker-compose                | 多容器管理，主要解决容器部署的问题                        |
| docker-machine                | Machine lets you create Docker hosts on your computer, on cloud providers, and inside your own data center. It creates servers, installs Docker on them, then configures the Docker client to talk to them |
| docker-credential-osxkeychain | [docker credential helpers](https://github.com/docker/docker-credential-helpers/releases) |

{%asset_img docker-command.png docker相关的二进制 %}

> 安装完来个hello-world是程序员的标准套路，`docker run hello-world `如果报错TLS handshake timeout，可以考虑Once more 或者来个梯子

## 配置

### 基础配置

* Docker for mac 提供了图形化的界面进行基础配置。

  可参考[Preference](https://docs.docker.com/docker-for-mac/#preferences)进行配置，主要的配置包括

  - Docker for mac 对应的VM的实时备份（默认不开启）
  - 共享文件，只有此处进行配置的目录才能够挂载到容器中
  - Docker for Mac 占用的CPU和内存占用，以及虚拟机子网网段
  - 代理配置，默认系统代理
  - 私有仓库配置
  - Docker Enginee配置文件自定义

### 其他配置

- 自动补全
  - bash 参考[install bash completion](https://docs.docker.com/docker-for-mac/#install-bash-completion)
  - zsh 参考[zsh下docker命令tab补全方法](https://www.cnblogs.com/zlzlnet/p/6109907.html)



## 参考文档

- [Docker for Mac 初体验](https://segmentfault.com/a/1190000005106237)
- [MacOS上安装Docker](https://segmentfault.com/a/1190000004556081)
- [使用docker compose 部署服务](http://blog.csdn.net/yl_1314/article/details/53761049)
- [zsh下docker命令tab补全方法](https://www.cnblogs.com/zlzlnet/p/6109907.html)