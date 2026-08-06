---
layout: default
title: 2.7 while Loops
parent: Unit 2
nav_order: 7
---

# 2.7 — while Loops

## 2.7.A while 循环的基本结构

**while 循环**在条件为 true 时反复执行循环体：

{% raw %}
```java
while (条件) {
    // 循环体
}
```
{% endraw %}

{: .important}
> - 进入循环前先判断条件；条件为 false 时循环体**一次也不执行**。
> - 循环体必须让条件**趋向于 false**（如更新计数器），否则会**无限循环（infinite loop）**。
> - 循环体执行顺序：**判断条件 → 执行循环体 → 再判断条件**，直到条件为 false。
> - **差一错误（off-by-one error）**：循环**多执行一次或少执行一次**导致的错误。例如用 `<=` 代替 `<`，或初始值设错。检查循环边界是避免差一错误的关键。

## 2.7.B while 循环的常见模式

- **计数循环**：`count++` 每轮 +1，用于统计次数。
- **累加循环**：`sum += x` 累积求和。
- **数字分解**：`temp % 10` 取末位、`temp /= 10` 去掉末位。

- ### 例题 1 — 打印偶数

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q1

  Which of the following code segments can be used to print only the even integers between 2 and 10, inclusive?

  (A)
{% raw %}
  ```java
  int num = 0;
  while (num < 10)
  {
      System.out.println(num);
      num += 2;
  }
  ```
{% endraw %}
  (B)
{% raw %}
  ```java
  int num = 0;
  while (num <= 10)
  {
      System.out.println(num);
      num += 2;
  }
  ```
{% endraw %}
  (C)
{% raw %}
  ```java
  int num = 0;
  while (num < 10)
  {
      num += 2;
      System.out.println(num);
  }
  ```
{% endraw %}
  (D)
{% raw %}
  ```java
  int num = 0;
  while (num <= 10)
  {
      num += 2;
      System.out.println(num);
  }
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (C)：num 从 0 开始，先 `num += 2` 再打印，打印 2、4、6、8、10。当 num 从 8 变到 10 后打印 10，下一轮条件 `10 < 10` 为 false 退出，正好输出 2 到 10 的所有偶数。选项 (A)(B) 会打印 0；(D) 会打印 12。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 奇偶判断

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q2

  In the following code segment, x is an int variable with a positive value.

{% raw %}
  ```java
  int temp = x;
  while (temp > 0)
  {
      temp -= 2;
  }
  System.out.println(temp == 0);
  ```
{% endraw %}

  Which of the following best describes the behavior of the code segment?

  (A) It prints 0 if x is even and prints -1 otherwise.  
  (B) It prints -1 if x is even and prints 0 otherwise.  
  (C) It prints true if x is even and prints false otherwise.  
  (D) It prints false if x is even and prints true otherwise.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    temp 不断减 2，直到不再大于 0。若 x 是偶数，temp 最终为 0；若 x 是奇数，temp 最终为 -1。`temp == 0` 在 x 为偶数时为 true。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 无限循环（负数输入）

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q3

  Consider the following code segment. Assume that the int variable input has been properly declared and initialized.

{% raw %}
  ```java
  int answer = 1;
  if (input != 0)
  {
      int count = 1;
      while (count != input)
      {
          count++;
          answer *= count;
      }
  }
  System.out.println(answer);
  ```
{% endraw %}

  Which of the following best describes the condition in which this code segment always results in integer overflow?

  (A) When input == 0  
  (B) When input == 1  
  (C) When input > 0  
  (D) When input < 0

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    count 从 1 开始**递增**，永远不可能等于一个负数（input < 0）。循环条件 `count != input` 恒为 true，循环永不终止，count 最终溢出。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 字符串拼接追踪

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q4

  Consider the following code segment.

{% raw %}
  ```java
  int a = 1;
  String result = "";
  while (a < 20)
  {
      result += a;
      a += 5;
  }
  System.out.println(result);
  ```
{% endraw %}

  What is printed as a result of executing this code segment?

  (A) `21`  
  (B) `161116`  
  (C) `161161`  
  (D) `16111621`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环过程：a=1 拼接 "1"，a 变 6；a=6 拼接 "6"，a 变 11；a=11 拼接 "11"，a 变 16；a=16 拼接 "16"，a 变 21，条件 `21 < 20` 为 false 退出。result = "161116"。正确答案是 **(B)**。

  </details>

- ### 例题 5 — 统计 2 和 3 的公倍数

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q9

  Consider the following code segment.

{% raw %}
  ```java
  int num = 1;
  int count = 0;
  while (num <= 10)
  {
      if (num % 2 == 0 && num % 3 == 0)
      {
          count++;
      }
      num++;
  }
  ```
{% endraw %}

  What value is stored in the variable count as a result of executing the code segment?

  (A) 1  
  (B) 3  
  (C) 5  
  (D) 7

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环遍历 1 到 10，统计同时能被 2 和 3 整除的数（即 6 的倍数）。1 到 10 中只有 6 一个，count = 1。正确答案是 **(A)**。

  </details>

- ### 例题 6 — 循环中变量倍增

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q11

  Consider the following code segment.

  ```java
  int count = 5;
  while (count < 100)
      count = count * 2;
  count = count + 1;
  ```

  What is the value of count after executing the code segment?

  (A) 100  
  (B) 101  
  (C) 160  
  (D) 161

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    count 依次为 10、20、40、80、160。当 count 变为 160（第一个 ≥ 100 的值）时循环条件 `160 < 100` 为 false，循环退出。最后 `count = 160 + 1 = 161`。正确答案是 **(D)**。

  </details>

- ### 例题 7 — 数字位数统计

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q22

  The following code segment is intended to print the number of digits in the int variable num, where `num > 0`.

{% raw %}
  ```java
  int count = 0;
  while ( /* missing condition */ )
  {
      count++;
      num = num / 10;
  }
  System.out.println(count);
  ```
{% endraw %}

  Which of the following can be used to replace `/* missing condition */` so that the code segment works as intended?

  (A) `count != 0`  
  (B) `count > 0`  
  (C) `num >= 0`  
  (D) `num != 0`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    num 每次除以 10 就少一位，count 相应 +1。当 num 变成 0 时所有位已数完，循环应终止，所以条件是 `num != 0`。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                   |
| ---------------- | -------------------------------------------- | ------------------------------------------ |
| while 结构       | 先判断后执行                                 | 条件为 false 时循环体一次也不执行          |
| 无限循环         | 条件永不趋 false                             | count 递增不可能等于负数 → 死循环          |
| 差一错误         | 多执行或少执行一次                           | 检查 `<` vs `<=`、初始值与终止值           |
| 循环追踪         | 记录每轮循环的变量值                         | 注意 ++ 与 += 的位置（先加后打印 vs 先打印后加）|
| 数字处理模式     | `% 10` 取末位、`/ 10` 去末位                 | 统计位数：条件 `num != 0`                  |
| 统计计数         | 满足条件时 count++                           | 与 6 的倍数判断：`%2==0 && %3==0`          |
