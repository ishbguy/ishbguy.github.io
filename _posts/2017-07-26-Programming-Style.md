---
layout: post
title: "Programming Style"
date: 2017-07-26 23:52:21 +0800
categories: Pattern
tags: Coding
---

* content
{:toc}

# Programming Style

Here are some rules for coding to construct my own programming style, I will
make convention with name, expression/statement, format, procedure, comment.

## Name 

Name should be:

1. Simple
2. Readable
3. Descritive
4. Exact
5. Memerable
6. Uniform

I divide name into 4 kinds, they are variable, class/struct, constant/macro,
function and class.

### Variable

Variable can also be divided into local variable and global variable, they all
be **noun**.

#### Local Variable

Local variable include normal variable, argument variable and temporary
variable. They all should be:

1. Short enough.
2. Start with lower case.
3. Use convention prefix or suffix:
    - i, j, k       looping variables
    - p, ptr        pointer
    - s, str        string
    - m_, mem       member
    - fp, fun       function pointer

#### Global Variable

Don't use global variable anymore.

Global variable should be:

1. Don't use abbreviation
2. Start with upper case
3. Describe more detail

### Class/Struct

Class and struct act as new type in coding, they should be **noun**, too.

1. Use one word noun if possible.
2. Start with upper case.
3. Member of class/struct should be one word noun as possible.

### Constant/Macro

Constant and Macro act as a notation for readable and memerable, so they should
be:

1. Whole name should be upper case.
2. Use "_" to seperate word if necessary.

### Function

Function is a procedure abstraction, it can be use to process data, it should
be:

1. Use verb-noun style.
2. Start with lower case if possible.

## Expression and Statement

1. Add 1 space beside operator.
2. 1 space folowing controling keyword.
3. "{" stay with statement and follow with newline "\n" beside function.
4. Indent with 4 spaces, and tabstop is 4.
5. Use "()" to clarify the meanning.
6. Directly express youself.
7. Divide complicated expression.
8. Avoid to use nested "?:" expression.
9. Use convention coding style.
10. Avoid to use macro function, if necessary, add "()" to macro body and arguments.
11. Use language to calculate the size.
12. Declare constant number with const or enum, avoid to use macro, use enum instead.
13. Don't use a macro function as an argument.
14. Arguments of macro function shouldn't have side effect.
15. Avoid to use goto.

## Comment

1. Comment for function and global variable.
2. Don't comment bad code, rewrite it.
3. Comment the same meaning with code.
4. Use Doxygen stye comment with API.
5. Don't comment for comment.

## Format

1. Space to seperate code block.
2. Variable should be declared as close as their usage.
3. Initial variable should be declared at the top of the code block.
4. Sort out the code block kind, place same kind code in same block.
5. A file should not be over than 500 lines, a line should not be over than 120 chars.

## Procedure

1. Check condition in caller, assert in callee(DEBUG, TEST).
2. Check error in callee, solve in caller.

