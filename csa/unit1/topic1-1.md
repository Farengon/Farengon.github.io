---
layout: default
title: 1.1 Introduction to Algorithms, Programming, and Compilers
parent: Unit 1
nav_order: 1
---

# 1.1 Introduction to Algorithms, Programming, and Compilers

本节主要是基础概念，考试涉及很少，了解即可。

## 1.1.A 

**Represent patterns and algorithms found in everyday life using written language or diagrams.**

### 1.1.A.1 Algorithm 算法

算法是一组**按顺序**执行的指令，用于解决问题或完成任务。

### 1.1.A.2 Sequencing

序列化用于定义流程中各步骤完成的顺序。流程中的步骤会**依次完成**。

{: .highlight}
> 对于第一次接触编程的同学，大家要明确一点：**在AP CSA课程中的**计算机程序的执行流程都是**确定**的**单步**执行。尽管程序的执行似乎在瞬间得到了结果，实际上代码是从程序的入口开始按照既定的步骤一行一行**顺序**地执行。

## 1.1.B

**Explain the code compilation and execution process.**

### 1.1.B.1 IDE 集成开发环境

IDE 即 Itegrated Development Environment 集成开发环境，在其中不仅仅可以写代码，同时可以直接在其中编译和运行。

{: .extra}
> 现代的 IDE 几乎都有自动补全和纠错功能，甚至有 AI 辅助（例如 VSCode 中的 Copilot），believe me，没有一个程序员可以拒绝这些功能。
>
> 当然，为了达到学习的目的，建议大家在做练习的时候关闭 AI 助手🙅‍。

### 1.1.B.2 Compiler 编译器

所有的编程语言都是给**人类**使用的，计算机并不认识 Java 语言。计算机只认识由0和1组成的**二进制码**。编译器的主要工作就是将人类语言翻译成机器码。

Java 编译器还会做**静态检查**。Java 的语法非常严格，如果程序的语法有误，那么编译器将无法编译，程序也就无法执行。

## 1.1.C

**Identify types of programming errors.**

### 1.1.C.1 Syntax Error 语法错误

不仅仅是 Java，所有的编程语言都遵循一定的语法。语法错误可以被编译器找到。存在语法错误的程序无法运行，尝试运行带有语法错误的程序时会得到编译器的**报错**，可以利用这一点来检查语法错误。

{: .extra}
> 在 IDE 中，语法错误通常会被红色波浪线标出。

### 1.1.C.2 Logic Error 逻辑错误

逻辑错误是指算法或程序中存在的缺陷，导致其行为异常或出乎意料。此类错误可通过使用特定数据**测试**程序来检测。通过**插入输出语句**显式查看程序运行过程中的数值变化也是一种常用的手段。

{: .note}
> 存在逻辑错误的程序可以运行，但运行的结果**有时**会出错，这常常会成为安全隐患。
>
> 例如这里有两堆苹果，一堆有 x 个，另一堆有 y 个，正确的算法是 `x+y`。
>
> 一个语法错误的程序可能是 `x加y`，编译器不认识中文，于是无法编译和运行；
> 
>  一个逻辑错误的程序可能是 `x-y`，它可以正常运行，并且当 y=0 时甚至能得到正确答案，但在大部分时候（y > 0 时）得到的是错误答案。我们只需要测试几组数据就可以找到这个 bug。
>
> 真实情况当然比这要复杂得多。因此在真实的程序开发中，有一个重要的职位**测试工程师**，专门负责找到程序中的错误和漏洞。

### 1.1.C.3 Run-time Error 运行时错误

程序在执行**过程中**出现的错误。这类错误通常会导致程序**异常终止**。

### 1.1.C.4 Exception 异常

异常是一种**运行时错误**，由编译器未能检测到的意外错误引发，并会中断程序的执行。

后续章节中涉及到的 Exception：