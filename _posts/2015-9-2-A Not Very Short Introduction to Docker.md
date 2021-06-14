---
title: 我的碎碎念：Docker入门指南
tags: [Docker]
description: 我的碎碎念：Docker入门指南
---

# 我的碎碎念：Docker入门指南

原文请参考[A Not Very Short Introduction to Docker ](http://anders.janmyr.com/2015/03/a-not-very-short-introduction-to-docker.html), 国内打不开的话请移步[A Not Very Short Introduction to Docker (backup)](https://rillhudev.coding.net/p/blogres/d/blogres/git/blob/master/A Not Very Short Introduction to Docker.md)

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-1.png)

之前曾经翻译过很多Docker入门介绍的文章，之所以再翻译这篇，是因为Anders的角度很独特，思路也很调理。你也可以看下作者的演讲稿《Docker， DevOps的未来》。本文介绍了Docker的一些基本概念、诱人的特性、Docker的工作原理、日常管理基本操作，以及一些Docker的问题的解决方案。

## 什么是Docker，你应该知道些什么？

相比很多人的解释，我相信说Docker是一个轻量级的虚拟机更容易理解。另外一种解释是：Docker就是操作系统中的chroot。如果你不知道chroot是什么的话，后一种解释可能无法帮助你理解什么是Docker。

chroot是一种操作，能改变当前运行的进程和子进程的根目录。 程序运行在这样的一个被修改的环境中，它不能访问这个环境目录树之外的文件和命令，这个被修改的环境就是“chroot牢笼”。

-- Arch Linux 的 wiki 中对 chroot 的解释

## 虚拟机 vs. Docker

下面这张图描述了虚拟机和Docker之间的差异。 在VM中，宿主OS上是hypervisor（虚拟机监视器）, 最上层是客户机操作系统，而Docker则使用Docker引擎和容器。 这样解释你能理解吗? Docker引擎和hypervisor之间的区别又是什么呢？你可以列出运行在宿主OS上的进程来理解它们的区别。

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-2.png)

下面这个简单的进程树可以看出它们的差异。虽然虚拟机中运行了很多进程，但是运行虚拟机的宿主机上却只有一个进程。

```
# Running processes on Host for a VM
$ pstree VM
-+= /VirtualBox.app
|--= coreos-vagrant
```

而运行Docker引擎的主机上则可以看到所有的进程。 容器进程是运行在宿主OS上的！，他们可以通过普通的ps，kill等命令进行检查和维护。

```
# Docker在主机中的进程
$ pstree docker
-+= /docker
|--= /bin/sh
|--= node server.js
|--= go run app
|--= ruby server.rb
...
|--= /bin/bash
```

所有的东西都是透明的， 意味着什么呢？意味着Docker容器比虚拟机更小，更快，更容易与其它东西集成。如下图所示。

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-3.png)

安装CoreOS的小型虚拟机居然有1.2GB， 而装上busybox的小型容器只有2.5MB。最快的虚拟机启动时间也是分钟级的，而容器的启动时间通常不到一秒。在同一宿主机上安装虚拟机需要正确的设置网络， 而安装Docker非常简单。

这么来看，容器是轻量、快速并且易集成，但这并不是它的全部！

## Docker 是一份合约

Docker还是开发者和运维之间的“合约”。 开发和运维在选择工具和环境时的姿态通常差别很大。开发者想要使用一些闪亮的新东西，比如Node.js、Rust、Go、微服务、Cassandra、Hadoop、blablabla.........而运维则倾向于使用以往用过的工具，因为事实证明那些旧的工具很有效。

但这恰恰是Docker的亮点， 运维喜欢它，因为Docker让他们只要关心一件事: 部署容器， 而开发者也一样很开心，只要写好代码，然后往容器里一扔，剩下的交给运维就完事了。

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-4.png)

不过别急，这还没完。运维还能帮助开发者构建优化好的容器以便用于本地开发。

更好的资源利用

很多年前，那时候还没有虚拟化，当我们需要创建一个新服务时，我们必须申请实际的物理机硬件。 这可能要花上数月，依赖于公司的流程。一旦服务器到位，我们创建好服务，很多时候它并没有像我们希望的那样成功，因为服务器的CPU使用率只有5%。 太奢侈了。

