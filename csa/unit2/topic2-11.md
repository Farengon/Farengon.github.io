---
layout: default
title: 2.11 Nested Iteration
parent: Unit 2
nav_order: 11
---

# 2.11 — Nested Iteration

## 2.11.A 嵌套循环（Nested Loops）

**嵌套循环**是循环体内再包含循环。外层循环每执行一次，内层循环完整执行一轮：

{% raw %}
```java
for (int outer = 0; outer < 3; outer++) {
    for (int inner = 0; inner < 4; inner++) {
        System.out.print("*");   // 共执行 3 × 4 = 12 次
    }
    System.out.println();
}
```
{% endraw %}

{: .important}
> - 内层循环体执行的总次数 = **外层迭代次数 × 内层迭代次数**。
> - 内层循环的初始值和条件可以**依赖外层循环变量**（如 `inner = outer`），这样每轮内层迭代次数不同。
> - 追踪嵌套循环时，可以按外层变量的每个取值，逐轮列出内层变量的取值序列。

## 2.11.B 嵌套循环的常见题型

- 计算打印语句执行的次数（乘法原理）。
- 判断内层循环头应如何设置才能输出特定图案。
- 追踪嵌套循环中计数器的最终值。

- ### 例题 1 — 修正嵌套循环输出

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q16

  Consider the following code segment.

{% raw %}
  ```java
  for (int j = 1; j <= 4; j++)          // Line 1
  {
      for (int k = j + 1; k >= 1; k--)  // Line 3
      {
          System.out.print(j + "");     // Line 5
      }
      System.out.println();
  }
  ```
{% endraw %}

  The code segment is intended to produce the following output, but does not work as intended.

  ```
  1
  22
  333
  4444
  ```

  Which of the following changes can be made so that the code segment works as intended?

  (A) Changing line 1 to `for (int j = 1; j < 4; j++)`  
  (B) Changing line 3 to `for (int k = 1; k <= j + 1; k++)`  
  (C) Changing line 3 to `for (int k = j; k >= 1; k--)`  
  (D) Changing line 5 to `System.out.print(k + " ");`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    原代码内层从 `k = j + 1` 到 `k = 1`，每轮内层多执行 1 次（输出 2、3、4、5 个）。改成 `k = j` 后：j=1 时内层 1 次、j=2 时 2 次、j=3 时 3 次、j=4 时 4 次，输出 1、22、333、4444。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 嵌套循环执行条件

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q17

  Consider the following code segment, in which `m` and `n` are properly declared and initialized `int` variables.

{% raw %}
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
{% endraw %}

  Which of the following best describes the conditions that must be true of `m` and `n` so that after this code segment executes, the value of `result` is greater than 0?

  (A) `n > 0 and m > 0`  
  (B) `n > 0 and m > n`  
  (C) `n > 0 and n > m`  
  (D) `m > 0 and m > n`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层循环要执行，必须 `n > 0`（i 从 0 到 n-1）。内层循环要执行，必须 `m < n`（j 从 m 到 n-1），即 `n > m`。两者都满足时 result 才 > 0。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 嵌套循环输出星号

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q18

  Consider the following code segment.

{% raw %}
  ```java
  int a = 1;
  while (a <= 2)
  {
      int c = 1;
      while (/* missing condition */)
      {
          System.out.print("*");
          c++;
      }
      a++;
  }
  ```
{% endraw %}

  The code segment is intended to print `"******"`.

  Which of the following can be used to replace `/* missing condition */` so that the code segment works as intended?

  (A) `c > 2`  
  (B) `c < 3`  
  (C) `c <= 3`  
  (D) `c >= 3`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层循环执行 2 次（a = 1, 2）。要打印 6 个星号，内层每轮需执行 3 次。c 从 1 开始，`c <= 3` 时执行：c=1, 2, 3 共 3 次。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 调用次数计算

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q19

  Consider the following code segment.

{% raw %}
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
{% endraw %}

  How many times will Math.random() be called as a result of executing this code segment?

  (A) 5  
  (B) 9  
  (C) 16  
  (D) 20

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层循环 4 次（outer = 1, 2, 3, 4），内层循环 5 次（inner = 0, 1, 2, 3, 4）。调用次数 = 4 × 5 = 20。正确答案是 **(D)**。

  </details>

- ### 例题 5 — 方法调用次数

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q20

  The following code segment appears in a method in the same class as the method doSomething().

{% raw %}
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
{% endraw %}

  How many times will doSomething() be called as a result of executing this code segment?

  (A) 5  
  (B) 8  
  (C) 10  
  (D) 15

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层 while 循环 2 次（i = 1, 2），内层 for 循环 5 次。调用次数 = 2 × 5 = 10。正确答案是 **(C)**。

  </details>

- ### 例题 6 — 星号数量

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q21

  Consider the following code segment.

{% raw %}
  ```java
  for (int x = 1; x <= 3; x++)
  {
      for (int y = 5; y > 1; y--)
      {
          System.out.print("*");
      }
  }
  ```
{% endraw %}

  Which of the following best describes the behavior of this code segment?

  (A) The print statement is executed 7 times because the outer loop iterates 3 times and the inner loop iterates 4 times.  
  (B) The print statement is executed 8 times because the outer loop iterates 3 times and the inner loop iterates 5 times.  
  (C) The print statement is executed 12 times because the outer loop iterates 3 times and the inner loop iterates 4 times for each iteration of the outer loop.  
  (D) The print statement is executed 15 times because the outer loop iterates 3 times and the inner loop iterates 5 times for each iteration of the outer loop.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层循环 3 次（x = 1, 2, 3）。内层 y 从 5 递减到 2（y > 1），共 4 次。打印次数 = 3 × 4 = 12。正确答案是 **(C)**。

  </details>

