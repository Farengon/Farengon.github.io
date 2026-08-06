---
layout: default
title: 2.9 Implementing Selection and Iteration Algorithms
parent: Unit 2
nav_order: 9
---

# 2.9 — Implementing Selection and Iteration Algorithms

## 2.9.A 组合使用选择与循环

许多经典算法需要把**选择（if）**和**循环（while/for）**组合起来：

- **数字分解**：循环中用 `% 10` 和 `/ 10` 逐个处理数字的每一位。
- **求和/求均值**：循环累加，循环结束后计算。
- **找最大/最小**：循环中逐个比较并记录。

{: .note}
> 处理数字问题的常用技巧：
> - `num % 10`：取出最右边的数字。
> - `num / 10`：去掉最右边的数字（整数除法）。
> - 循环条件常为 `temp > 0` 或 `temp != 0`，配合更新语句使循环终止。

## 2.9.B 常见算法模式

| 模式         | 关键步骤                                             |
| ------------ | ---------------------------------------------------- |
| 数字逆序输出 | 循环取末位打印，再 `/ 10`                           |
| 数位求和     | 循环 `sum += temp % 10; temp /= 10;`                 |
| 区间求和     | 循环从 low 到 high 累加                              |
| 布尔结果     | 循环中判断条件，记录 true/false                      |

{: .note}
> **大纲要求掌握的标准算法（EK 2.9.A.1）：**
> - 判断一个整数是否**能被另一个整数整除**：`num % divisor == 0`。
> - **提取整数中的各个数字**：`num % 10` 取末位，`num / 10` 去掉末位。
> - **统计某个数字/值出现的频率**：循环中计数。
> - 计算和、平均值、最小值、最大值。
> - 找出满足特定条件的值（如奇数、正数等）。

- ### 例题 1 — 数字逐位输出

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q9

  Consider the following code segment.

  ```java
  int num = 245;
  int temp = num;
  while (temp > 0)
  {
      System.out.print(temp % 10 + " ");
      temp /= 10;
  }
  ```

  What is printed as a result of executing this code segment?

  (A) `2 4 5`  
  (B) `4 5`  
  (C) `5 4`  
  (D) `5 4 2`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环用 `temp % 10` 打印最右边的数字，再用 `temp /= 10` 去掉它：245 → 打印 5，temp = 24 → 打印 4，temp = 2 → 打印 2，temp = 0 退出。输出 "5 4 2"。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 区间求和修正

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q10

  In the following code segment, assume that low and high are properly declared and initialized int variables and that `low < high`. The code segment is intended to print the sum of the integers between low and high, inclusive, but does not always work as intended.

  ```java
  int sum = 0;          // line 1
  int j = low;          // line 2
  while (sum <= high)   // line 3
  {
      sum += j;         // line 5
      j++;              // line 6
  }
  System.out.println(sum);
  ```

  Which of the following changes can be made so that this code segment works as intended?

  (A) Changing line 1 to `int sum = low;`  
  (B) Changing line 2 to `int j = 0;`  
  (C) Changing line 3 to `while (j <= high)`  
  (D) Interchanging lines 5 and 6

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    原循环条件 `sum <= high` 检查的是**累加和**而非当前数 j，循环终止时机错误。应改为 `while (j <= high)`：当 j 超过 high 时停止，保证从 low 加到 high 的所有整数都被累加。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 数位求和

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q11

  In the following code segment, num has been assigned a positive int value.

  ```java
  int x = 0;
  int temp = num;
  while (temp > 0)
  {
      x += temp % 10;
      temp /= 10;
  }
  System.out.println(x);
  ```

  Which of the following best describes the value printed by this code segment?

  (A) A count of the number of digits in num  
  (B) The average of the digits in num  
  (C) The sum of the digits in num  
  (D) Whether num is evenly divisible by 10

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环用 `temp % 10` 取出每一位并累加到 x，然后 `temp /= 10` 去掉末位。最终 x 是 num 各位数字的**总和**。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 布尔表达式等价（== 两侧为布尔）

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q28

  Consider the following statement.

  ```java
  boolean x = (5 < 8) == (5 == 8);
  ```

  What is the value of `x` after the statement is executed?

  (A) 5  
  (B) 8  
  (C) true  
  (D) false

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `5 < 8` 为 true，`5 == 8` 为 false。`true == false` 为 false，所以 x = false。正确答案是 **(D)**。

  </details>

- ### 例题 5 — 布尔比较表达式

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q30

  In the following Boolean expression, the int variables x and y have been properly declared and initialized.

  ```java
  (x <= 10) == (y > 25)
  ```

  Which of the following values for x and y will result in the expression evaluating to true?

  (A) x = 8 and y = 25  
  (B) x = 10 and y = 10  
  (C) x = 10 and y = 30  
  (D) x = 15 and y = 30

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    只有当两侧布尔值**相同**时 `==` 才为 true。选项 (C)：x = 10 → `10 <= 10` 为 true；y = 30 → `30 > 25` 为 true；`true == true` 为 true。其他选项两侧一真一假。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点           | 关键内容                                     | 考试提示                                       |
| -------------- | -------------------------------------------- | ---------------------------------------------- |
| 数字分解       | `% 10` 取末位、`/ 10` 去末位                 | 配合 while 循环逐个处理                        |
| 数位求和       | `sum += temp % 10`                           | 循环终止条件 `temp > 0`                       |
| 区间求和       | 循环条件用**控制变量**而非累加和             | `while (j <= high)` 而非 `while (sum <= high)`|
| 布尔等价       | `(A) == (B)` 两侧都必须是布尔值              | 先求各侧真假再比较                            |
| 算法实现       | 明确循环的终止条件与更新语句                 | 检查边界值（low、high）                        |
