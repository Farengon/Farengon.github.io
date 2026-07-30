---
layout: default
title: 1.5 Casting and Range of Variables
parent: Unit 1
nav_order: 5
---

# 1.5 Casting and Range of Variables

## 1.5.A

**Develop code to cast primitive values to different primitive types in arithmetic expressions and determine the value that is produced as a result.**

### 1.5.A.1 Casting Operator 类型转换运算符

{: .syntax}
> `(int)double_value` 将 double 转换为 int
>
> `(double)int_value` 将 int 转换为 double

注意类型转换的优先级比算术运算的优先级更高。

```java
System.out.println((int)3.5 * 4);  // 先算 (int)3.5 = 3，再算3 * 4 输出 12
System.out.println((int)(3.5 * 4));  // 先算 3.5 * 4 = 17.0，再算 (int)17.0 输出 17
```

### 1.5.A.2 double to int

使用 `(double)` 将 double 类型的值被转换为 int 时，直接舍弃小数部分，**不是四舍五入**。

{: .note}
> 本课程考试涉及到所有的小数转整数都是丢弃小数部分。**牢记**。

### 1.5.A.3 Auto Casting 自动类型转换

在某些情况下类型转换的发生是**隐式**的，尽管代码中没有显式使用类型转换运算符，但数据类型确实发生了转换。例如：

```java
int a = 3
double b = a; // 使用 int 给 double 变量赋值，3 被自动转换为 3.0
```

本课程只需要掌握 int 到 double 存在自动类型转换。

{: .extra}
> 原因是 int 的表示长度比 double 更短，因此 int 可以“拓宽”到 double。
>
> 实际上，Java 中“更短”到“更长”的类型之间都可以自动类型转换。  
> byte → short → int → long → float → double

### 1.5.A.4

在 Java 中实现四舍五入的方法：

```java
// assume x is a double variable, to get its nearest int, use:
(int)(x + 0.5)  // if x > 0
(int)(x - 0.5)  // if x < 0
```

## 1.5.B

**Describe conditions when an integer expression evaluates to a value out of range.**

### 1.5.B.1 Integer's Range 整数的范围

在 Java 中，int 的值并不能无限大，而是存在一个范围

{: .syntax}
> Java 中最大的整数用 `Integer.MAX_VALUE` 表示
>
> Java 中最小的整数用 `Integer.MIN_VALUE` 表示

{: .note}
> Integer.MAX_VALUE 和 Integer.MIN_VALUE 本质上也是两个 int 类型的变量。

### 1.5.B.2 Integer Storage 整数的存储

Java 中每个整数（int 类型）占用的内存是固定的 4 个字节，这是 int 存在最值的**原因**。

{: .extra}
> 1 字节（byte）= 8 比特（bit）
> 
> 1 比特就是一个二进制位（0 或 1）。一个 int 本质就是一个 32 位的二进制数，其中最高位用于表示符号。
>
> Integer.MAX_VALUE = 2^31-1  
> Integer.MIN_VALUE = -2^31

### 1.5.B.3 Integer Overflow 整数溢出

如果一个表达式的结果是 int 类型，那么结果一定在 Integer.MAX_VALUE 和 Integer.MIN_VALUE 范围内。

如果结果的数值在范围外，则会造成**溢出**，这个值会被“修改”成一个合法的范围内的整数，但在数学上不是正确的结果。例如：

```java
System.out.println(Integer.MAX_VALUE);  // 2147483647
System.out.println(Integer.MAX_VALUE + 1);  // -2147483648, an integer overflow occurs
```

整数溢出会造成结果错误，但并不会中断程序运行，也不会有报错信息，是一种容易被忽略但时常出现的 bug。

## 1.5.C

**Describe conditions that limit accuracy of expressions.**

### 1.5.C.1 Round-off Error 舍入误差

不仅仅是 int，Java 中所有数据类型都有固定的内存分配。

有时，有限的二进制位无法精确表示小数，这会带来微小的误差。例如

```java
System.out.println(0.1 * 3); // 0.30000000000000004
```

{: .extra}
> 0.1 的二进制表示是 0.00011001100110011...，是一个无限小数，因此并不能被有限的二进制位来表示。

为了减少舍入误差，尽量使用 int 类型来运算。
