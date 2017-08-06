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

+ {info, man} {grep, find}
+ grep Pocket Reference

**PS**: Both grep and find are used to search string, however, grep is usually
used in searching string in text file, and find is usually used in searching
the files in the system, so they are different. grep can work with regex, you
can study regex when learning grep. find is very useful in dealing with system
searching trancation. If you just want to make a simply and fastly searching,
you can use locate to do it. xargs is a great CMD to let a CMD to process
multi-file, it is vary useful and effective, but you should think about a
mount out the file it use just one command line to finish the job.


## Sed & AWK

+ {info, man} {sed,awk}
+ sed & awk
+ The awk programming language
+ Effective awk programming

**PS**: sed's advantage is to search and replace the text, what's more, it also
used to format the raw txt data, it is very useful in dealing with text line.
awk is a powerful text manipulating tool, it's syntax can also become a
programming language. Its strength is in dealing with text colum and making
report. All these two can work greatly well with regex, so you should learn
regex first.

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
