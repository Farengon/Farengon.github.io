---
layout: default
title: Unit 1：基本类型 (Primitive Types)
parent: AP CSA
nav_order: 1
---

# Unit 1：基本类型 (Primitive Types)

在 Java 中，所有的数据都有其类型。这一章我们主要学习最基础的三种数据类型。

## 1. 常见基本类型

* **`int`**: 整数类型（例如 `int age = 16;`）
* **`double`**: 双精度浮点数/小数（例如 `double price = 19.99;`）
* **`boolean`**: 布尔值，只有 `true` 和 `false`（例如 `boolean isPassed = true;`）

## 2. 算术运算符 (Arithmetic Operators)

注意 Java 中的**整数除法**：
```java
int a = 5;
int b = 2;
System.out.println(a / b); // 输出 2，而不是 2.5！因为整数相除会截断小数部分。