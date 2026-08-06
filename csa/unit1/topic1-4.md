---
layout: default
title: 1.4 Assignment Statements and Input
parent: Unit 1
nav_order: 4
---

# 1.4 — Assignment Statements and Input

---

## 1.4.A 赋值语句

### 1.4.A.1 变量必须先赋值再使用

每个变量在表达式中被使用之前，**必须已经被赋值**。该值必须来自一个**兼容的数据类型**。变量被**初始化（initialized）** 是指它第一次被赋予一个值的那一刻。

引用类型（reference types）可以被赋值为一个新对象，也可以赋值为 `null`——`null` 是一个特殊值，表示该引用不关联任何对象。基本类型（primitive types）不能赋值为 `null`。

{: .important}
> 仅仅声明变量是不够的——在使用变量之前必须确保它已经被赋值（初始化）。尝试使用未初始化的变量会导致编译错误。

---

### 1.4.A.2 赋值运算符 =

赋值运算符 `=` 允许程序**初始化**或**改变**变量中存储的值。**等号右侧的表达式先被求值，然后将结果存入左侧的变量中**。

赋值语句的基本形式：

```java
variable = expression;
```

执行过程：

1. 计算右侧表达式的值，得到一个单一的结果
2. 将该结果存入左侧变量中（**覆盖**该变量之前的值）

{: .extra}
> **Exclusion statement** — 在表达式中使用赋值运算符（如 `a = b = 4;` 或 `a[i += 5]`）不在 AP CSA 考试范围内。

---

### 1.4.A.3 表达式求值

在程序执行过程中，**表达式被求值以产生一个单一的值**。该值具有一个**类型**，该类型由表达式的求值方式决定。

例如：

- `5 + 3` 求值为 `int` 类型的 `8`
- `5.0 + 3` 求值为 `double` 类型的 `8.0`
- `true && false` 求值为 `boolean` 类型的 `false`

赋值语句中，右侧表达式的值被求出来后，再存入左侧变量。

- ### 例题 1 — 赋值语句追踪

  > Source: AP Classroom Practice Exam 1 MCQ, Q1

  Consider the following code segment.

  ```java
  int x = 20;
  int y = 10;
  int temp = x;
  x = y;
  y = temp * x;
  System.out.println(x + " " + y);
  ```

  What is printed as a result of executing this code segment?

  (A) 10 100  
  (B) 10 200  
  (C) 20 100  
  (D) 20 200

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>
    
  **分析与解答：**

  逐步追踪变量的值：

  | 语句            | x      | y                 | temp |
  | --------------- | ------ | ----------------- | ---- |
  | `int x = 20;`   | 20     | —                 | —    |
  | `int y = 10;`   | 20     | 10                | —    |
  | `int temp = x;` | 20     | 10                | 20   |
  | `x = y;`        | **10** | 10                | 20   |
  | `y = temp * x;` | 10     | **20 × 10 = 200** | 20   |

  最终 `x = 10`，`y = 200`。程序输出 `10 200`。正确答案是 **(B)**。

  本题考察赋值语句的执行顺序：右侧表达式 `temp * x` 先被求值为 `200`，再赋值给 `y`。

  </details>

- ### 例题 2 — 多变量赋值追踪

  > Source: AP Classroom Practice Exam 2 MCQ, Q1

  Consider the following code segment.

  ```java
  int w = 50;
  int x = 20;
  int y = x;
  x = w;
  w = x + y;
  System.out.println(w + " " + x);
  ```

  What is printed as a result of executing the code segment?

  (A) 40 20  
  (B) 70 20  
  (C) 70 50  
  (D) 100 50

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**

      逐步追踪变量的值：

      | 语句          | w                | x      | y      |
      | ------------- | ---------------- | ------ | ------ |
      | `int w = 50;` | 50               | —      | —      |
      | `int x = 20;` | 50               | 20     | —      |
      | `int y = x;`  | 50               | 20     | **20** |
      | `x = w;`      | 50               | **50** | 20     |
      | `w = x + y;`  | **50 + 20 = 70** | 50     | 20     |

      最终 `w = 70`，`x = 50`。程序输出 `70 50`。正确答案是 **(C)**。

      本题的关键点：赋值语句 `y = x;` 将 `x` 的**值**（20）复制给 `y`，之后 `x` 改变不影响 `y`。赋值语句 `x = w;` 将 `w` 的值（50）赋给 `x`，覆盖了 `x` 原来的值。

  </details>

- ### 例题 3 — 变量必须先声明再使用

  > Source: AP Classroom New Unit 1 TopicQuestion MCQ, Q9

  Consider the following code segment.

  ```java
  int x = 5;
  int y = 6;
  /* missing code */
  z = (x + y) / 2;
  ```

  Which of the following can replace `/* missing code */` so that the code segment compiles without error?

  (A) `boolean z = true;`  
   (B) `int z = 0.0;`  
   (C) `int z = 0;`  
   (D) `z = 0;`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**

      变量 `z` 在第四行被使用之前，必须先声明并初始化为一个兼容的数据类型。

      - **(A)** 错误：`z` 被声明为 `boolean`，但 `(x + y) / 2` 的结果是 `int` 类型，不能赋值给 `boolean` 变量。
      - **(B)** 错误：`0.0` 是 `double` 类型，不能赋值给 `int` 变量。
      - **(C)** **正确**：`int z = 0;` 声明了 `int` 类型的变量 `z` 并初始化为 `0`，之后 `z = (x + y) / 2;` 赋值兼容。
      - **(D)** 错误：`z = 0;` 试图使用变量 `z`，但 `z` 尚未声明，会导致编译错误。

      正确答案是 **(C)**。

      本题考察 Essential Knowledge 1.4.A.1：变量在使用前必须被赋值，且该值必须来自兼容的数据类型。

  </details>

