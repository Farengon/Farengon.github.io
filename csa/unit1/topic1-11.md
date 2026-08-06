---
layout: default
title: 1.11 Math Class
parent: Unit 1
nav_order: 11
---

# 1.11 — Math Class

## 1.11.A Math 类的常用静态方法

`Math` 类是 Java 标准库中的类，其方法都是 **static 方法**，通过 `Math.方法名()` 调用。AP CSA 考试要求的 Math 类方法：

| 方法                          | 作用                           | 示例                       |
| ----------------------------- | ------------------------------ | -------------------------- |
| `Math.abs(x)`                 | 返回绝对值                     | `Math.abs(-5)` → 5         |
| `Math.pow(a, b)`              | 返回 a 的 b 次幂               | `Math.pow(2, 3)` → 8.0     |
| `Math.sqrt(x)`                | 返回平方根                     | `Math.sqrt(9)` → 3.0       |
| `Math.random()`               | 返回 [0, 1) 的随机 double 值   | 每次调用结果不同           |

{: .note}
> `Math.random()` 返回大于等于 0、小于 1 的 double 值，常用于生成随机整数。

## 1.11.B 用 Math.random() 生成随机整数

**生成 [0, n) 的随机整数：** `(int) (Math.random() * n)`

**生成 [min, max] 的随机整数（含端点）：** `(int) (Math.random() * (max - min + 1)) + min`

{: .important}
> 一定要用圆括号把 `Math.random() * n` 括起来再强制转换。`(int) Math.random() * n` 会先转换再乘法，结果恒为 0！因为 `Math.random()` 在 [0,1) 之间，转成 int 后是 0。

- ### 例题 1 — Math.random 括号问题

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q4

  Consider the following statement, which is intended to generate an integer between 1 and 10, inclusive, and assign it to result. This statement does not work as intended.

  ```java
  int result = (int) Math.random() * 10 + 1;
  ```

  Which of the following changes can be made so that this statement works as intended?

  (A) `int result = (int) Math.random() * (10 + 1);`  
  (B) `int result = (int)(Math.random() * 10) + 1;`  
  (C) `int result = (int) Math.random() * 9 + 1;`  
  (D) `int result = Math.random() * 10 + 1;`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    原语句中 `(int) Math.random()` 先把 [0,1) 转成 int（恒为 0），再乘 10 加 1，结果恒为 1。选项 (B) 先用圆括号保证 `Math.random() * 10` 先算，得到 [0,10)，转 int 后得到 [0,9]，再加 1 得到 [1,10]。正确答案是 **(B)**。

  </details>

- ### 例题 2 — Math.abs 的参数要求

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q5

  Consider the following code segment.

  ```java
  double result = Math.abs(x);
  ```

  Which of the following statements about the variable x is true?

  (A) x may hold any numerical value.  
  (B) x must be equal to 0.  
  (C) x must have a value greater than 0.  
  (D) x must have a value less than 0.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `Math.abs(x)` 返回 x 的绝对值，任何 int 或 double 数值都可以作为参数。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 随机数的取值范围

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q6

  Consider the following code segment.

  ```java
  int num = (int)(Math.random() * 6);
  System.out.println(num);
  ```

  Which of the following cannot be printed as a result of executing this code segment?

  (A) 0  
  (B) 2  
  (C) 4  
  (D) 6

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `Math.random() * 6` 得到 [0, 6)，转成 int 后得到 {0, 1, 2, 3, 4, 5}。6 不在范围内，因此无法打印 6。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 生成 [1, 25] 的随机整数

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q24

  Which of the following statements assigns a random integer between 1 and 25 inclusive, to rand?

  (A) `int rand = (int) (Math.random()) * 25 + 1;`  
  (B) `int rand = (int) (Math.random() * 25);`  
  (C) `int rand = (int) (Math.random() * 25) + 1;`  
  (D) `int rand = (int) (Math.random() + 1) * 25;`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `Math.random() * 25` 得到 [0, 25)，转 int 得 [0, 24]，加 1 得 [1, 25]。选项 (C) 正确。选项 (A) 中括号位置错误（先转 int 再乘，恒为 0）；(B) 得到 [0, 24]；(D) 中 `(int)(Math.random()+1)` 恒为 1，乘 25 恒为 25。正确答案是 **(C)**。

  </details>

- ### 例题 5 — 生成 [min, max] 的随机整数

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q25

  Consider the following code segment, which is intended to assign to `num` a random integer value between `min` and `max`, inclusive, each with an equal chance of being assigned to `num`. Assume that `min` and `max` are integer variables and that the value of `max` is greater than the value of `min`.

  ```java
  double rn = Math.random();
  int num = /* missing code */;
  ```

  Which of the following can replace `/* missing code */` so that the code segment works as intended?

  (A) `(int) (rn * max) + min`  
  (B) `(int) (rn * (max - min)) + min`  
  (C) `(int) (rn * (max - min)) + 1`  
  (D) `(int) (rn * (max - min + 1)) + min`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `max - min + 1` 是取值范围内数值的个数。`rn * (max - min + 1)` 得到 [0, max-min+1)，转 int 得 [0, max-min]，再加 min 得 [min, max]。正确答案是 **(D)**。

  </details>

- ### 例题 6 — Math.pow 与 Math.sqrt 组合

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q19

  Consider the following statement, which is intended to assign the value of the expression √((x+y)²/|a−b|) to the variable result. Assume that the double variables x, y, a, and b have been properly declared and initialized.

  ```java
  double result = /* missing code */;
  ```

  Which of the following can replace `/* missing code */` so that the statement works as intended?

  (A) `Math.sqrt((x + y) * 2 / Math.abs(a, b))`  
  (B) `Math.sqrt((x + y) * (x + y) / Math.abs(a - b))`  
  (C) `Math.sqrt(Math.pow(x + y, 2) / Math.abs(a, b))`  
  (D) `Math.sqrt(Math.pow(x + y, 2) / Math.abs(a - b))`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `Math.pow(x + y, 2)` 计算 (x+y)²；`Math.abs(a - b)` 计算 |a−b|（`Math.abs` 只接受一个参数，`Math.abs(a, b)` 是错的）；`Math.sqrt(...)` 开平方。选项 (D) 完全正确。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                             | 考试提示                                               |
| ---------------- | ---------------------------------------------------- | ------------------------------------------------------ |
| Math 类方法      | `abs`、`pow`、`sqrt`、`random` 均为 static 方法      | 通过 `Math.方法名()` 调用                              |
| 随机整数 [0,n)   | `(int)(Math.random() * n)`                           | 括号不能漏，否则恒为 0                                 |
| 随机整数 [min,max] | `(int)(Math.random() * (max - min + 1)) + min`     | 注意 `+1` 的位置                                       |
| Math.abs 参数    | 只接受一个参数，返回绝对值                           | 任意数值均可                                           |
| Math.pow 参数    | 两个参数，返回 double                                | `Math.pow(x, 2)` 是平方                                |
