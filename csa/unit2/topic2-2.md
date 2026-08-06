---
layout: default
title: 2.2 Boolean Expressions
parent: Unit 2
nav_order: 2
---

# 2.2 — Boolean Expressions

## 2.2.A 关系运算符（Relational Operators）

**布尔表达式（Boolean Expression）** 求值为 `true` 或 `false`。AP CSA 中的关系运算符：

| 运算符 | 含义           | 示例          |
| ------ | -------------- | ------------- |
| `==`   | 等于           | `a == b`      |
| `!=`   | 不等于         | `a != b`      |
| `<`    | 小于           | `x < 10`      |
| `<=`   | 小于或等于     | `x <= 10`     |
| `>`    | 大于           | `x > 0`       |
| `>=`   | 大于或等于     | `x >= 5`      |

{: .important}
> - 关系运算返回 `boolean` 值，可用于**布尔变量赋值**和 `if` 条件。
> - 算术表达式（如 `3 + 4`）可以与关系运算符组合：`(3 + 4 == 5)`。
> - 布尔表达式之间也可以用 `==` / `!=` 比较：`(x <= 10) == (y > 25)`。
> - **基本类型**用 `==` 比较的是**实际值**；**引用类型**（对象）用 `==` 比较的是**引用**（是否指向同一对象），比较对象内容要使用方法（如 String 的 `equals`）。

## 2.2.B 布尔表达式的求值

布尔变量可以直接用于表达式；`==` 判断两个布尔值是否**相同**，`!=` 判断是否**不同**。

```java
boolean a = true;
boolean b = false;
boolean result = (a != b);   // result = true
```

- ### 例题 1 — 布尔变量比较的陷阱

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q4

  Consider the following code segment, which is intended to print true only when both r and v are positive numbers. Assume that r and v have been properly declared and initialized.

  ```java
  boolean rPos = r > 0;
  boolean vPos = v > 0;
  System.out.print(rPos == vPos);
  ```

  The code segment does not always work as intended.

  Which of the following values for r and v will demonstrate that this code segment does not work as intended?

  (A) r = -10, v = 10  
  (B) r = -1, v = -4  
  (C) r = 5, v = -2  
  (D) r = 6, v = 3

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `rPos == vPos` 在 rPos 和 vPos **相同**时为 true。选项 (B)：r = -1 → rPos = false；v = -4 → vPos = false；`false == false` 为 true，但题目期望两者都为正是才打印 true（两个都是负数应打印 false）。选项 (B) 证明代码不符合预期。正确答案是 **(B)**。

  </details>

- ### 例题 2 — != 运算符

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q5

  In the following code segment, a and b are properly declared and initialized boolean variables.

  ```java
  boolean result = (a != b);
  System.out.println(result);
  ```

  Which of the following best describes the behavior of the code segment?

  (A) It prints true if a is true and b is false, and prints false otherwise.  
  (B) It prints true if a and b have different values, and prints false otherwise.  
  (C) It prints true if a and b have the same value, and prints false otherwise.  
  (D) It prints false for all possible values of a and b.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `a != b` 在 a 和 b **不相等**时求值为 true。选项 (B) 准确描述了该行为。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 算术与关系组合

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q6

  Consider the following expression.

  ```java
  (3 + 4 == 5) != (3 + 4 >= 5)
  ```

  What value, if any, does the expression evaluate to?

  (A) true  
  (B) false  
  (C) 5  
  (D) No value; relational operators cannot be used on arithmetic expressions.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `3 + 4 == 5` → `7 == 5` → **false**；`3 + 4 >= 5` → `7 >= 5` → **true**。两个布尔值不同，`false != true` → **true**。关系运算符完全可以用于算术表达式的结果。正确答案是 **(A)**。

  </details>

- ### 例题 4 — 布尔表达式的值（== 两侧）

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q21

  Consider the following code segment.

  ```java
  int a = 10;
  int b = 5 * 2;
  System.out.print(a == b);
  ```

  What is printed as a result of executing the code segment?

  (A) 10  
  (B) `10==10`  
  (C) true  
  (D) false

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `b = 5 * 2 = 10`，所以 `a == b` 即 `10 == 10`，求值为 **true**。`==` 返回的是布尔值，不是数字。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点           | 关键内容                                   | 考试提示                                 |
| -------------- | ------------------------------------------ | ---------------------------------------- |
| 关系运算符     | `==` `!=` `<` `<=` `>` `>=`                | 返回 boolean                             |
| 布尔比较       | `==` 判断布尔值相同，`!=` 判断不同         | 注意与"两个数都大于 0"这类意图的区别     |
| 表达式组合     | 算术表达式可以作为关系运算的操作数         | 先算算术，再比较                         |
| 常见陷阱       | `rPos == vPos` 不等于"r 和 v 都为正"       | 两个 false 也相等                        |
