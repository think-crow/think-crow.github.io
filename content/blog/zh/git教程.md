---
title: git基础及怎么PR
date: 2024-10-09T21:00:43+08:00
tags: ["hugo"]
series: ["hugo建站"]
featured: true
---
网站文档更新到网站的必要学习步骤，参考 标题1 即可！.

<!--more-->

##     git上传操作步骤图解：

![git总结](/images/blog/git总结.png)

备注：git是一个开源的分布式版本管理系统，可以随时切换你提交的版本。

上述工作区，暂存区，本地仓库，远程仓库是git提交的一整个过程！

工作区也就是你的代码文件夹，暂存区就是你将要提交的内容，本地仓库就是已经提交了内容但没有上传远端，最后就是上传远端（上传远端之后，若有不妥可版本回退！即回退到之前任意一次提交的的内容）。

## 1、git顺序上传步骤：

1、git init: 在当前目录初始化一个新的 Git 仓库。

2、git add <file>: 将文件添加到暂存区。

3、git commit -m "Commit message": 将暂存区的文件提交到本地仓库。

4、git remote add <仓库名> <远程仓库地址>: 添加一个新的远程仓库。

5、git push -u <仓库名> <分支名>: 将本地提交推送到远程仓库。

**备注：上述5个步骤只是首次执行的命令，后续只执行2、3、5即可！**



## 2、git常用查看命令：

1、git status     查看暂存区与缓存区的状态。

2、git remote -v   显示远程仓库地址的详细信息。

3、git branch  <分支名>     列出本地分支。

4、git branch -m  <分支名>     重命名当前分支。

5、git checkout  <分支名>     切换到指定分支。

6、git checkout -b  <分支名>     创建并切换到指定分支。

7、git branch -d  <分支名>        删除分支

8、git remote rename  <旧仓库名称>  <新仓库名称>   重命名本地 Git 仓库中的远程仓库名称



## 3、注意事项

1、命令不要敲错和漏敲了，一个字母敲错就error，很难发现的！

2、报错看error，根据error找问题（百度和gpt很香的）。

3、git push会经常碰到网络问题，可以设置ssh密钥（简略步骤）！

-    ssh-keygen -t rsa -b 4096 -C "邮箱地址xxx@xxx.com"  (密钥保存在 ~家目录/.ssh的文件夹)
-    id_rsa.pub里面的内容复制到GitHub的settings的SSH and GPG keys里面即可

4、参考文档是个好东西，要看细致了，漏看东西很致命！



<!--2025年1月6日-->

## 4、怎么PR（[参考文档](https://dtstack.github.io/chunjun-web/docs/chunjunDocs/contribute-pr/)）

### 第一步：fork仓库到自己仓库。

### 第二步：clone到本地。

### 第三步：添加源仓库地址链接。（upstream代表远程源仓库）

```
 # add upstream
 git remote add upstream https://github.com/DTStack/chunjun.git
 # 查看远程仓库设置
$ git remote -v
origin  https://github.com/your_name/chunjun.git (fetch)
origin  https://github.com/your_name/chunjun.git (push)
upstream    https://github.com/DTStack/chunjun.git (fetch)
upstream    https://github.com/DTStack/chunjun.git (push)
```

### 第四步：提交代码

任何一个提交都要基于最新的分支 **切换分支**

```
# 从源仓库（upstream）拉取所有分支信息和更新。
$ git remote update upstream -p
# 创建一个新的分支 branch_name，并切换到该分支。
$ git checkout -b branch_name
# 从源仓库 upstream 的 master 分支拉取最新代码，并合并到当前本地分支。
$ git pull upstream master:branch_name

  Already up to date.
```



**本地修改代码后，提交commit**

```
# 提交commit前先进行代码格式化
$ mvn spotless:apply
git commit -a -m "<you_commit_message>"
```

**rebase远程分支**

这一步很重要，因为我们仓库中的chunjun代码很有可能已经落后于社区，所以我们 push commit前需要rebase，保证我们的commit是基于社区最新的代码，很多小伙伴没有这一步导致提交的pr当中包含了其他人的commit

```
# 先从远程仓库拉取最新代码，确保本地了解远程分支的状态：
$ git fetch upstream
$ git rebase upstream/main

假设你正在一个名为 feature/branch_name 的分支上，远程主分支是 upstream/main。
运行后会发生以下情况：
Git 会将 feature/branch_name 分支上的提交临时保存起来。
将 upstream/main 的最新提交拉到本地。
重新将 feature/branch_name 的提交逐一应用到 upstream/main 的最新代码之上。
```

*rebase后有可能出现代码冲突，一般是由于多人编辑同一个文件引起的，只需要根据提示打开冲突文件对冲突部分进行修改，将提示的冲突文件的冲突都解决后，执行

```
$ git add .
$ git rebase --continue
```

依此往复，直至屏幕出现类似rebase successful字样即可

*rebase之后代码可能无法正常推送，需要`git push -f` 强制推送，强制推送是一个有风险的操作，操作前请仔细检查以避免出现无关代码被强制覆盖的问题

## 第五步：

**push到github仓库**

```
$ git push origin branch_name
```

## 第六步：提交pr







### 方法 3: 在作者没有合并前，删除所有本地提交并清理远程 PR

1、删除所有提交（硬重置到远程分支）

```
git reset --hard origin/main
```

2、强制推送删除更改到远程仓库

```
git push origin music --force
```





**一分耕耘，一分收获，       加油！**     



​																																
