---
layout: default
title: 2.5 Compound Boolean Expressions
parent: Unit 2
nav_order: 5
---

# 2.5 — Compound Boolean Expressions

## 2.5.A 逻辑运算符

**复合布尔表达式（Compound Boolean Expression）** 用逻辑运算符连接两个或多个布尔表达式：

| 运算符 | 含义     | 说明                                     |
| ------ | -------- | ---------------------------------------- |
| `&&`   | 与（AND） | 两边都为 true 结果才为 true              |
| `\|\|` | 或（OR）  | 至少一边为 true 结果就为 true            |
| `!`    | 非（NOT） | 取反：true ↔ false                       |

**优先级（从高到低）：** `!` > 关系运算符（`<`, `>`, `==` 等）> `&&` > `||`

{: .important}
> `&&` 和 `||` 采用**短路求值（Short-Circuit Evaluation）**：
> - `a && b`：若 a 为 false，**不再求值 b**，直接得 false。
> - `a || b`：若 a 为 true，**不再求值 b**，直接得 true。

## 2.5.B 边界条件的表达

判断一个值在区间 `[low, high]` 内：`x >= low && x <= high`（两个条件都要满足，用 `&&`）。

- ### 例题 1 — 用 && 表达区间

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q13

  A certain device requires a passcode to be used. The passcode must meet both of the following requirements.

  - The passcode must be 4 digits long.
  - The passcode must not start with a zero (0) digit.

  Assume that `pass` is a properly declared and initialized int variable.

  Which of the following expressions will evaluate to true if pass is an acceptable passcode?

  (A) `pass >= 1000 || pass < 10000`  
  (B) `pass > 1000 || pass <= 10000`  
  (C) `pass >= 1000 && pass < 10000`  
  (D) `pass > 1000 && pass < 10000`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    4 位数且不以 0 开头，即 1000 ≤ pass ≤ 9999，等价于 `pass >= 1000 && pass < 10000`。选项 (C) 使用 `&&` 同时满足两个条件；(A)(B) 用 `||`，任意一边为真就为真，会把 100 或 20000 等也判为合格。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 区间端点的包含

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q14

  A fitness application categorizes daily step counts into different activity levels. The "Active" level is defined as any step count between 10,000 and 15,000, inclusive. The following code segment is intended to determine if a user's step count falls within the "Active" category.

  ```java
  if (steps > 10000 && steps < 15000)
  {
      activityLevel = "Active";
  }
  ```

  Which of the following best explains the error, if any, in this code segment?

  (A) There is no error in the code segment as it correctly identifies "Active" step counts.  
  (B) The condition should be `if (steps >= 10000 && steps <= 15000)` to properly include 10,000 and 15,000.  
  (C) The condition should be `if (steps > 10000 || steps < 15000)` to include the correct range of step counts.  
  (D) The condition should be `if (steps >= 10000 || steps <= 15000)` to include all step counts from 10,000 and above, as well as 15,000 and below.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    题目要求区间**含端点**（10,000 和 15,000 都算 "Active"）。原代码用 `>` 和 `<` 排除了端点。选项 (B) 用 `>=` 和 `<=` 正确包含端点。选项 (C)(D) 用 `||` 会匹配几乎所有步数，完全错误。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 短路求值

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q15

  Consider the following code segment.

  ```java
  boolean a = true;
  boolean b = true;
  System.out.print((b || (!a || b)) + " ");
  System.out.print(((!b || !a) && a) + " ");
  System.out.println(!(a && b) && b);
  ```

  What output is produced when this code segment is executed?

  (A) `true true true`  
  (B) `true false true`  
  (C) `true false false`  
  (D) `false true false`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    ① `b || (!a || b)`：b 为 true，短路，得 **true**。② `(!b || !a) && a`：!b = false，!a = false，`(!b || !a)` = false，`&& a` 短路得 **false**。③ `!(a && b) && b`：a && b = true，!true = false，短路得 **false**。输出 `true false false`。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 等价布尔表达式

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q1

  Consider the following code segment.

  ```java
  boolean b1 = true && ((5 % 2) == 0);
  boolean b2 = /* missing expression */;
  ```

  Which of the following can replace `/* missing expression */` so that the value stored in b2 is the same as the value stored in b1 after the code segment has executed?

  (A) `false || ((5 % 2) == 1)`  
  (B) `false && ((5 % 2) == 1)`  
  (C) `true || ((5 % 2) == 1)`  
  (D) `true && ((5 % 2) == 1)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `5 % 2 == 0` → `1 == 0` → false，`true && false` → false，所以 b1 = false。选项 (B)：`false && ...` 短路求值直接得 **false**，与 b1 相同。选项 (A) `false || true` = true；(C) `true || ...` = true；(D) `true && true` = true。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                   | 考试提示                                     |
| ---------------- | ------------------------------------------ | -------------------------------------------- |
| 逻辑运算符       | `&&`、`\|\|`、`!`                          | 优先级：`!` > 关系 > `&&` > `\|\|`           |
| 区间表达         | `x >= low && x <= high`                    | 端点是否包含决定用 `>` 还是 `>=`             |
| 短路求值         | `&&` 遇 false 停、`\|\|` 遇 true 停        | 短路时右侧表达式不被求值                     |
| 等价表达式       | 用短路特性构造等价布尔表达式                | `false && X` 恒为 false                      |
