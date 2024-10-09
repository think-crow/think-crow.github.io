---
title: git命令教程
date: 2024-10-09T21:00:43+08:00
tags: ["git"]
series: ["hugo建站"]
featured: true
---
网站文档更新到网站的必要学习步骤，参考 标题1 即可！.

<!--more-->

#     git上传操作步骤图解：

![git总结](/images/blog/git总结.png)



# 1、git顺序上传步骤：

1、git init: 在当前目录初始化一个新的 Git 仓库。

2、git add <file>: 将文件添加到暂存区。

3、git commit -m "Commit message": 将暂存区的文件提交到本地仓库。

4、git remote add <仓库名> <远程仓库地址>: 添加一个新的远程仓库。

5、git push -u <仓库名> <分支名>: 将本地提交推送到远程仓库。

**备注：上述5个步骤只是首次执行的命令，后续只执行2、3、5即可！**



# 2、git常用查看命令：

1、git status     查看暂存区与缓存区的状态。

2、git remote -v   显示远程仓库地址的详细信息。

3、git branch <分支名>     列出本地分支。

4、git branch -m <分支名>     重命名当前分支。

5、git checkout <分支名>     切换到指定分支。

6、git checkout -b <分支名>     创建并切换到指定分支。



# 3、注意事项

1、命令不要敲错和漏敲了，一个字母敲错就error，很难发现的！

2、报错看error，根据error找问题（百度和gpt很香的）。

3、git push会经常碰到网络问题，可以设置ssh密钥（简略步骤）！

-    ssh-keygen -t rsa -b 4096 -C "邮箱地址xxx@xxx.com"  (密钥保存在 ~家目录/.ssh的文件夹)
-    id_rsa.pub里面的内容复制到GitHub的settings的SSH and GPG keys里面即可

4、参考文档是个好东西，要看细致了，漏看东西很致命！



**一分耕耘，一分收获，       加油！**     



​																																
