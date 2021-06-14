---
layout: post
title: Artemis后台管理系统操作简介
date: 2020-3-4
categories: blog
tags: [Artemis]
description: Artemis后台管理系统操作简介
---

# Artemis后台管理系统操作简介

## 1.登录

后台管理系统的登录网址为：http://www.artemis.org.cn:8000/xadmin/

![login](https://coding-net-production-file-ci.codehub.cn/c1e39d10-6993-11ea-a64e-d95e0eba03ce.png?sign=oFoUF7nbszQMe7ioAD6Nt07uw9RhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4MTIxJnQ9MTU4NDYwMjEyMSZyPTc3MzMwMTMyJmY9L2MxZTM5ZDEwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

输入用户名和密码，点击“登录”按钮或按回车键，即可进入后面管理主页面

![home-page](https://coding-net-production-file-ci.codehub.cn/c1daea80-6993-11ea-a64e-d95e0eba03ce.png?sign=qlWhNEwmM7xi/a0mJ6LAVfAIQ0lhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4NjI1JnQ9MTU4NDYwMjYyNSZyPTU2ODc3MjExJmY9L2MxZGFlYTgwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

目前除超级管理员外，其余账号仅拥有课程管理的权限，若点击除课程管理以外的导航按钮，页面会出现错误信息。若不小心误点，点击浏览器的后退按钮回到当前页面即可。

## 2.管理课程信息

### 1）新增课程

点击页面左侧导航栏中的“课程信息”按钮，会显示出课程信息的展示页面，如下图所示：

![add-course1](https://coding-net-production-file-ci.codehub.cn/bf825480-6993-11ea-a64e-d95e0eba03ce.png?sign=xpa86FiNZktL0FTR0hVnFFsrPCBhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4Njc1JnQ9MTU4NDYwMjY3NSZyPTkwMTI1OTUzJmY9L2JmODI1NDgwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击页面右侧表格上方的“增加课程”按钮，如下图所示：

![add-course2](https://coding-net-production-file-ci.codehub.cn/bf88bd20-6993-11ea-a64e-d95e0eba03ce.png?sign=FNE9cdimBcrJhg75Alh7M1Z+vR1hPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4NzAyJnQ9MTU4NDYwMjcwMiZyPTc1MTUzNDkwJmY9L2JmODhiZDIwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

在增加课程页面，如下图所示，输入课程名、课程描述、课程详情等信息，为课程选择一张封面图片并上传，所有红色星号标记的参数为必填选项，输入完成后点击页面右下角的“保存”按钮，即可完成新增一门课程。如果还需要新增其他课程也可以点击“保存并增加另一个”按钮继续新增下一门课程。

![add-course3](https://coding-net-production-file-ci.codehub.cn/c00c4500-6993-11ea-a64e-d95e0eba03ce.png?sign=Z81uovdl5Mq68i0pYi7+pXQ4YuhhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4NzI4JnQ9MTU4NDYwMjcyOCZyPTg1MDc2MDI4JmY9L2MwMGM0NTAwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

### 2）编辑课程

点击左侧导航栏中的“课程信息”按钮或者页面上方的路径导航按钮（如红色框中所示）均可跳转到课程信息展示页面，如下图所示：

![edit-course1](https://coding-net-production-file-ci.codehub.cn/c16cbf60-6993-11ea-a64e-d95e0eba03ce.png?sign=eo8vse7UZsAO5cV093YaYyu6oY5hPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4ODI3JnQ9MTU4NDYwMjgyNyZyPTI1NzAxMjIxJmY9L2MxNmNiZjYwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击需要编辑的课程名，即可进入到课程编辑页面，如下图所示。编辑完成后，点击下方“保存”按钮完成编辑。

![edit-course2](https://coding-net-production-file-ci.codehub.cn/c17068e0-6993-11ea-a64e-d95e0eba03ce.png?sign=2qYS+Xr5k2PS+DIOr5pQkL1TK45hPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4ODQ4JnQ9MTU4NDYwMjg0OCZyPTcxMjg4NDc3JmY9L2MxNzA2OGUwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

### 3）删除课程

删除课程有两种方法：

一、在课程信息的展示页面，勾选要删除的课程，点击右下角“选择了n个中的m个”绿色按钮，点击弹出的按钮“删除所选的课程”，如下图所示：

![delete-course1](https://coding-net-production-file-ci.codehub.cn/c084a950-6993-11ea-a64e-d95e0eba03ce.png?sign=F2+uYI+Su7g/j7NcGAhj5Zru0UxhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4ODcwJnQ9MTU4NDYwMjg3MCZyPTMxNTY2NDkxJmY9L2MwODRhOTUwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

二、进入编辑课程信息页面，点击右下角“删除”按钮即可删除该课程，如下图所示：

![delete-course2](https://coding-net-production-file-ci.codehub.cn/c0ec1db0-6993-11ea-a64e-d95e0eba03ce.png?sign=jI/8QHLumaAZ+EbJ8g3JIGRKIQNhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4ODkyJnQ9MTU4NDYwMjg5MiZyPTcwNTY0MzA2JmY9L2MwZWMxZGIwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

## 3.章节信息

### 1）新增章节

点击页面左侧导航栏中的“章节信息”按钮，会显示出所有课程的全部章节信息，如下图所示：

![add-chapter1](https://coding-net-production-file-ci.codehub.cn/bf7200d0-6993-11ea-a64e-d95e0eba03ce.png?sign=fLEAFqP5Dyj9yxRMfJm1FF/6A9VhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4OTE3JnQ9MTU4NDYwMjkxNyZyPTI4MDI3ODE0JmY9L2JmNzIwMGQwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击页面右侧表格上方的“增加章节”按钮，如下图所示：

![add-chapter2](https://coding-net-production-file-ci.codehub.cn/bf78b790-6993-11ea-a64e-d95e0eba03ce.png?sign=5jWajvRR4btwLevKqBt8TdeqSyNhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4OTQzJnQ9MTU4NDYwMjk0MyZyPTczMzg5MzkmZj0vYmY3OGI3OTAtNjk5My0xMWVhLWE2NGUtZDk1ZTBlYmEwM2NlLnBuZyZiPWNvZGluZy1uZXQtcHJvZHVjdGlvbi1maWxl)

在增加章节页面，如下图所示，选择此次增加的章节所属课程，若课程不存在也可以点击后面的加号按钮先增加课程，再输入章节名，完成后点击页面右下角的“保存”按钮，即可完成新增一章节。如果还需要新增其他章节也可以点击“保存并增加另一个”按钮继续新增下一章节。

![add-chapter3](https://coding-net-production-file-ci.codehub.cn/bf7d4b70-6993-11ea-a64e-d95e0eba03ce.png?sign=3HVVL8/dABXV/PgonhggcSLUZIVhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4OTY0JnQ9MTU4NDYwMjk2NCZyPTE4MjE1MzMmZj0vYmY3ZDRiNzAtNjk5My0xMWVhLWE2NGUtZDk1ZTBlYmEwM2NlLnBuZyZiPWNvZGluZy1uZXQtcHJvZHVjdGlvbi1maWxl)

### 2）编辑章节

点击左侧导航栏中的“章节信息”按钮或者页面上方的路径导航按钮（如红色框中所示）均可跳转到章节信息展示页面，如下图所示：

![edit-chapter1](https://coding-net-production-file-ci.codehub.cn/c16433e0-6993-11ea-a64e-d95e0eba03ce.png?sign=U0sWVAfUEGgJmdCyNLV8GAzLjIthPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE4OTkxJnQ9MTU4NDYwMjk5MSZyPTQ0NzkxMDE5JmY9L2MxNjQzM2UwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击需要编辑的章节对应的课程，即可进入到章节编辑页面，如下图所示。编辑完成后，点击下方“保存”按钮完成编辑。

![edit-chapter2](https://coding-net-production-file-ci.codehub.cn/c16656c0-6993-11ea-a64e-d95e0eba03ce.png?sign=nE7alTEMFgmER0zbXX/BpT6CfaNhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MDA5JnQ9MTU4NDYwMzAwOSZyPTYyMDM3NDE5JmY9L2MxNjY1NmMwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

### 3）删除章节

删除章节有两种方法：

一、在章节信息的展示页面，勾选要删除的章节，点击右下角“选择了n个中的m个”绿色按钮，点击弹出的按钮“删除所选的章节”，如下图所示：

![delete-chapter1](https://coding-net-production-file-ci.codehub.cn/c0898b50-6993-11ea-a64e-d95e0eba03ce.png?sign=A7nRjBmIgxf0jG4mnJeuUelaLKphPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MDUyJnQ9MTU4NDYwMzA1MiZyPTk5OTg0NTgwJmY9L2MwODk4YjUwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

二、进入编辑章节信息页面，点击右下角“删除”按钮即可删除章节，如下图所示：

![delete-chapter2](https://coding-net-production-file-ci.codehub.cn/c0854590-6993-11ea-a64e-d95e0eba03ce.png?sign=aHj6biSR8beBArJilgebT0Q7u4thPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MDc3JnQ9MTU4NDYwMzA3NyZyPTI5MDgzNjQ5JmY9L2MwODU0NTkwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

## 4.视频信息

### 1）新增视频

点击页面左侧导航栏中的“视频信息”按钮，会显示出系统中所有的视频信息，如下图所示：

![add-video1](https://coding-net-production-file-ci.codehub.cn/c00fc770-6993-11ea-a64e-d95e0eba03ce.png?sign=96zxYxBg+Lp3YPOwsTa7vQuxTGVhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MTAzJnQ9MTU4NDYwMzEwMyZyPTYzMzA3MzI4JmY9L2MwMGZjNzcwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击页面右侧表格上方的“增加视频”按钮，如下图所示：

![add-video2](https://coding-net-production-file-ci.codehub.cn/c0819c10-6993-11ea-a64e-d95e0eba03ce.png?sign=Zehmj/cWjsyGQS28cMNzhaiwlAVhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MTI1JnQ9MTU4NDYwMzEyNSZyPTE0MTg2MDQ2JmY9L2MwODE5YzEwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

在增加视频页面，如下图所示，选择增加的视频所属章节，如果该视频所属章节不存在，也可以点击章节后面的加号按钮先增加章节，**在访问地址中需要填入该视频所存储的网络地址（系统暂不支持本地直接上传视频）**，再输入视频名和学习时长，完成后点击页面右下角的“保存”按钮，即可完成新增一个视频。如果还需要新增其他视频也可以点击“保存并增加另一个”按钮继续新增下一个视频。

![add-video3](https://coding-net-production-file-ci.codehub.cn/c0871a50-6993-11ea-a64e-d95e0eba03ce.png?sign=Zai+sbgpU5x3QyXfhWtLfWX3fdxhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MTc4JnQ9MTU4NDYwMzE3OCZyPTQ3MDA3NjM2JmY9L2MwODcxYTUwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

### 2）编辑视频

点击左侧导航栏中的“视频信息”按钮或者页面上方的路径导航按钮（如红色框中所示）均可跳转到视频信息展示页面，如下图所示：

![edit-video1](https://coding-net-production-file-ci.codehub.cn/c1d60880-6993-11ea-a64e-d95e0eba03ce.png?sign=s7bpfQGQcuihe8lSDt8avFe2AgBhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MjE4JnQ9MTU4NDYwMzIxOCZyPTEyMjQ5MzA4JmY9L2MxZDYwODgwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击需要编辑的视频对应的章节，即可进入到视频编辑页面，如下图所示。编辑完成后，点击右下角“保存”按钮完成编辑。

![edit-video2](https://coding-net-production-file-ci.codehub.cn/c1db5fb0-6993-11ea-a64e-d95e0eba03ce.png?sign=K9W++0VeQ0ehKqaLqReNF2F7q0ZhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MjM0JnQ9MTU4NDYwMzIzNCZyPTM0OTg3NTg1JmY9L2MxZGI1ZmIwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

### 3）删除视频

删除视频有两种方法：

一、在视频信息的展示页面，勾选要删除的视频，点击右下角“选择了n个中的m个”绿色按钮，点击弹出的按钮“删除所选的视频”，如下图所示：

![delete-video1](https://coding-net-production-file-ci.codehub.cn/c0f6f320-6993-11ea-a64e-d95e0eba03ce.png?sign=QXDzvK3KiSdVIPzFfCCfDpmTyQJhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MjYxJnQ9MTU4NDYwMzI2MSZyPTcxMzExNjQyJmY9L2MwZjZmMzIwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

二、进入编辑视频信息页面，点击右下角“删除”按钮即可删除该视频，如下图所示：

![delete-video2](https://coding-net-production-file-ci.codehub.cn/c0f9b240-6993-11ea-a64e-d95e0eba03ce.png?sign=27Xt9f8Mvyj6hDRGBgIxFuvlVGlhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5Mjg0JnQ9MTU4NDYwMzI4NCZyPTg1MDEzNDkwJmY9L2MwZjliMjQwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

## 5.课程参考资料

### 1）新增参考资料

点击页面左侧导航栏中的“课程资源”按钮，会显示出所有课程的参考资料信息，如下图所示：

![add-ref1](https://coding-net-production-file-ci.codehub.cn/c0121160-6993-11ea-a64e-d95e0eba03ce.png?sign=BCFoiuvtFLI0pHU8q3/0Jitaf/phPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MzE5JnQ9MTU4NDYwMzMxOSZyPTkwNDM0Njg2JmY9L2MwMTIxMTYwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击页面右侧表格上方的“增加课程资源”按钮，如下图所示：

![add-ref2](https://coding-net-production-file-ci.codehub.cn/c01cbfc0-6993-11ea-a64e-d95e0eba03ce.png?sign=K38gu09oyf/xpCIm/WnxB1vnSfFhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MzU4JnQ9MTU4NDYwMzM1OCZyPTM5NDU5MzkmZj0vYzAxY2JmYzAtNjk5My0xMWVhLWE2NGUtZDk1ZTBlYmEwM2NlLnBuZyZiPWNvZGluZy1uZXQtcHJvZHVjdGlvbi1maWxl)

在增加课程资源页面，如下图所示，选择此次增加的参考资料所属的课程，如果课程不存在可以点击右边的加号按钮先增加课程，再输入资料名称，从本地选择文件并上传，即可完成新增参考资料。如果还需要新增其他资源也可以点击“保存并增加另一个”按钮继续新增下资源。

**注意：此处上传的资源文件类型不限，但因服务器存储空间有限，请勿上传视频等占用空间较大的文件。**

![add-ref3](https://coding-net-production-file-ci.codehub.cn/c00b81b0-6993-11ea-a64e-d95e0eba03ce.png?sign=9Hk7g9G5e3vErTcPil8SLu/qQv5hPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5MzgyJnQ9MTU4NDYwMzM4MiZyPTc2NTk5NzcyJmY9L2MwMGI4MWIwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

### 2）编辑参考资料

点击左侧导航栏中的“课程资源”按钮或者页面上方的路径导航按钮（如红色框中所示）均可跳转到课程资源信息展示页面，如下图所示：

![edit-ref1](https://coding-net-production-file-ci.codehub.cn/c168eed0-6993-11ea-a64e-d95e0eba03ce.png?sign=dcJF/DdjQT6cpcYc2cWjPkCmApFhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5NDAzJnQ9MTU4NDYwMzQwMyZyPTY3MTIxODgwJmY9L2MxNjhlZWQwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

点击需要编辑的资源对应的课程，即可进入到课程资源编辑页面，如下图所示。编辑完成后，点击右下角“保存”按钮完成编辑。

![edit-ref2](https://coding-net-production-file-ci.codehub.cn/c1d5e170-6993-11ea-a64e-d95e0eba03ce.png?sign=PApHDoOWrp3cXpog5S+ax+G3I/thPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5NDI1JnQ9MTU4NDYwMzQyNSZyPTIyOTM2NDI4JmY9L2MxZDVlMTcwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

### 3）删除信息资源

删除信息资源有两种方法：

一、在信息资源的展示页面，勾选要删除的资源，点击右下角“选择了n个中的m个”绿色按钮，点击弹出的按钮“删除所选的章节”，如下图所示：

![delete-ref1](https://coding-net-production-file-ci.codehub.cn/c0f3e5e0-6993-11ea-a64e-d95e0eba03ce.png?sign=Ktj09knmI6TO+BatbY53tgbuGt9hPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5NDQ3JnQ9MTU4NDYwMzQ0NyZyPTMwMDMyODI3JmY9L2MwZjNlNWUwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

二、进入编辑信息资源信息页面，点击右下角“删除”按钮即可删除资源，如下图所示：

![delete-ref2](https://coding-net-production-file-ci.codehub.cn/c0f03c60-6993-11ea-a64e-d95e0eba03ce.png?sign=Jz24O5YuwWV75TqdfcECRr+kcQNhPTEyNTcyNDI1OTkmaz1BS0lEYXk4M2xGbWFTNlk0TFRkek1WTzFTZFpPeUpTTk9ZcHImZT0xNTg0ODE5NDc0JnQ9MTU4NDYwMzQ3NCZyPTE2NzI2NjYxJmY9L2MwZjAzYzYwLTY5OTMtMTFlYS1hNjRlLWQ5NWUwZWJhMDNjZS5wbmcmYj1jb2RpbmctbmV0LXByb2R1Y3Rpb24tZmlsZQ==)