- ### 例题 4 — 使用临时变量交换值

  > Source: AP Classroom New Unit 1 TopicQuestion MCQ, Q12

  Consider the following code segment that is intended to swap the values of the `int` variables `x` and `y`.

  ```java
  int temp = x;
  /* missing code */
  ```

  Which of the following can replace `/* missing code */` so that the code segment works as intended?

  (A) `x = y; y = temp;`  
   (B) `y = x; x = temp;`  
   (C) `y = x; temp = y;`  
   (D) `y = x; temp = x;`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**

      交换两个变量的值需要使用一个临时变量来保存其中一个变量的原始值。

      - **Step 1:** `int temp = x;` —— 将 `x` 的原始值存入 `temp`
      - **Step 2:** `x = y;` —— 将 `y` 的值赋给 `x`（此时 `x` 的原始值已丢失，但保存在 `temp` 中）
      - **Step 3:** `y = temp;` —— 将 `temp` 中保存的 `x` 原始值赋给 `y`

      选项 **(A)** 正确实现了这三步。其他选项没有正确保留原始值或顺序错误。

      正确答案是 **(A)**。

      本题考察赋值语句的实际应用——使用临时变量交换两个变量的值，这是编程中的经典算法。

  </details>

- ### 例题 5 — 表达式求值产生单一值

  > Source: AP CSA Course and Exam Description (Sample Exam Questions)

  Consider the following code segment.

  ```java
  int a = 3;
  int b = 4;
  int result = a * b + 2;
  System.out.println(result);
  ```

  What is printed as a result of executing this code segment?

  (A) 9  
   (B) 12  
   (C) 14  
   (D) 18

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**

      赋值语句 `int result = a * b + 2;` 的执行过程：

      1. 先计算右侧表达式 `a * b + 2`：
      - `*` 优先级高于 `+`，先计算 `a * b = 3 * 4 = 12`
      - 再计算 `12 + 2 = 14`
      2. 表达式求值产生一个**单一的值** `14`，类型为 `int`
      3. 将该值赋给变量 `result`

      最终输出 `14`。正确答案是 **(C)**。

      本题考察 Essential Knowledge 1.4.A.3：表达式被求值以产生一个单一的值，该值具有确定的类型。

  </details>

---

## 1.4.B 输入

### 1.4.B.1 输入的概念

程序可以从多种来源获取输入（input），包括触觉、音频、视觉或文本等形式。**Scanner 类**是 Java 中从键盘获取文本输入的一种方式。

Scanner 的基本使用模式：

```java
Scanner sc = new Scanner(System.in);  // 创建 Scanner 对象，连接到键盘输入
int num = sc.nextInt();               // 读取一个整数
double val = sc.nextDouble();         // 读取一个 double 值
String word = sc.next();              // 读取一个单词
String line = sc.nextLine();          // 读取一整行
```

{: .extra}
> **Exclusion statement** — 任何特定形式的用户输入（如键盘输入的具体实现）不在 AP CSA 考试范围内。Scanner 在考试中的正式使用仅限于 Unit 4 中从文件读取数据。

- ### 例题 6 — 程序输入的概念

  > Source: AP CSA Course and Exam Description

  Which of the following best describes the purpose of the `Scanner` class in Java?

  (A) It is used to display output to the console.  
   (B) It is used to obtain text input from an input source such as the keyboard.  
   (C) It is used to perform mathematical calculations.  
   (D) It is used to create random numbers.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

  **分析与解答：**
  - **(A)** 错误：显示输出到控制台使用的是 `System.out.print` 和 `System.out.println`。
  - **(B)** **正确**：`Scanner` 类用于从输入源（如键盘或文件）获取文本输入。
  - **(C)** 错误：Java 有内置的算术运算符进行数学计算。
  - **(D)** 错误：生成随机数使用的是 `Math.random()` 方法。

  正确答案是 **(B)**。

  本题考察 Essential Knowledge 1.4.B.1：`Scanner` 类是从键盘获取文本输入的一种方式。

  </details>

---

## 考点总结

| 考点编号 | 核心内容                                                                | 关联例题     |
| -------- | ----------------------------------------------------------------------- | ------------ |
| 1.4.A.1  | 变量必须先赋值再使用；值必须来自兼容的数据类型；引用类型可赋值为 `null` | 例题 3       |
| 1.4.A.2  | 赋值运算符 `=` 将右侧表达式的值存入左侧变量                             | 例题 1、2、4 |
| 1.4.A.3  | 表达式求值产生一个单一的值，该值具有确定的类型                          | 例题 5       |
| 1.4.B.1  | 输入可以来自多种来源；`Scanner` 类用于获取文本输入                      | 例题 6       |
