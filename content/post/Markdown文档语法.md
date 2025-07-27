---
title: Markdown文档语法
date: 2024-10-09T21:26:06+08:00
tags: 
series: 
featured: true
---
把Markdown文档比作word的话，这篇文章就是教你怎么使用word.

什么是Markdown文档：技术人眼中很方便的写作工具！

<!--more-->

**官方解释**：Markdown是一种轻量级标记语言，排版语法简洁，让人们更多地关注内容本身而非排版。它使用易读易写的纯文本格式编写文档，可与HTML混编，可导出 HTML、PDF 以及本身的 .md 格式的文件。因简洁、高效、易读、易写，Markdown被大量使用，如Github、Wikipedia、简书等。

## 1、标题语法

要创建标题，请在单词或短语前面添加井号 (`#`) 。`#` 的数量代表了标题的级别。例如，添加三个 `#` 表示创建一个三级标题 (`<h3>`) (例如：`### My Header`)。

# #  +文字 ：一级标题  

## ## +文字：二级标题

### ### +文字：三级标题



## 2、引用语法

要创建块引用，请在段落前添加一个 `>` 符号。

```text
> Dorothy followed her through many of the beautiful rooms in her castle.
```

展示效果：

>  Dorothy followed her through many of the beautiful rooms in her castle.



## 3、Markdown 代码语法

要将单词或短语表示为代码，请将其包裹在反引号 (```) 中。

展示效果（红字部分）：

At the command prompt, type `nano`.

## 4、Markdown 分隔线语法

要创建分隔线，请在单独一行上使用三个或多个星号 (`***`)、破折号 (`---`) 或下划线 (`___`) ，并且不能包含其他内容。

展示效果（从上到下依次：***、---、___）：

***

---

___

## 5、Markdown 链接语法

链接文本放在中括号内，链接地址放在后面的括号中，链接title可选。

超链接Markdown语法代码：`[超链接显示名](超链接地址 "超链接title")`

对应的HTML代码：`<a href="超链接地址" title="超链接title">超链接显示名</a>`

```text
这是一个链接 [Markdown参考网站](https://markdown.com.cn/basic-syntax/)。
```

展示效果：

这是一个链接 [Markdown参考网站](https://markdown.com.cn/basic-syntax/)

# 6、Markdown 图片语法

要添加图像，请使用感叹号 (`!`), 然后在方括号增加替代文本，图片链接放在圆括号里，括号里的链接后可以增加一个可选的图片标题文本。

插入图片Markdown语法代码：`![图片alt](图片链接 "图片title")`。

```text
![这是图片](/images/blog/1.png "图片标题")
```

![这是图片](/images/blog/1.jpg "图片标题")

图片链接地址也可以为外链地址，像这样：https://www.rwany.net/uploads/money/weixin.jpg（浏览器里面输入这个地址能直接访问到！）

外链地址的优势：博客搬家时，大量引用的图片地址仍然有效！不会占用服务器资源，增加访问速度！





***

最后：上述只是部分Markdown文档语法，完全够新手使用，后续可以自己学习更多的语法来编写自己的文章！
