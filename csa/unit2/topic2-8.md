---
layout: default
title: 2.8 for Loops
parent: Unit 2
nav_order: 8
---

# 2.8 — for Loops

## 2.8.A for 循环的基本结构

**for 循环**把循环变量的**初始化、条件、更新**集中在一行：

```java
for (初始化; 条件; 更新) {
    // 循环体
}
```

例如：`for (int j = 1; j <= 5; j++)` 让 j 依次取 1、2、3、4、5。

{: .important}
> - 循环执行顺序：**初始化（仅一次）→ 判断条件 → 执行循环体 → 更新 → 再判断**。
> - 更新表达式（如 `j += 2`）改变循环变量的方式决定了循环的取值序列。
> - 条件若永不成立或永为 true，会导致循环体不执行或**无限循环**。

## 2.8.B for 与 while 的等价转换

```java
// for 循环
for (int i = 0; i < 10; i++) { ... }

// 等价 while 循环
int i = 0;
while (i < 10) {
    ...
    i++;   // 更新语句的位置与循环体内操作顺序相关
}
```

- ### 例题 1 — 无限循环的条件

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q5

  Consider the following code segment.

  ```java
  int sum = 0;
  for (int j = 1; /* missing condition */; j += 2)
  {
      sum += j;
  }
  ```

  Which of the following replacements for `/* missing condition */` will cause an infinite loop?

  (A) `j == 100`  
  (B) `j != 100`  
  (C) `j <= 100`  
  (D) `j >= 100`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    j 从 1 开始每次 +2：1, 3, 5, ..., 99, 101, ...。j 永远**不会等于 100**（只取奇数），所以条件 `j != 100` 恒为 true，造成无限循环。正确答案是 **(B)**。

  </details>

- ### 例题 2 — for 与 while 的输出一致性

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q6

  Consider the following two code segments, which are intended to produce identical outputs.

  **Code Segment 1**

  ```java
  for (int i = 0; i < 10; i++)
  {
      System.out.println("counting " + i);
  }
  ```

  **Code Segment 2**

  ```java
  int x = 0;
  while (x < 10)
  {
      x = x + 1;
      System.out.println("counting " + x);
  }
  ```

  Which of the following changes can be made to Code Segment 2 so that the outputs of the two code segments are identical as intended?

  (A) Move the statement `x = x + 1;` so that it follows the print statement inside the loop body.  
  (B) Rename the variable x to be i so that it is the same variable name as in Code Segment 1.  
  (C) Remove the statement `x = x + 1;` because this statement is not in the loop body in Code Segment 1.  
  (D) Change the statement `x = x + 1;` to be `x++;` so that the increment of the loop control variable is the same in both code segments.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    for 循环先打印 i 再更新（i++ 在循环体之后）。Code Segment 2 中 `x = x + 1` 在打印之前执行，导致输出 1~10 而非 0~9。把 `x = x + 1;` 移到循环体的最后（打印语句之后），与 for 循环的更新时机一致。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 带条件的循环追踪

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q7

  Consider the following code segment.

  ```java
  for (int m = 16; m > 0; m -= 2)
  {
      if ((m % 3) == 1)
      {
          System.out.print(m + " ");
      }
  }
  ```

  What is printed as a result of executing this code segment?

  (A) `15 12 9 6 3`  
  (B) `12 6 0`  
  (C) `16 14 12 10 8 6 4 2`  
  (D) `16 10 4`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    m 依次取 16, 14, 12, 10, 8, 6, 4, 2。满足 `m % 3 == 1` 的：16 % 3 = 1 ✓，14 % 3 = 2 ✗，12 % 3 = 0 ✗，10 % 3 = 1 ✓，8 % 3 = 2 ✗，6 % 3 = 0 ✗，4 % 3 = 1 ✓，2 % 3 = 2 ✗。输出 "16 10 4"。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 奇偶判断的条件

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q8

  In the following code segment, num has been assigned a positive int value. The following code segment is intended to print true if num is even and is intended to print false otherwise.

  ```java
  boolean isEven = true;
  if (/* missing code */)
  {
      isEven = false;
  }
  System.out.println(isEven);
  ```

  Which of the following can replace `/* missing code */` so that this code segment works as intended?

  (A) `num / 2 == 0`  
  (B) `num / 2 != 0`  
  (C) `num % 2 == 0`  
  (D) `num % 2 != 0`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    isEven 初始为 true，当 num 是**奇数**时应变为 false。判断奇数用 `num % 2 != 0`（余数不为 0）。正确答案是 **(D)**。

  </details>

