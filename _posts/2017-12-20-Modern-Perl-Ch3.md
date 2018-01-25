---
layout: post
title: "[Modern Perl] Ch3: Perl 语言"
date: 2017-12-20 14:40:52 +0800
categories: Note
tags: Perl
---

* content
{:toc}

# [[Modern Perl][MP]] Ch3: Perl 语言

[MP]:http://www.modernperlbooks.com/books/modern_perl_2016/index.html

Perl 语言是一种结合了多种不同部分的语言。尽管口头语言使用语音语调以及直觉去沟通和理解，但是计算机和源代码需要的是精确表达。虽然你可以不了解每个语言特性就能写出高效的 Perl 代码，但是为了写出更好的 Perl 代码你必须理解代码是怎样工作的。

## 名字(Names)

Perl 程序里面的变量，函数，包，类，甚至文件句柄都使用名字，有效的 Perl 名字以字母或下划线开头，后面任意结合字母，数字或者下划线。当开启了 utf8 编译指示(pragma)后，你还可以使用任何 UTF-8 字符作为名字的一部分。

### 变量名和印记(Sigils)

变量名一般会以一个印记开头，这个印记可以指示变量的类型。**标量(Scalar)变量**使用`$`，**数组(Array)变量**使用`@`，**哈希(Hash)变量**使用`%`：

{% highlight perl %}
my $scalar;
my @array;
my %hash;
{% endhighlight %}

印记将变量分离在不同的**名字空间(namespace)** ，你可以使用相同的名字去命名不同的变量类型，但是这会让人产生误解。

{% highlight perl %}
my ($bad_name, @bad_name, %bad_name);
{% endhighlight %}

变量的印记根据使用而改变，这个叫**变种印记**。类似于语境决定你希望从一个操作中返回多少个元素或者希望获得什么样的数值，印记控制着如何操作数据。例如，使用`$`印记去访问数组或哈希的单个元素：

{% highlight perl %}
my $hash_element  = $hash{ $key };
my $array_element = $array[ $index ];

$hash{ $key }     = 'value';
$array[ $index ]  = 'item';
{% endhighlight %}

这个与量语境(amount context)一起使用是非常重要的。

同理，要访问数组或哈希的多个元素，一般叫做**切片(slicing)** ，使用`@`印记以及列表语境(list context)：

{% highlight perl %}
my @hash_elements  = @hash{ @keys };
my @array_elements = @array[ @indexes ];
my %hash;
@hash{ @keys }     = @values;
{% endhighlight %}

### 名字空间(Namespaces)

Perl 允许你将同类的函数和变量集中放在一个独立的命名空间，叫做名字空间或包(Packages)。Perl 允许多级的名字空间，名字空间之间使用`::`连接，如`DessertShop::IceGream`。在名字空间里面，可以使用简短的函数名和变量名，但是在名字空间意外，需要使用全路径形式的名字，如：`DessertShop::IceCream::add_sprinkles()`。

Perl 惯例保留小写字母的包名字给 Perl 核心程序，例如`strict`和`warning`。用户定义的包全部以大写字母开头。所有名字空间在 Perl 里面都是全局可见的。

## 变量(Variables)

变量是一个保存值(values)的容器。类似数学里面利用符号去描述公式，让人更加容易理解。

### 变量的作用域(Variable Scopes)

你的程序能够访问一个变量依靠的是变量的作用域。在现代 Perl 里面大部分的变量都有一个被程序语法所控制的**词法作用域(Lexical Scope)** 。大部分的词法作用域要么是`{}`代码块里面的内容，要么是整个文件，文件单独提供它们自己的词法作用域，比如**包(package)** 的声明:

{% highlight perl %}
package Store::Toy;
my $discount = 0.10;
package Store::Music;
# $discount 依旧可见
say "Our current discount is $discount!";
{% endhighlight %}

你也可以在包声明的时候提供块(block)，这会产生一个新的词法作用域：

{% highlight perl %}
package Store::Toy {
   my $discount = 0.10;
}
package Store::Music {
   # $discount not visible
}
package Store::BoardGame;
# $discount still not visible
{% endhighlight %}

### 变量印记(Variable Sigils)

变量声明时的印记决定了变量的类型：scalar，array 或者 hash。变量访问时的印记根据使用而变得不同，例如，你定义了一个 array 为 `@values`，访问第一个元素的形式为 `$values[0]`，访问一组元素的形式为 `@values[ @indices ]`。印记作为左值(lvalue)时决定量语境：

{% highlight perl %}
# imposes lvalue context on some_function()
@values[ @indexes ] = some_function();
{% endhighlight %}

或者作为右值(rvalue)时强制转换(coerced)：

{% highlight perl %}
# list evaluated to final element in scalar context
my $element = @values[ @indices ];
{% endhighlight %}

### 匿名变量(Anonymous Variables)

Perl 的变量不需要名字，名字的存在只是为了帮助程序员跟踪变量。没有名字的变量是匿名的，只有通过**引用(reference)** 才能访问匿名变量。

### 变量，类型和强制转换

变量类型，印记和语境之间的关系是 Perl 的关键部分。

Perl 变量表示值和存储值的容器(container)。Perl 的类型系统处理值类型和容器类型，一个变量的容器是不能改变的，但是变量的值是灵活的，你可以存储一行字符串在一个变量里，然后在后面追加一个数。

对一个变量执行一个需要指定值类型操作会导致强制转换：

{% highlight perl %}
my $count = @items; # 得到 array 的元素个数
{% endhighlight %}
