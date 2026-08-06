---
layout: default
title: 2.1 Algorithms with Selection and Repetition
parent: Unit 2
nav_order: 1
---

# 2.1 — Algorithms with Selection and Repetition

## 2.1.A 选择（Selection）与重复（Repetition）

许多算法需要**选择**和**重复**两种控制结构：

- **选择（Selection）**：根据条件决定执行哪些步骤，用 `if` 语句实现。例如："如果 x 大于 y，则交换 x 和 y"。
- **重复（Repetition）**：反复执行一组步骤，用 `while` / `for` 循环实现。例如："重复比较并交换，直到所有数有序"。

{: .note}
> 设计算法时，先想清楚每一步的**条件**和**顺序**，再考虑如何组合选择与重复，往往可以避免逻辑漏洞（例如漏掉最后一个比较）。

- ### 例题 1 — 选择+重复的排序算法

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q1

  The variables x, y, and z are integers. Which of the following algorithms can be used to swap the values of the variables so that they are ordered from least to greatest (i.e., x ≤ y ≤ z)?

  (A) Step 1: If x is greater than y, swap the values of x and y. / Step 2: If y is greater than z, swap the values of y and z.  
  (B) Step 1: If x is greater than z, swap the values of x and z. / Step 2: If y is greater than z, swap the values of y and z.  
  (C) Step 1: If x is greater than y, swap the values of x and y. / Step 2: If y is greater than z, swap the values of y and z. / Step 3: If x is greater than y, swap the values of x and y.  
  (D) Step 1: If x is greater than y, swap the values of x and y. / Step 2: If y is greater than z, swap the values of y and z. / Step 3: If x is greater than z, swap the values of x and z.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (C)：Step 1 保证 x ≤ y；Step 2 把最大的数放到 z（z 成为最大）；Step 3 再次比较 x 和 y，保证 x 是最小。三步后 x ≤ y ≤ z。选项 (A)(B) 只有两步，无法保证三个数完全有序；(D) 的 Step 3 比较 x 和 z，可能破坏 Step 2 已形成的顺序。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 分步选择的密码分类算法

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q2

  A company is designing a program to evaluate the strength of a user's password. The program needs to indicate if the password is "weak," "medium," or "strong" based on the following guidelines.

  - A password with fewer than 8 characters is classified as "weak."
  - A password with 8 or more characters is classified as "medium," where all characters are either numbers or letters.
  - A password with 8 or more characters plus at least one special character (like !, @, or #) is classified as "strong."

  Which of the following algorithms will correctly classify a password?

  (A) Step 1: If the password has fewer than 8 characters, label it as "weak" and skip Steps 2 and 3. Otherwise, go to Step 2. / Step 2: If the password has more than 8 characters, label it as "medium" and skip Step 3. Otherwise, go to Step 3. / Step 3: Label the password as "strong."  
  (B) Step 1: If the password has fewer than 8 characters, label it as "weak" and skip Steps 2 and 3. Otherwise, go to Step 2. / Step 2: If the password contains at least one special character, label it as "strong" and skip Step 3. Otherwise, go to Step 3. / Step 3: Label the password as "medium."  
  (C) Step 1: If the password has 8 or more characters, label it as "medium" and skip Steps 2 and 3. Otherwise, go to Step 2. / Step 2: If the password has more than 8 characters and contains at least one special character, label it as "strong" and skip Step 3. Otherwise, go to Step 3. / Step 3: Label the password as "weak."  
  (D) Step 1: If the password has 8 or more characters and contains at least one special character, label it as "strong" and skip Steps 2 and 3. Otherwise, go to Step 2. / Step 2: If the password does not contain at least one special character, label it as "medium" and skip Step 3. Otherwise, go to Step 3. / Step 3: Label the password as "weak."

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (B)：先排除 <8 字符的 "weak"；再判断是否含特殊字符，有则为 "strong"；最后剩下的（≥8 字符且无特殊字符）为 "medium"。每次只走一条路径，覆盖了所有情况。选项 (A) 的 Step 2 条件 ">8" 与 "≥8" 不吻合且漏判；(C)(D) 均有逻辑漏洞。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 用户分类算法

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q3

  Users of a mobile application are categorized based on the average number of hours they use the application each day, as shown in the following table.

  | Category       | Average Hours of Use Per Day |
  | -------------- | ---------------------------- |
  | Top User       | Greater than 5               |
  | Regular User   | Between 1 and 5, inclusive   |
  | Inactive User  | Less than 1                  |

  Suppose `n` is the average number of hours a user spends using the application each day. Which of the following algorithms can be used to assign the correct categorization to a user?

  (A) If n is greater than 5, categorize the user as a top user. Otherwise, if n is less than or equal to 5, categorize the user as a regular user. Otherwise, categorize the user as an inactive user.  
  (B) If n is greater than 5, categorize the user as a top user. Otherwise, if n is greater than or equal to 1, categorize the user as a regular user. Otherwise, categorize the user as an inactive user.  
  (C) If n is less than 1, categorize the user as an inactive user. Otherwise, if n is greater than or equal to 1, categorize the user as a regular user. Otherwise, categorize the user as a top user.  
  (D) If n is greater than or equal to 1, categorize the user as a regular user. Otherwise, if n is less than 1, categorize the user as an inactive user. Otherwise, categorize the user as a top user.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (B)：先判断 n > 5 → top；再判断 n ≥ 1 → regular；剩余 n < 1 → inactive。三个分支覆盖所有可能。选项 (A) 把 n ≤ 5 全部归为 regular，n < 1 的情况永远不会走到 inactive 分支；选项 (C)(D) 也存在覆盖不到 top user 的问题。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                       | 考试提示                                       |
| ------------------ | ---------------------------------------------- | ---------------------------------------------- |
| 选择结构           | 根据条件执行不同分支（if / else）              | 条件顺序决定逻辑是否正确                       |
| 重复结构           | 反复执行步骤（while / for）                    | 注意循环终止条件                               |
| 算法设计           | 覆盖所有情况、避免重复判断                     | 用"先排除、再细分"的思路验证每个分支           |
| 边界条件           | ≥、>、<、≤ 的区分                              | 检查端点值（如 n = 5、n = 1）                  |