接着，虚拟化来了。它可以在几分钟之内把一台机器运转起来，还可以在同一硬件上运行多个虚拟机，资源使用率就不只5%了。但是，我们还需要给每个服务分配一个虚拟机，因此我们还是不能如愿的使用这台机器。

容器化是演化进程的下一步。容器可以在几秒之内创建起来，而且还能以比虚拟机更小的粒度进行部署。

## 依赖

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-5.png)

Docker启动速度真的很酷。 但是，我们为什么不把所有的都服务部署到同一台机器上呢？ 原因很简单：依赖的问题。在同一台机器上安装多个独立的服务，不管是真是机器还是虚拟机都是一场灾难。用Docker公司的说法是：地狱一样的矩阵依赖。

而Docker通过在容器中保留依赖关系解决了矩阵依赖的问题。

## 速度

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-6.png)

快当然不错，但是能快100倍就太不可思议了。速度让很多事情成为可能，增加了更多新的可能性。比如，现在可以快速创建新的环境，如果需要从Clojure开发环境完整的切换到Go语言吗？启动一个容器吧。需要为集成和性能测试提供生产环境DB ？启动一个容器吧！ 需要从Apache切换整个生产环境到Nginx？启动容器吧！

## Docker是怎么工作的？

Docker是一个Client-Server结构的系统，Docker守护进程运行在主机上， 然后通过Socket连接从客户端访问， 客户端和守护进程也可以运行再同一主机上，但这不是必须的。Docker命令行客户端也是类似的工作方式，但它通常通过Unix域套接字而不是TCP套接字连接。

守护进程从客户端接受命令并管理运行在主机上的容器。

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-7.png)

## Docker 概念及相互作用

主机， 运行容器的机器。

镜像，文件的层次结构，以及包含如何运行容器的元数据

容器，一个从镜像中启动，包含正在运行的程序的进程

Registry， 镜像仓库

卷，容器外的存储

Dockerfile， 用于创建镜像的脚本

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-8.png)

我们可以通过Dockerfile来构建镜像， 还可以通过commit一个运行的容器来创建一个镜像，这个镜像可以会被标记，可以推到Registry或者从Registry上拉下来，可以通过创建或者运行镜像的方式来启动容器，可以被stop，也可以通过rm来移除它。

## 镜像

镜像是一种文件结构，包含如何运行容器的元数据。Dockerfile中的每条命令都会在文件系统中创建一个新的层次结构，文件系统在这些层次上构建起来，镜像就构建于这些联合的文件系统之上。

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-9.png)

当容器启动后，所有镜像都会统一合并到一个进程中。 联合文件系统中的文件被删除时， 它们只是被标记为已删除，但实际上仍然存在。

```
# Commands for interacting with images
$ docker images  # 查看所有镜像.
$ docker import  # 从tarball创建镜像
$ docker build   # 通过Dockerfile创建镜像
$ docker commit  # 从容器中创建镜像
$ docker rmi     # 删除镜像
$ docker history # 列出镜像的变更历史
```

### 镜像大小

这是一些经常使用的镜像相关的数据：

scratch - 基础镜像， 0个文件，大小为0

busybox - 最小Unix系统，2.5MB，10000个文件

debian:jessie - Debian最新版， 122MB， 18000 个文件

ubuntu:14.04 - 188MB，23000 个文件

### 创建镜像

可以通过docker commit container-id、docker import url-to-tar或者docker build -f Dockerfile .来创建镜像。
先看commit的方式：

```
# 通过commit的方式来创建镜像
$ docker run -i -t debian:jessie bash
root@e6c7d21960:/# apt-get update
root@e6c7d21960:/# apt-get install postgresql
root@e6c7d21960:/# apt-get install node
root@e6c7d21960:/# node --version
root@e6c7d21960:/# curl https://iojs.org/dist/v1.2.0/iojs-v1.2.0-
linux-x64.tar.gz -o iojs.tgz
root@e6c7d21960:/# tar xzf iojs.tgz
root@e6c7d21960:/# ls
root@e6c7d21960:/# cd iojs-v1.2.0-linux-x64/
root@e6c7d21960:/# ls
root@e6c7d21960:/# cp -r * /usr/local/
root@e6c7d21960:/# iojs --version
1.2.0
root@e6c7d21960:/# exit
$ docker ps -l -q
e6c7d21960
$ docker commit e6c7d21960 postgres-iojs
daeb0b76283eac2e0c7f7504bdde2d49c721a1b03a50f750ea9982464cfccb1e
```

