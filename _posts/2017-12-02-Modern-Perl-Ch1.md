---
layout: post
title: "[Modern Perl] Ch1: Perl 哲学"
date: 2017-12-02 13:07:38 +0800
categories: Note
tags: Perl
---

* content
{:toc}

# [[Modern Perl][MP]] Ch1: Perl 哲学

[MP]:http://www.modernperlbooks.com/books/modern_perl_2016/index.html

+ Perl gets things done -- 它是灵活(flexible)，大度(forgiving)，可塑造的(malleable)
+ Perl 是实效的(pragmatic)
+ Perl 伴你成长

## Perldoc

Perl 尊重你的时间，Perl 文化重视文档。语言本身就内置大量的核心文档，而`perldoc`工具是完整的 Perl 安装的一部分。`perldoc`不但可以查看核心文档，而且可以查看每个已安装模块的文档。

### 如何使用 perldoc 阅读文档 

`perldoc`的简单使用如下：
{% highlight shell %}
$ perldoc List::Util
$ perldoc perltoc
$ perldoc Moose::Manual
{% endhighlight %}

一些常用的阅读命令是
{% highlight shell %}
$ perldoc perl     # Perl 文档分类简介
$ perldoc perltoc  # 核心文档的内容介绍
$ perldoc perlfaq  # 经常问到的 Perl 相关问题
$ perldoc perlop   # Perl 的符号操作符
$ perldoc perlsyn  # Perl 的语法指令
$ perldoc perldiag # Perl 内置的警告信息
$ perldoc perlvar  # Perl 内置的符号变量
{% endhighlight %}

`perldoc`不但可以显示相关分类的文档，而且结合相应的 option 可以在相关分类里面进行内容查找：
{% highlight shell %}
$ perldoc -q keyword # 查找 FAQ 内容
$ perldoc -f func    # 查找内置函数使用文档
$ perldoc -v var     # 查找内置变量说明
$ perldoc -l doc     # 查找包含文档的文件路径
{% endhighlight %}

## 表达性(Expressivity)

Perl 的设计是模拟人与人之间的交流，这可以让你根据需要自由的编写程序。学习 Perl 就像学习任何口头语言，你可以学习一些词，然后将它们串联成句子，然后进行简单的对话。精通需要进行读写代码的练习。这种表达性让精通的人创造惊人的程序，让粗心的人制造混乱的代码。表达你自己，但是需要注意可读性以及可维护性，尤其是给那些后面接手你工作的人。

举个例子，把列表里的元素乘以3，新手：
{% highlight perl %}
my @tripled;
for (my $i = 0; $i < scalar @numbers; $i++) {
    $tripled[$i] = $numbers[$i] * 3;
}
{% endhighlight %}
进阶的：
{% highlight perl %}
my @tripled;
for my $num (@numbers) {
    push @tripled, $num * 3;
}
{% endhighlight %}
经验丰富的：
{% highlight perl %}
my @tripled = map { $_ * 3 } @numbers;
{% endhighlight %}

## 语境(Context)

Perl 使用语境去表示如何对待一段数据，这样可以控制数据的数量和类型。比如，一些 Perl 操作当你期望的是0,1或者许多结果的时候会表现出不同的行为，一些操作允许你指定数值的，文字的，或者布尔值的数据。当你阅读 Perl 代码的时候，你需要时刻记住语境的存在，每个表达式是一个大的语境的一部分。

### Void, Scalar 以及 List 语境

**量语境**控制一个操作产生多少个你期望的数据项，在 Perl 里，你要求多少个数据项影响到接收多少个。

假设你有一个保存 TODO list 的函数 `find_chores()`，当你调用这个函数而不使用它的返回值，你就在使用 **空值语境(void context)** ：
{% highlight perl %}
find_chores();
{% endhighlight %}
当你将函数的返回值赋值给单个数据项，你就在强制使用 **标量语境(scalar context)** ：
{% highlight perl %}
my $single_result = find_chores();
{% endhighlight %}
当你将函数的返回值赋值给一个数组，或者一个列表，或者将返回值像列表一样传递给例外一个函数时，你就在使用 **列表语境(list context)** ：
{% highlight perl %}
my @all_results             = find_chores();
my ($single_element, @rest) = find_chores();
my ($single_element)        = find_chores();

# list of results passed to a function
process_list_of_results( find_chores() );
{% endhighlight %}

### Numeric, String 以及 Boolean 语境

Perl 另外一个语境是 **值语境**，它影响 Perl 如何去解释一段数据。Perl 可以分辨出你有一个数还是字符串，并且可以在这两种类型之间进行转换。Perl 会根据你使用的操作符去强制指定合适的类型。

{% highlight perl %}
# eq 操作符强制它的操作数使用 字符串语境(string context)
say "alice is not bob!" if $alice eq $bob;

# == 操作符强制它的操作数使用 数值语境(numeric context)
my $alice = 'Alice';
say "alice is not bob!" if $alice == 'Bob';
{% endhighlight %}

如果需要强制值语境，你可以：

{% highlight perl %}
my $numeric_x =  0 + $x;  # forces numeric context
my $stringy_x = '' . $x;  # forces string  context
my $boolean_x =    !!$x;  # forces boolean context
{% endhighlight %}

## 隐含概念(Implicit Ideas)

Perl 代码第一眼看起来密度很大，但是它充满语言捷径(shortcuts)，语境(context)是其中一个捷径，另外一个捷径是**默认变量(default variables)** ，类似于发音。

### 默认标量变量(Default Scalar Variable)

默认标量变量`$_`被许多 Perl 内置操作使用，主要是在缺少明确的传递参数的时候。比如：`chr, chomp, ord, lc, length, print, reverse, say, uc`。`$_`在 Perl 里面表现的类似于英语里面的`it`发音，`chmop`默认是接收`$_`变量的，所以以下形式是等价的：
{% highlight perl %}
chomp $_;
chomp;
{% endhighlight %}
需要注意的是，`$_`是唯一的，共享的，如果你在某一个函数里面改变了它，其他函数的`$_`也会发生变化。

### 默认数组变量(Default Array Variables)

除了默认标量变量以外，Perl 还提供 2 个默认数组标量：`@_`，`@ARGV`。Perl 通过`@_`给函数传递参数，函数内部的数组操作符默认使用这个变量：
{% highlight perl %}
sub foo {
    my $arg = shift;
    ...
}
sub foo_explicit_args {
    my $arg = shift @_;
    ...
}
{% endhighlight %}
类似于`$_`之于`it`，`@_`可以比作英语里面的`they`或者`them`，但是不同的是，每个函数都有自己的`@_`。

在所有函数之外，`@ARGV`包含了传递给程序的命令行参数，Perl 的数组操作符在函数之外隐含使用`@ARGV`，所以当你需要`@ARGV`时，你不能狗用`$_`去代替。`@ARGV`有一个特例就是，当你使用空的文件句柄`<>`时，Perl 打开`@ARGV`里面所有的文件进行读取，如果`@ARGV`是空的，Perl 会从标准输入进行读取。
