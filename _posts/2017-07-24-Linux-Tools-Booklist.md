---
layout: post
title: "Linux Tools Booklist"
date: 2017-07-24 22:58:21 +0800
categories: Booklist
tags: Tools Vim
---

* content
{:toc}

# Linux Tools Booklist

这是一份关于 Linux 日常工具相关的书单。

## Grep & Find

+ `$ {info,man} {grep,find}`
+ grep Pocket Reference

`grep` 和 `find` 都是 Linux 下的查找工具，都是通过字符串查找，并且支持 regexp，
但是它们各自的查找对象是不同的，grep 的查找对象是**文本内容**，而 find 的查找
对象是**文件系统的文件名**。grep 是 GNU regexp 的缩写，find 是 findutils 工具
包的一个工具，其中包含：find、xargs、locate 等工具，有些系统会把 locate 工具从
findutils 分离出来形成独立的 mlocate 的软件包，find 一般随 Linux 发行版一起发
行，但是 mlocate 需要独立安装。

## Sed & AWK

+ `$ {info,man} {sed,awk}`
+ Sed & AWK /《sed 与 awk》
+ The AWK Programming Language /《AWK 程序设计语言》
+ Effective AWK Programming /《高效 AWK 编程》

sed 是一个流编辑器，一般用在文字查找和更替，并且可以格式化 RAW 文本数据。
awk 也可以进行文字查找和更替，但是 awk 比 sed 更强大，因为 awk 包含数据类型，逻
辑控制，可以引入第三方库，这已经可以看作一门编程语言了。

## Make

`make` 是一个项目管理工具，根据 Makefile 来检测项目的生成文件是否需要重新编译，
若需要，则根据 Makefile 里面定义的 rules 去重新编译生成。

+ `$ {info, man} make`
+ Managing Projects with GNU make /《GNU Make 项目管理》
+ The GNU Make Book

## Autotools

Autotools 是 GNU 程序的构建工具集，包含：autoconf、automake、libtool。小程序，
小项目一般只需要手写 Makefile 就 OK 了，但是如果大型的软件项目，手写就比较麻烦，
所以需要一系列的工具去自动生成 Makefile，而 Autotools 正为此而生。

+ `$ {info, man} {autoconf, automake, libtool}`
+ Autotools

**PS**: 学习 Autotools 之前一定要有 Makefile 的相关知识，因为 Autotools 是以
 Makefile 为基础的，最终生成的也是 Makefile。

## Vim

+ Learning the vi and Vim Editors /《学习 vi 和 Vim 编辑器》
+ Practical Vim /《Vim 使用技巧》
+ Pro Vim
+ [Use Vim as IDE](https://github.com/yangyangwithgnu/use_vim_as_ide)
+ vi and Vim Editor Pocket Reference
+ `$ vim -c help`

尽管 Linux 上的编辑器很多，但是 vi/Vim 可谓是最经典的编辑器之一，因为几乎所有的
Linux 系统都会安装 vi/Vim。vi 是可视化输入编辑器，而 Vim 是 vi 的改进版，或者说
是增强版，添加了许多传统 vi 没有的功能特性，使其变得更加强大。虽然 Vim 并不是开
箱即非常好用的，甚至有点过于简单，但是经过配置和调教，增加功能插件，一定何以满
足你在编辑上，特别是在编写程序的体验。一旦熟悉了 Vim 的操作，就能够提升编辑的效
率，甚至有种爱不释手的感觉。在学习 Linux 的道路上，我认为 Vim 是值得尝试学习的。