从上面可以看出，我们可以通过docker commit来创建镜像，但是这种方式有点凌乱而且很难复制， 更好的方式是通过Dockerfile来构建镜像，因为它步骤清晰并且容易复制：

```
FROM debian:jessie
# Dockerfile for postgres-iojs
RUN apt-get update
RUN apt-get install postgresql
RUN curl https://iojs.org/dist/iojs-v1.2.0.tgz -o iojs.tgz
RUN tar xzf iojs.tgz
RUN cp -r iojs-v1.2.0-linux-x64/* /usr/local
```

然后用下面的命令来构建：

```
$ docker build -tag postgres-iojs .
```

Dockerfile中的每一个命令都创建了新版的layer，通常把类似的命令放在一起，通过&&和续行符号把命令组合起来：

```
FROM debian:jessie
# Dockerfile for postgres-iojs
RUN apt-get update && \
apt-get install postgresql && \
curl https://iojs.org/dist/iojs-v1.2.0.tgz -o iojs.tgz && \
tar xzf iojs.tgz && \
cp -r iojs-v1.2.0-linux-x64/* /usr/local
```

这些行中命令的顺序很重要，因为Docker为了加速镜像的构建，会缓存中间的镜像。 组织Dockerfile的顺序时，注意把经常变化的行放在文件的底部，当缓存中相关的文件改变时，镜像会重新运行，即使Dockerfile中的行没有发生变化也是如此。

## Dockerfile 中的命令

Dockerfile 支持13个命令， 其中一些命令用于构建镜像，另外一些用于从镜像中运行容器，这是一个关于命令什么时候被用到的表格:

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-10.png)

### BUILD 命令：

FROM - 新镜像是基于哪个镜像的

MAINTAINER - 镜像维护者的姓名和邮箱地址

COPY - 拷贝文件和目录到镜像中

ADD - 同COPY一样，但会自动处理URL和解压tarball压缩包

RUN - 在容器中运行一个命令， 比如：apt-get install

ONBUILD - 当构建一个被继承的Dockerfile时运行命令

.dockerignore - 不是一个命令， 但它能控制什么文件被加入到构建的上下文中，构建镜像时应该包含.git以及其它的不需要的文件。

### RUN 命令：

CMD - 运行容器时的默认命令，可以被命令行参数覆盖

ENV - 设置容器内的环境变量

EXPOSE - 从容器中暴露出端口， 必须显式的通过在主机上的RUN命令带上-p或者-P来暴露端口

VOLUME - 指定一个在文件系统之后的存储目录。如果不是通过docker run -v设置的， 那么将被创建为/var/lib/docker/volumes

ENTRYPOINT - 指定一个命令不会被docker run image cmd命令覆盖。常用于提供一个默认的可执行程序并使用命令作为参数。

### BUILD, RUN命令都有的命令:

USER - 为RUN、CMD、ENTRYPOINT命令设置用户

WORKDIR - 为RUN、CMD、ENTRYPOINT、ADD、COPY命令设置工作目录

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-11.png)

## 运行的容器

容器启动后，进程在它可以运行的联合文件系统中获得了新的可写层。

从1.5版本起，它还可以让最顶层的layer设置为只读，强制我们为所有文件输出（如日志、临时文件）使用卷。

```
# 用于与容器交互的命令
$ docker create  # 创建一个容器，但不启动它
$ docker run     #  创建并启动一个容器
$ docker stop    # 停止容器
$ docker start   #  启动容器
$ docker restart # 重启容器
$ docker rm      # 删除容器
$ docker kill    #  给容器发送kill信号
$ docker attach  # 连接到正在运行的容器中
$ docker wait    # 阻塞直到容器停止为止
$ docker exec    # 在运行的容器中执行一条命令
```

### docker run

如上所述， docker run是用户启动新容器的命令， 这里是一些通用的运行容器的方法：

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-12.png)

```
# 交互式运行容器
$ docker run -it --rm ubuntu
```

