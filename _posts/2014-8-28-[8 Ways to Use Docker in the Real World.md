---
title: 八个Docker的真实应用场景
tags: [Docker]
description: 八个Docker的真实应用场景
---



# 八个Docker的真实应用场景

原文请参考[8 Ways to Use Docker in the Real World – Flux7 Blog](https://www.flux7.com/blog/8-ways-to-use-docker-in-the-real-world-flux7-blog/), 译文去除了不太相关的内容。

![](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20140828-1.png)

在我们讨论Docker的使用场景之前，先来看看Docker这个工具有什么特别的地方吧。

在我们讨论Docker的使用场景之前，先来看看Docker这个工具有什么特别的地方吧。
Docker提供了轻量级的虚拟化，它几乎没有任何额外开销，这个特性非常酷。
首先你在享有Docker带来的虚拟化能力的时候无需担心它带来的额外开销。其次，相比于虚拟机，你可以在同一台机器上创建更多数量的容器。
Docker的另外一个优点是容器的启动与停止都能在几秒中内完成。Docker公司的创始人 Solomon Hykes曾经介绍过Docker在单纯的LXC之上做了哪些[事情](http://stackoverflow.com/questions/17989306/what-does-docker-add-to-just-plain-lxc)，你可以去看看。
下面是我总结的一些Docker的使用场景，它为你展示了如何借助Docker的优势，在低开销的情况下，打造一个一致性的环境。

### 1. 简化配置

这是Docker公司宣传的Docker的主要使用场景。虚拟机的最大好处是能在你的硬件设施上运行各种配置不一样的平台（软件、系统），Docker在降低额外开销的情况下提供了同样的功能。它能让你将运行环境和配置放在代码中然后部署，同一个Docker的配置可以在不同的环境中使用，这样就降低了硬件要求和应用环境之间耦合度。

### 2. 代码流水线（Code Pipeline）管理

前一个场景对于管理代码的流水线起到了很大的帮助。代码从开发者的机器到最终在生产环境上的部署，需要经过很多的中间环境。而每一个中间环境都有自己微小的差别，Docker给应用提供了一个从开发到上线均一致的环境，让代码的流水线变得简单不少。

### 3. 提高开发效率

这就带来了一些额外的好处：Docker能提升开发者的开发效率。如果你想看一个详细一点的例子，可以参考Aater在[DevOpsDays Austin 2014 ](http://www.slideshare.net/Flux7Labs/using-docker-to-improve-web-developer-productivity-dev-opsdays-austin-may-5) 大会或者是DockerCon上的演讲。
不同的开发环境中，我们都想把两件事做好。一是我们想让开发环境尽量贴近生产环境，二是我们想快速搭建开发环境。
理想状态中，要达到第一个目标，我们需要将每一个服务都跑在独立的虚拟机中以便监控生产环境中服务的运行状态。然而，我们却不想每次都需要网络连接，每次重新编译的时候远程连接上去特别麻烦。这就是Docker做的特别好的地方，开发环境的机器通常内存比较小，之前使用虚拟的时候，我们经常需要为开发环境的机器加内存，而现在Docker可以轻易的让几十个服务在Docker中跑起来。

### 4. 隔离应用

有很多种原因会让你选择在一个机器上运行不同的应用，比如之前提到的提高开发效率的场景等。
我们经常需要考虑两点，一是因为要降低成本而进行服务器整合，二是将一个整体式的应用拆分成松耦合的单个服务（译者注：微服务架构）。如果你想了解为什么松耦合的应用这么重要，请参考Steve Yege的[这篇论文](https://plus.google.com/+RipRowan/posts/eVeouesvaVX)，文中将Google和亚马逊做了比较。

### 5. 整合服务器

正如通过虚拟机来整合多个应用，Docker隔离应用的能力使得Docker可以整合多个服务器以降低成本。由于没有多个操作系统的内存占用，以及能在多个实例之间共享没有使用的内存，Docker可以比虚拟机提供更好的服务器整合解决方案。

### 6. 调试能力

Docker提供了很多的工具，这些工具不一定只是针对容器，但是却适用于容器。它们提供了很多的功能，包括可以为容器设置检查点、设置版本和查看两个容器之间的差别，这些特性可以帮助调试Bug。你可以在[《Docker拯救世界》](http://flux7.com/blogs/docker/docker-saves-the-day-at-flux7/)

### 7. 多租户环境

另外一个Docker有意思的使用场景是在多租户的应用中，它可以避免关键应用的重写。我们一个特别的关于这个场景的例子是为IoT（译者注：物联网）的应用开发一个快速、易用的多租户环境。这种多租户的基本代码非常复杂，很难处理，重新规划这样一个应用不但消耗时间，也浪费金钱。
使用Docker，可以为每一个租户的应用层的多个实例创建隔离的环境，这不仅简单而且成本低廉，当然这一切得益于Docker环境的启动速度和其高效的`diff`命令。
你可以在[这里](http://flux7.com/blogs/docker/using-docker-for-quick-and-easy-multi-tenancy/)了解关于此场景的更多信息。

### 8. 快速部署

在虚拟机之前，引入新的硬件资源需要消耗几天的时间。虚拟化技术（Virtualization）将这个时间缩短到了分钟级别。而Docker通过为进程仅仅创建一个容器而无需启动一个操作系统，再次将这个过程缩短到了秒级。这正是Google和Facebook都看重的特性。