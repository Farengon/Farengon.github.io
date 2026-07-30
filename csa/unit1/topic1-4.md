---
layout: default
title: 1.4 Assignment Statements and Input
parent: Unit 1
nav_order: 4
---

# 1.4 Assignment Statements and Input

## 1.4.A 

**Develop code for assignment statements with expressions and determine the value that is stored in the variable as a result of these statements.**

### 1.4.A.1 Variable Initialization 变量初始化

变量在被使用前必须先赋值。变量被声明后的第一次赋值被称作变量的初始化。

只能使用和变量的数据类型**兼容**的值来对变量赋值。

对于 reference type，可以使用 [null] 进行初始化。

### 1.4.A.2 Assignment 赋值

使用赋值号（=）对变量赋值。

{: .syntax}
> variable = expression
>
> 将右侧表达式的值存到左侧的变量中。

对变量赋值会**覆盖**变量原来的值。

```java
int a;  // 声明变量 a
a = 1;  // 初始化变量 a
int b = 2;  // 声明 & 初始化变量 b
b = 3;  // 修改变量 b 的值为 3
```

### 1.4.A.3 

程序执行过程中，表达式会被计算并生成一个值。在赋值语句中，先计算表达式的结果，再将结果赋值给变量。

## 1.4.B

**Develop code to read input.**

### 1.4.B.1 Input 输入

本门课程中我们只需要掌握文本的输入，即使用键盘输入文字。

在 Java 中，通常使用 Scanner 类来处理键盘输入。

在后续的[文件（file）](/csa/unit4/topic4-6)章节中将详细讨论 Scanner 的用法。
