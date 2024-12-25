---
title: 
date: 2024-12-10T00:19:24+08:00
tags: []
series: []
featured: true
draft: true
---
Here is summary.

<!--more-->

1、DNS解析增加A记录 

@解析为xxx.com    www解析为www.xxx.com 。用@解析记录值为ping的网站ip即可

注意：文档说明让用四个，但腾讯云的域名负载均衡最多同一个域名只能增加两个！所以ping一下githubpages生成的域名，设成这个ip就可以。

2、增加CNAME记录  记录值为：xxx.github.io