这是一个可以让你像普通的终端程序一样交互式的运行容器的方法， 如果你想把管道输出到容器中，可以使用-t选项。

--interactive (-i) - 将标准输入发送给进程

-tty (-t) - 告诉进程有终端连接。 这个功能会影响程序的输出和它如何处理Ctrx-C等信号。

--rm - 退出时删除镜像。

```
# 后台运行容器
$ docker run -d hadoop
```

### docker run -env

```
# 运行一个命名容器并给它传一些环境变量
$ docker run \
--name mydb \
--env MYSQL_USER=db-user \
-e MYSQL_PASSWORD=secret \
--env-file ./mysql.env \
mysql
```

--name - 给容器命名， 否则它是一个随机容器

--env （-e）- 设置容器中的环境变量

--env-file - 从env-file中引入所有环境变量（同Linux下的source env-file 功能）

mysql - 指定镜像名为 mysql:lastest

### docker run -publish

```
# 发布容器的80端口到主机上的随机端口
$ docker run -p 80 nginx
# 发布容器端口80和主机上的8080端口
$ docker run -p 8080:80 nginx

# 发布容器80端口到主机127.0.0.0.1的8080端口
$ docker run -p 127.0.0.1:8080:80 nginx

# 发布所有容器中暴露的端口到主机的随机端口上
$ docker run -P nginx
```

nginx 镜像，比如暴露出80和443端口。

```
FROM debian:wheezy
  MAINTAINER NGINX "docker-maint@nginx.com"
EXPOSE 80 443
```

### docker run --link

```
# 启动postgres容器，给它起名为mydb
$ docker run --name mydb postgres
# 把mydb 链接到 myqpp 的db
$ docker run --link mydb:db myapp
```

连接容器需要设置容器到被连接的容器之间的网络，有两件事要做：

通过容器的连接名，更新 /etc/hosts 。 在上面的例子中，连接名是db， 可以方便的通过名字db来访问容器。

为暴露的端口设置环境变量。这个好像没啥实际用处，你也可以通过 主机名:端口的形式访问对应的端口。

### docker run limits

还可以通过run limits来限制容器可以使用的主机资源

```
# 限制内存大小
$ docker run -m 256m yourapp
# 限制进程可以使用的cpu份数(cpu shares)(总CPU份数为1024)
$ docker run --cpu-shares 512 mypp

# 改变运行进程的用户为www，而不是root（出于安全考虑）
$ docker run -u=www nginx
```

设置CPU份数为1024中的512份并不意味着可以使用一半的CPU资源，这意味着在一个无任何限制的容器中，它最多可以使用一半的份数。比如我们有两个有1024份的容器，和一个512份的容器(1024:1024:512) ，那么512份的那个容器，就只能得到1/5的总CPU份数

### docker exec container

docker exec 允许我们在已经运行的容器内部执行命令，这点在debug的时候很有用。

```
# 使用id 6f2c42c0在容器内部运行shell
$ docker exec -it 6f2c42c0 sh
```

## 卷

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-13.png)

卷提供容器外的持久存储。 这意味着如果你提交了新的镜像，数据将不会被保存。

```
# Start a new nginx container with /var/log as a volume
$ docker run  -v /var/log nginx
```

如果目录不存在，则会被自动创建为：/var/lib/docker/valumes/ec3c543bc..535

实际的目录名可以通过命令：docker inspect container-id 找到。

```
# 启动新的nginx容器，设置/var/log为卷，并映射到主机的/tmp目录下
$ docker run -v /tmp:/var/log nginx
```

还可以使用--valumes-from选项从别的容器中挂载卷。

```
# 启动容器db
$ docker run -v /var/lib/postgresql/data --name mydb postgres
# 启动backup容器，从mydb容器中挂载卷
$ docker run --volumes-from mydb backup
```

## Docker Registry

Docker Hub是Docker的官方镜像仓库，支持私有库和共有库，仓库可以被标记为官方仓库，意味着它由该项目的维护者（或跟它有关的人）策划。

Docker Hub 还支持自动化构建来自Github和Bitbucket的项目，如果启用自动构建功能，那么每次你提交代码到代码库都会自动构建镜像。

