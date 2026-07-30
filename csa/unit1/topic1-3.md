---
layout: default
title: 1.3 Expressions and Output
parent: Unit 1
nav_order: 3
---

# 1.3 Expressions and Output

## 1.3.A

**Develop code to generate output and determine the result that would be displayed.**

### 1.3.A.1 Output 输出

{: .syntax}
> `System.out.print()`  
> `System.out.println()`  
> 括号中写需要输出的内容

`println` 中的 `ln` 可以看作 line 的缩写，使用`System.out.println()`输出后光标会自动移动到**下一行**，后续的输出将从下一行开始。使用`System.out.print()`输出后光标停留在原地，后续的输出将紧接此次输出。

## 1.3.B

**Develop code to utilize string literals and determine the result of using string literals.**

### 1.3.B.1 Literal

值的代码表达。三种 primitive type 的表示：

- int 整数：32，199，8232，-11，0，666...

- double 小数：2.1，0.637，133.322...

- boolean 布尔值：true，false

### 1.3.B.2 String Literal

使用双引号表示字符串：

"java", "Hello", "32", "2.1", "true", "&* ds8^$"...

{: .note}
> 字符串是由字符连接而成，包括所有的可见和不可见字符。
>
> 字符串是一种 reference 类型，字符串 "32" 和整数 32 不同，字符串 "True" 和布尔值 True 不同，不要搞混。

### 1.3.B.3 Escape Sequence 转义序列

在字符串中使用反斜杠（\）加特定的字符可以定义转义序列。本课程中会涉及的转义序列有三种：

- `\"`: 表示这个位置是一个双引号字符，不参与字符串定义的引号匹配。

    - "hi"java" 是错误的表达，因为双引号从前往后匹配，Java会将这个表达解释为字符串"hi"和一串不符合语法的乱码。

    - "hi\"java" 是正确的表达，这个字符串的值是 hi"java。

- `\\`: 表示这个位置是一个反斜杠字符。

- `\n`: 表示在这里换行。

## 1.3.C

**Develop code for arithmetic expressions and determine the result of these expressions.**

### 1.3.C.1 Arithmetic Expression 算术表达式

用于算术运算，包括**操作数**和**运算符**，操作数可以是 int 或 double 类型的值或变量。

一个算术表达式可以得到一个数值结果。

### 1.3.C.2 Arithmetic Operator 算术运算符

包括 +，-，*，/，% 五种运算符。

{: .important}
> 对于一个算术表达式 `操作数1 操作符 操作数2`
> 
> 只要操作数中有 double 类型，结果一定是 double 类型。
> 
> 只有当两个操作数都是 int 类型，结果才是 int 类型。
>
> 结果的类型与**数值无关**。例如
>
> `2.5 * 4` 的结果是 double 类型的 10.0，尽管在数学上 10 是一个整数。

### 1.3.C.3 Dividing 除法

两个整数相除得到的结果是商的整数部分（**int 类型**）。**不是四舍五入！**

只要有一个 double 类型的操作数，得到的就是精确的商（**double 类型**）。

{: .extra}
> 实际上由于精度限制，如果商是无限小数，计算机也只能得到一个近似值。

### 1.3.C.4 Remainder 模运算

模运算（%）用于计算**余数**。

`a % b` 得到 a 除以 b 的余数。

{: .extra}
> a < 0 和 b <= 0 的情况不在课程考察范围内。

### 1.3.C.5 Compound Arithmetic Expression 复合算术表达式

对于一个复合的算术表达式，按照括号 > 乘除模（* / %）> 加减（+ -）的优先级顺序依次计算。

### 1.3.C.6 Dividing by Zero

用整数除以 0 会导致 **ArithmeticException**。

{: .note}
> 使用 double 除以 0 不会导致异常，这不在课程考察范围内。
>
> 因此,考试时看到 0 在除数的位置上时一定可以确定引发异常。反过来，题目如果问如何才会出现 ArithmeticException，要想到令除数为0。
