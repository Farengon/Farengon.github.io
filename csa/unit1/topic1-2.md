---
layout: default
title: 1.2 Variables and Data Types
parent: Unit 1
nav_order: 2
---

# 1.2 Variables and Data Types

## 1.2.A

**Identify the most appropriate data type category for a particular specification.**

### 1.2.A.1 Data Type 数据类型

在 Java 中，所有的数据都具有数据类型。当我们使用程序解决实际问题的时候，需要根据要求用不同类型的数据来进行表示。

Java 中的数据类型分为 primitive data type 和 reference data type 两类。

### 1.2.A.2 Primitive Data Type

Java 共有 8 种 primitive type，了解即可，不需要记忆：

{: .extra}
> byte, short, int, long, float, double, boolean, char

### 1.2.A.3 Reference Data Type

除 primitive type 外的数据类型都是 reference type。

reference type 用来定义对象。

## 1.2.B

**Develop code to declare variables to store numbers and Boolean values.**

### 1.2.B.1 Primitive Type in CSA

CSA 课程涉及到以下3种primitive type

| 类型 | 描述 | 范围 |
|------|------|------|
| `int` | 整数 | -2,147,483,648 到 2,147,483,647 |
| `double` | 双精度浮点数 | ±4.9e-324 到 ±1.7e+308 |
| `boolean` | 布尔值 | `true` 或 `false` |

### 1.2.B.2 Variable 变量

变量是用来**储存**数据的。每一个变量都有自己的**数据类型**和**变量名**，并会储存一个**值**。

数据类型和变量名是变量的两个核心属性，使用以下语法定义变量：

{: .syntax}
> data_type variable_name

例如

```java
int score;  // 一个叫做score的整数变量
double temprature;  // 一个叫做temperature的浮点数变量
boolean flag;  // 一个叫做flag的布尔变量
```

变量的数据类型和变量名在定义后，**永远不变**。

变量的值在程序运行的过程中通常会发生改变。

primitive 类型的变量储存值本身；reference 类型的变量储存对象的**引用/地址**。关于primitive type和reference type存储方式的讨论