即使你不想用自动构建，你还是可以直接docker push到Docker Hub，Docker pull则会拉取镜像下来。docker run 一个本地不存在的镜像，则会自动开始docker pull操作。

你也可以在任意地方托管镜像，官方有Registry的开源项目，但是，还有很多Bug。

此外，Quay、Tutum和Google 还提供私有镜像托管服务。

## 检查容器

检查容器的命令有一大把:

```
$ docker ps      # 显示运行的容器
$ docker inspect # 显示容器信息（包括ip地址）
$ docker logs    # 获取容器中的日志
$ docker events  # 获取容器事件
$ docker port    # 显示容器的公开端口
$ docker top     # 显示容器中运行的进程
$ docker diff    # 查看容器文件系统中改变的文件
$ docker stats   # 查看各种纬度数据、内存、CPU、文件系统等
```

下面详细讲一下docker ps 和docker inspect，这两个命令最常用了。

```
# 列出所有容器，包括已停止的。
$ docker ps --all
CONTAINER ID   IMAGE            COMMAND    NAMES
9923ad197b65   busybox:latest   "sh"       romantic_fermat
fe7f682cf546   debian:jessie    "bash"     silly_bartik
09c707e2ec07   scratch:latest   "ls"       suspicious_perlman
b15c5c553202   mongo:2.6.7      "/entrypo  some-mongo
fbe1f24d7df8   busybox:latest   "true"     db_data

# Inspect the container named silly_bartik
# Output is shortened for brevity.
$ docker inspect silly_bartik
1 [{
2 "Args": [
3 "-c",
4 "/usr/local/bin/confd-watch.sh"
5 ],
6 "Config": {
10 "Hostname": "3c012df7bab9",
11 "Image": "andersjanmyr/nginx-confd:development",
12 },
13 "Id": "3c012df7bab977a194199f1",
14 "Image": "d3bd1f07cae1bd624e2e",
15 "NetworkSettings": {
16 "IPAddress": "",
18 "Ports": null
19 },
20 "Volumes": {},
22 }]
```

## 技巧花招

获取容器id。写脚本时很有用。

```
# Get the id (-q) of the last (-l) run container
# 获取最后(-l)一个启动的容器id(-q)
$ docker ps -l -q
c8044ab1a3d0
```

docker inspect可以带格式化的字符串----Go语言模板作为参数，详细描述所需的数据。写脚本时同时有用。

```
$ docker inspect -f '{{ .NetworkSettings.IPAddress }}' 6f2c42c05500
172.17.0.11
```

使用docker exec来跟运行中的容器进行交互。

```
# 获取容器环境变量
$ docker exec -it 6f2c42c05500 env
PATH=/usr/local/sbin:/usr...
HOSTNAME=6f2c42c05500
REDIS_1_PORT=tcp://172.17.0.9:6379
REDIS_1_PORT_6379_TCP=tcp://172.17.0.9:6379
...
```

通过卷来避免每次运行时都重建镜像， 下面是一个Dockerfile，每次构建时，会拷贝当前目录到容器中。

```
  1 FROM dockerfile/nodejs:latest
  2
  3 MAINTAINER Anders Janmyr "anders@janmyr.com"
  4 RUN apt-get update && \
  5   apt-get install zlib1g-dev && \
  6   npm install -g pm2 && \
  7   mkdir -p /srv/app
  8
  9 WORKDIR /srv/app
 10 COPY . /srv/app
 11
 12 CMD pm2 start app.js -x -i 1 && pm2 logs
 13
```

构建并运行镜像:

```
$ docker build -t myapp .
$ docker run -it --rm myapp
```

为避免重建，创建一次性镜像并在运行时挂载本地目录。

## 安全

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-14.jpg)

大家可能听说过使用Docker不那么安全。这不是假话，但这不成问题。

### 目前Docker存在以下安全问题：

镜像签名未被正确的核准。

如果你在容器中拥有root权限，那你潜在的拥有对真个主机的root权限。

### 安全解决办法:

从你的私有仓库中使用受信任的镜像

尽量不要以root运行容器

把容器中的root当作是主机上的root？ 还是把容器的根目录设置为容器内的根目录 ？

如果服务器上所有的容器都是你的，那你不需要担心他们之间会有危险的交互。

## “选择”容器