- ### 例题 7 — 内层依赖外层

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q14

  Consider the following code segment.

{% raw %}
  ```java
  for (int outer = 0; outer < 3; outer++)
  {
      for (/* missing loop header */)
      {
          System.out.print(outer + "" + inner + "-");
      }
  }
  ```
{% endraw %}

  Which of the following can be used as a replacement for `/* missing loop header */` so that the code segment produces the output `00-01-02-11-12-22-`?

  (A) `int inner = 0; inner < 3; inner++`  
  (B) `int inner = 1; inner < 3; inner++`  
  (C) `int inner = outer - 1; inner < 3; inner++`  
  (D) `int inner = outer; inner < 3; inner++`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    期望输出：outer=0 时 inner 取 0,1,2；outer=1 时 inner 取 1,2；outer=2 时 inner 取 2。这正是 `inner = outer; inner < 3` 的效果。选项 (D) 正确。正确答案是 **(D)**。

  </details>

- ### 例题 8 — 内层循环次数

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q15

  Consider the following code segment.

{% raw %}
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
{% endraw %}

  How many times will the statement in line 6 be executed as a result of running the code segment?

  (A) 1  
  (B) 10  
  (C) 11  
  (D) 20

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    内层循环初始条件 `y = x`，条件 `y <= x` 立即满足，内层每轮只执行 **1 次**。外层循环执行 10 次（x = 10 到 1），所以 line 6 执行 10 次。正确答案是 **(B)**。

  </details>

- ### 例题 9 — 打印 6

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q18

  Consider the following code segment.

{% raw %}
  ```java
  int count = 0;
  for (int x = 1; x <= 3; x++)
  {
      /* missing loop header */
      {
          count++;
      }
  }
  System.out.println(count);
  ```
{% endraw %}

  Which of the following can be used to replace `/* missing loop header */` so that the code segment prints 6?

  (A) `for (int y = 0; y <= 2; y++)`  
  (B) `for (int y = 0; y < 3; y++)`  
  (C) `for (int y = 3; y <= x; y++)`  
  (D) `for (int y = 0; y < x; y++)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (D)：x=1 时内层 1 次，x=2 时内层 2 次，x=3 时内层 3 次，总 1+2+3=6 次。选项 (A)(B) 每轮 3 次共 9 次；(C) 只有 x=3 时 y=3 ≤ 3 成立，共 1 次。正确答案是 **(D)**。

  </details>

- ### 例题 10 — 输出 0123 三行

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q20

  Consider the following code segment.

{% raw %}
  ```java
  /* missing loop header */
  {
      for (int k = 0; k < 4; k++)
      {
          System.out.print(k);
      }
      System.out.println();
  }
  ```
{% endraw %}

  This code segment is intended to produce the following output.

  ```
  0123
  0123
  0123
  ```

  Which of the following can be used to replace `/* missing loop header */` so that the code segment works as intended?

  (A) `for (int j = 0; j < 2; j++)`  
  (B) `for (int j = 1; j <= 2; j++)`  
  (C) `for (int j = 0; j <= 6; j += 2)`  
  (D) `for (int j = 1; j < 6; j += 2)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    需要外层循环恰好执行 3 次。选项 (D)：j = 1, 3, 5 共 3 次。选项 (A)(B) 执行 2 次；(C) 执行 4 次（0, 2, 4, 6）。正确答案是 **(D)**。

  </details>

- ### 例题 11 — 乘法原理

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q29

  In the following code segment, outerMax and innerMax are properly declared and initialized int variables that are greater than or equal to zero.

{% raw %}
  ```java
  for (int outer = 0; outer < outerMax; outer++)
  {
      for (int inner = 0; inner < innerMax; inner++)
      {
          System.out.println("*");
      }
  }
  ```
{% endraw %}

  Which of the following best describes the behavior of the code segment?

  (A) It prints "*" a total of outerMax + innerMax times.  
  (B) It prints "*" a total of outerMax × innerMax times.  
  (C) It prints "*" a total of (outerMax + 1) + (innerMax + 1) times.  
  (D) It prints "*" a total of (outerMax + 1) × (innerMax + 1) times.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层循环执行 outerMax 次，内层循环每次执行 innerMax 次。总次数 = outerMax × innerMax。正确答案是 **(B)**。

  </details>

- ### 例题 12 — 嵌套循环执行次数

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q19

  Consider the following code segment.

{% raw %}
  ```java
  int val = 1;
  while (val <= 6)
  {
      for (int k = 0; k <= 2; k++)
      {
          System.out.println("Surprise!");   // Line 6
      }
      val++;
  }
  ```
{% endraw %}

  How many times will the statement in line 6 be executed as a result of running the code segment?

  (A) 3  
  (B) 12  
  (C) 15  
  (D) 18

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层 while 循环 6 次（val = 1 到 6），内层 for 循环 3 次（k = 0, 1, 2）。总次数 = 6 × 3 = 18。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 嵌套循环次数       | 外层次数 × 内层次数                          | 内层条件依赖外层时逐轮计算                     |
| 内层依赖外层       | `inner = outer` 使内层次数递减               | 00-01-02 / 11-12 / 22 型输出                   |
| 循环执行条件       | 内层要执行需 `m < n`                         | 先保证外层 n > 0                               |
| 特殊内层           | `y = x; y <= x` 每轮只执行 1 次              | 别想当然地认为是全遍历                         |
| 图案/计数问题      | 逐轮列出取值，或直接相乘                     | 乘法原理 + 边界检查                            |
