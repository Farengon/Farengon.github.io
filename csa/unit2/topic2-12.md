---
layout: default
title: 2.12 Informal Run-Time Analysis
parent: Unit 2
nav_order: 12
---

# 2.12 — Informal Run-Time Analysis

## 2.12.A 非正式运行时间分析

**非正式运行时间分析（Informal Run-Time Analysis）** 关注程序（尤其是循环）执行的**次数**，从而估计运行时间随输入规模增长的方式。

{: .note}
> AP CSA 不要求正式的复杂度记号（如大 O），但要求能够：
> - 数出某个语句在循环中执行的次数；
> - 根据循环结构与输入规模描述运行时间的变化；
> - 区分**线性**（与 n 成正比）、**平方**（与 n² 成正比，如嵌套循环）等增长方式。

## 2.12.B 判断执行次数

- **单层循环**：次数 = 循环迭代次数（由初始值、步长、终止条件决定）。
- **嵌套循环**：次数 = 各层迭代次数的乘积（或逐层求和）。
- 循环体内的条件（if）可能使语句**并非每轮都执行**，需要结合条件分析。

- ### 例题 1 — 嵌套循环的迭代条件

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q17

  Consider the following code segment, in which `m` and `n` are properly declared and initialized `int` variables.

  ```java
  int result = 0;
  for (int i = 0; i < n; i++)
  {
      for (int j = m; j < n; j++)
      {
          result++;
      }
  }
  ```

  Which of the following best describes the conditions that must be true of `m` and `n` so that after this code segment executes, the value of `result` is greater than 0?

  (A) `n > 0 and m > 0`  
  (B) `n > 0 and m > n`  
  (C) `n > 0 and n > m`  
  (D) `m > 0 and m > n`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `result++` 要执行，外层循环需执行（`n > 0`），内层循环也需执行（`m < n`，即 `n > m`）。注意外层执行 n 次，内层每次执行 n - m 次，result 最终为 n × (n - m)，要求 n > 0 且 n > m。正确答案是 **(C)**。

  </details>

- ### 例题 2 — Math.random 调用次数

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q19

  Consider the following code segment.

  ```java
  double sum = 0.0;
  for (int outer = 1; outer <= 4; outer++)
  {
      for (int inner = 0; inner <= 4; inner++)
      {
          sum += Math.random();
      }
  }
  ```

  How many times will Math.random() be called as a result of executing this code segment?

  (A) 5  
  (B) 9  
  (C) 16  
  (D) 20

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层 4 次、内层 5 次，`Math.random()` 的调用次数为固定常量 4 × 5 = 20（与输入规模无关）。正确答案是 **(D)**。

  </details>

- ### 例题 3 — doSomething 调用次数

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q20

  The following code segment appears in a method in the same class as the method doSomething().

  ```java
  int i = 1;
  while (i < 3)
  {
      for (int j = 1; j <= 5; j++)
      {
          doSomething();
      }
      i++;
  }
  ```

  How many times will doSomething() be called as a result of executing this code segment?

  (A) 5  
  (B) 8  
  (C) 10  
  (D) 15

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层 while 执行 2 次（i = 1, 2），内层 for 每次执行 5 次。调用次数 = 2 × 5 = 10。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 内层循环迭代次数

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q21

  Consider the following code segment.

  ```java
  for (int x = 1; x <= 3; x++)
  {
      for (int y = 5; y > 1; y--)
      {
          System.out.print("*");
      }
  }
  ```

  Which of the following best describes the behavior of this code segment?

  (A) The print statement is executed 7 times because the outer loop iterates 3 times and the inner loop iterates 4 times.  
  (B) The print statement is executed 8 times because the outer loop iterates 3 times and the inner loop iterates 5 times.  
  (C) The print statement is executed 12 times because the outer loop iterates 3 times and the inner loop iterates 4 times for each iteration of the outer loop.  
  (D) The print statement is executed 15 times because the outer loop iterates 3 times and the inner loop iterates 5 times for each iteration of the outer loop.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层 3 次，内层 y 从 5 到 2 共 4 次，打印语句执行 3 × 4 = 12 次。选项 (C) 正确描述了行为。正确答案是 **(C)**。

  </details>

- ### 例题 5 — 内层依赖外层的迭代

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q15

  Consider the following code segment.

  ```java
  int counter = 0;
  for (int x = 10; x > 0; x--)
  {
      for (int y = x; y <= x; y++)
      {
          counter++;   // Line 6
      }
  }
  ```

  How many times will the statement in line 6 be executed as a result of running the code segment?

  (A) 1  
  (B) 10  
  (C) 11  
  (D) 20

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    内层循环条件 `y = x` 且 `y <= x`，每轮只执行 1 次。外层 10 次，line 6 共执行 10 × 1 = 10 次。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                     |
| ------------------ | -------------------------------------------- | -------------------------------------------- |
| 执行次数统计       | 单层 = 迭代次数；嵌套 = 乘积或求和           | 数清每层循环的迭代次数                       |
| 增长方式           | 单层 ≈ 线性；嵌套 ≈ 平方                     | 随输入规模增大，嵌套循环运行时间增长更快     |
| 固定次数           | 与输入无关的常量次数（如 4×5=20）            | 不要误以为与输入规模相关                     |
| 条件影响           | 循环体内 if 使语句不总是执行                 | 结合条件逐轮判断                             |
