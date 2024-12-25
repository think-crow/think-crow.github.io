---
title: kail安装报错 解决办法
date: 2024-11-01T15:01:24+08:00
tags: []
series: []
featured: false
---


安装步骤网上现成的很多,这里只记录下碰到的问题！

<!--more-->

### 问题一：安装进程卡着不动

![这是图片](/images/blog/kail5.png "图片标题")

原因：网络问题

方法：关闭防火墙，外置usb网卡接入kail虚拟机再安装即可。

### 问题二：开机黑屏，只有一个_

![这是图片](/images/blog/kail4.png "图片标题")

原因：核对一下安装过程碰到的GRUB启动引导器选项选择那里！(如下图就懒得截图，找了两张一样的！原地址：[kail安装教程](https://blog.csdn.net/fingue/article/details/127559353)【图片竟然还有防盗措施，那就截屏吧】)

![这是图片](/images/blog/kail2.png "图片标题")

![这是图片](/images/blog/kail3.png "图片标题")

方法：确定上述两项没问题后，系统安装完成重启时，虚拟机可能会弹出一个选项，选择连接到虚拟机一下（感觉应该是这个原因，第一次我点的拒绝！）

***

#### 安装完成后的效果：

![这是图片](/images/blog/kail1.png "图片标题")

![这是图片](/images/blog/kail.png "图片标题")