我给选择两字加了引号， 因为目前根本没有任何别的选择， 但是很多容器爱好者想玩玩，比如Ubuntu的LXD、微软的Drawbridge，还有Rocket。

Rocket由CoreOS开发，CoreOS是一个很大的容器平台。 他们开发Rocket的理由是觉得Docker公司让Docker变得臃肿，并且还和CoreOS有业务冲突。

他们在这个新的容器中，尝试移除那些因为历史原因而留下来的Docker瑕疵。并通过socket activation提供简单的容器和彻底的安全构建。

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-16.png)

## 编排

当我们把应用程序拆开到多个不同的容器中时，会产生一些新的问题。怎么让不同的部分进行通信呢？ 这些容器在单个主机上怎么办？ 多个主机上又是怎么处理？

单个主机上，Docker通过连接来解决编排的问题。

为简化容器的链接操作，Docker提供了一个叫docker-compose的工具。（以前它叫fig, 由另一家公司开发，然后最近Docker收购了他们）

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-16.png)

### docker-compose

在单个docker-compose.yml文件中声明多个容器的信息。来看一个例子，管理web和redis两个容器的配置文件：

```
  1   web:
  2   build: .
  3   command: python app.py
  4   ports:
  5    - "5000:5000"
  6   volumes:
  7    - .:/code
  8   links:
  9    - redis
 10 redis:
 11   image: redis
```

启动上述容器，可以使用docker-compose up命令

```
$ docker-compose up
  Pulling image orchardup/redis...
  Building web...
  Starting figtest_redis_1...
  Starting figtest_web_1...
  redis_1 | [8] 02 Jan 18:43:35.576 # Server
  started, Redis version 2.8.3
  web_1   |  * Running on http://0.0.0.0:5000/
```

也可以通过detached模式（detached mode）启动： docker-compose up -d，然后可以通过docker-compose ps查看容器中跑了啥东西:

```
$ docker-compose up -d
Starting figtest_redis_1...
Starting figtest_web_1...
$ docker-compose ps
Name              Command                    State   Ports
------------------------------------------------------------
figtest_redis_1   /usr/local/bin/run         Up
figtest_web_1     /bin/sh -c python app.py   Up      5000->5000
```

还可以同时让命令在一个容器或者多个容器中同时工作。

```
# 从web容器中获取环境变量
$ docker-compose run web env
# 扩展到多个容器中(Scale to multiple containers)
$ docker-compose scale web=3 redis=2

# 从所有容器中返回日志信息
$ docker-compose logs
```

从以上命令可以看出，扩展很容易，不过应用程序必须写成支持处理多个容器的方式。在容器外，不支持负载均衡。

## Docker托管

很多公司想做在云中托管Docker的生意，如下图。

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-17.png)

这些提供商尝试解决不同的问题， 从简单的托管到做"云操作系统"。其中有两家比较有前景：

### CoreOS

如上图所示，CoreOS是可以在CoreOS集群中托管多个容器的一系列服务的集合：

![01](https://rillhudev.coding.net/p/blogres/d/blogres/git/raw/master/20150902-18.png)

CoreOS Linux发行版是裁剪的Linux，在初次启动时使用114MB的RAM，没有包管理器， 使用Docker或者它自己的Rocket运行一切程序。

CoreOS 使用Docker（或Rocket）在主机上安装应用。

使用systemd作为init服务，它的性能超级好，还能很好的处理启动依赖关系， 强大的日志系统，还支持socket-activation。

etcd 是分布式的，一致性 K-V 存储用于配置共享和服务发现。

fleet，集群管理器，是systemd的扩展，能与多台机器工作，采用etcd来管理配置并运行在每一个台CoreOS服务器上。

### AWS

Docker容器托管在Amazon有两种途径：
Elastic Beanstalk部署Docker容器，它工作的很好，但就是太慢了， 一次全新的部署需要好几分钟，感觉跟一般的容器秒级启动不大对劲。
ECS、Elastic Container Server是Amazon上游容器集群解决方案， 目前还在预览版3，看起来很有前途，跟Amazon其它服务一样，通过简单的web service调用与它交互。

## 总结

- Docker is here to stay
- 解决了依赖问题
- 容器各方面都很快
- 有集群解决方案，但不能无缝对接