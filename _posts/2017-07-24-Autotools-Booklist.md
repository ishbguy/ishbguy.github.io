---
layout: post
title: "Make & Autotools Booklist"
date: 2017-07-24 22:39:50 +0800
categories: Booklist
tags: Tools
---

* content
{:toc}

# Make & Autotools Booklist

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