- ### 例题 5 — 正序与倒序输出

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q10

  Consider the following two code segments. Code segment 2 is a revision of code segment 1 in which the loop header has been changed.

  **Code Segment 1**

  ```java
  for (int k = 1; k <= 5; k++)
  {
      System.out.print(k);
  }
  ```

  **Code Segment 2**

  ```java
  for (int k = 5; k >= 1; k--)
  {
      System.out.print(k);
  }
  ```

  Which of the following best explains the difference, if any, between the output of code segment 1 and code segment 2?

  (A) Both code segments produce the same output, because they both iterate four times.  
  (B) Both code segments produce the same output, because they both iterate five times.  
  (C) Code segment 1 prints more values than code segment 2 does, because it iterates for one additional value of k.  
  (D) The code segments print the same values but in a different order, because code segment 1 iterates from 1 to 5 and code segment 2 iterates from 5 to 1.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    代码段 1 输出 12345，代码段 2 输出 54321。两者迭代 5 次、取值相同，但顺序相反。正确答案是 **(D)**。

  </details>

- ### 例题 6 — for 转 while

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q13

  Consider the following code segment.

  ```java
  for (int j = 1; j < 10; j += 2)
  {
      System.out.print(j);
  }
  ```

  Which of the following code segments will produce the same output as the given code segment?

  (A)
  ```java
  int j = 1;
  while (j < 10)
  {
      j += 2;
      System.out.print(j);
  }
  ```
  (B)
  ```java
  int j = 1;
  while (j < 10)
  {
      System.out.print(j);
      j += 2;
  }
  ```
  (C)
  ```java
  int j = 1;
  while (j <= 10)
  {
      j += 2;
      System.out.print(j);
  }
  ```
  (D)
  ```java
  int j = 1;
  while (j >= 10)
  {
      j += 2;
      System.out.print(j);
  }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    原 for 循环打印 j 后再更新，输出 13579。选项 (B) 的 while 循环先打印再 `j += 2`，同样输出 13579。选项 (A)(C) 先更新后打印，输出 3579；(D) 条件 `j >= 10` 一开始就为 false。正确答案是 **(B)**。

  </details>

- ### 例题 7 — 奇数求和

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q26

  Consider the following code segment.

  ```java
  int sum = 0;
  for (int k = 1; k <= 30; k = k + 2)
      sum += k;
  System.out.println(sum);
  ```

  Which of the following best describes the output of the code segment?

  (A) The segment will print the sum of only the even integers from 1 through 30, inclusive, because it starts sum at 0, increments k by 2, and terminates when k exceeds 30.  
  (B) The segment will print the sum of only the odd integers from 1 through 30, inclusive, because it starts k at 1, increments k by 2, and terminates when k exceeds 30.  
  (C) The segment will print the sum of only the even integers from 1 through 60, inclusive, because it starts sum at 0, increments k by 2, and iterates 30 times.  
  (D) The segment will print the sum of only the odd integers from 1 through 60, inclusive, because it starts k at 1, increments k by 2, and iterates 30 times.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    k 从 1 开始每次 +2，取值为 1, 3, 5, ..., 29（都是奇数），条件 `k <= 30` 在 k 超过 30 时终止。求的是 1 到 30 范围内奇数的和。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| for 结构         | `for (初始化; 条件; 更新)`                   | 初始化只执行一次                               |
| 执行顺序         | 初始化 → 判断 → 循环体 → 更新 → 再判断      | 打印与更新的先后影响输出                       |
| 无限循环         | 更新跳过条件值（如 j+=2 跳过 100）           | j != 100 恒真 → 死循环                         |
| for ↔ while 转换 | 更新语句放在循环体末尾                       | 与 for 的更新时机保持一致                      |
| 取值序列         | 初始值、步长、终止条件决定序列               | m -= 2、k += 2 等步长                      |
