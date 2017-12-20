---
layout: post
title: "[Modern Perl] Ch2: Perl 社区"
date: 2017-12-11 18:49:33 +0800
categories: Note
tags: Perl
---

* content
{:toc}

# [[Modern Perl][MP]] Ch2: Perl 社区

[MP]:(http://www.modernperlbooks.com/books/modern_perl_2016/index.html)

Perl 最伟大的成就是拥有完备的可用代码库，Perl 之父 Larry Wall 明确鼓励 Perl 社区创造并维护他们自己的扩展去解决问题。Perl 欢迎各个层级的参与者，从新手到 Perl 自身开发者。从其他有经验的程序员编写的代码进行学习，这会让你变成更好的程序员。

## [CPAN](http://www.cpan.org/)

CPAN(Comprehensive Perl Archive Network)是一个可分发，可复用 Perl 代码的上传、镜像系统，这是 Modern Perl 一个强大的工具箱。CPAN 管理着可复用 Perl 代码的**分支(distribution)** ，或者是集合。一个分支包含一个或多个**模块(modules)** 。一个分支拥有自己的 CPAN 名字空间(namespace)并且提供相关元数据(metadata)。

CPAN 额外提供完备的自动化测试以及跨平台和版本的测试报告。每个 CPAN 分支拥有自己的 [ticket queue](http://rt.cpan.org/) 用于报告 bugs 以及与作者互动。CPAN 网站还提供以往的分支版本，模块评分，文档注释等，所有这些都可以通过 http://search.cpan.org/ 和 http://metacpan.org 进行浏览。

现代的 Perl 安装基本都会包含一个连接，查找，下载，构建，测试和安装 CPAN 分支的客户端，这就是`CPAN.pm`。简单的安装模块操作如下：
```shell
$ cpan
cpan[1]> install Modern::Perl
```
或者直接从命令行安装模块：
```shell
$ cpan Modern::Perl
```

### CPAN 管理工具

系统自带的 Perl 一般情况下是旧版的，严谨的开发者会自行安装新版的 Perl，所以管理不同版本的 Perl就变得有必要了。

#### `App::cpanminus`

`App::cpanminus`是一个快捷，简单，无需配置的 CPAN 客户端，安装方法如下：
```shell
$ curl -LO http://xrl.us/cpanm
$ less cpanm # review the code before running
$ chmod +x cpanm
$ ./cpanm
```

#### `App::perlbrew`

`App::perlbrew`是一个管理 Perl 的多版本还有配置的系统，安装同样简单：
```shell
$ curl -LO http://xrl.us/perlbrew
$ less perlbrew # review the code before running
$ chmod +x perlbrew
$ ./perlbrew install
$ perldoc App::perlbrew
```

## 社区网站

[Perl 主页](http://www.perl.org/)有文档，源码，入门教程，邮件列表以及重要的社区项目，比如 [Perl.org Onlne Library](https://www.perl.org/books/library.html)。如果你是 Perl 新手，Perl [新手](http://learn.perl.org/faq/beginners.html)邮件列表是一个提问的好地方。

+ [Perl Development](http://dev.perl.org/)
+ [CPAN](http://www.cpan.org/)
+ [Search CPAN](http://search.cpan.org/)
+ [metacpan](http://matacpan.org/)
+ [Perl Blogs](http://blogs.perl.org/)
+ [Perl Weekly](http://perlweekly.com/)
+ [@perlbuzz](https://twitter.com/perlbuzz/)

## 开发网站

+ [Best Practical Solutions](http://bestpratical.com/)维护着一个 RT，这是一个流行的 Perl 开发需求跟踪系统
+ [Perl Queue](http://rt.perl.org/)
+ [perl5-porter mailing list](http://lists.cpan.org/showlist.cgi?name=perl5-porters)
+ [Perl Foundation](http://www.perlfoundation.org/)
+ [Github](https://github.com/)

## 事件

+ [YAPC(Yet Another Perl Conference)](http://yapc.org/)
+ [Perl Mongers](http://www.pm.org/)

## IRC

+ [IRC Perl](irc://irc.perl.org)
