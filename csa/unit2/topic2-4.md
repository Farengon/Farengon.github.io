---
layout: default
title: 2.4 Nested if Statements
parent: Unit 2
nav_order: 4
---

# 2.4 — Nested if Statements

## 2.4.A 嵌套 if 语句（Nested if）

**嵌套 if（Nested if）** 是 if 语句内部再包含 if 语句：

{% raw %}
```java
if (外层条件) {
    if (内层条件) {
        // 两层条件都满足
    } else {
        // 外层满足、内层不满足
    }
}
```
{% endraw %}

{: .important}
> 追踪嵌套 if 时，**一层一层判断**：先看外层条件是否为 true，再进入内层判断。注意每个 `else` 与哪个 `if` 配对。

**多路选择（Multiway Selection）：** `if-else if` 链用于有一系列条件、每个条件对应不同代码段的情况——**最多只有一个**分支会被执行（第一个条件为 true 的分支）。

{: .note}
> 嵌套 if 的关键性质：**内层 if 的布尔条件只有在外层 if 条件为 true 时才会被求值**。

## 2.4.B 嵌套 if 与 else if 的组合

嵌套 if 与 `else if` 可以组合使用，形成复杂的决策逻辑。追踪时要特别注意**缩进和花括号**对应的归属关系。

- ### 例题 1 — 嵌套 if 追踪（result 拼接）

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q11

  Consider the following code segment, which uses properly declared and initialized `int` variables `x` and `y` and the `String` variable `result`.

{% raw %}
  ```java
  String result = "";
  if (x < 5)
  {
      if (y > 0)
      {
          result += "a";
      }
      else
      {
          result += "b";
      }
  }
  else if (x > 10)
  {
      if (y < 0)
      {
          result += "c";
      }
      else if (y < 10)
      {
          result += "d";
      }
      result += "e";
  }
  result += "f";
  ```
{% endraw %}

  What is the value of `result` after the code segment is executed if `x` has the value 15 and `y` has the value 5?

  (A) `adf`  
  (B) `d`  
  (C) `def`  
  (D) `ef`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    x = 15：`x < 5` 为 false，`x > 10` 为 true，进入外层 else if。y = 5：`y < 0` 为 false，`y < 10` 为 true，result += "d"。然后 `result += "e"`（在 else if 块内、内层 if 之外，无条件执行）。最后 `result += "f"`（最外层，无条件执行）。result = "def"。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 等价的嵌套 if 结构

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q12

  In the following code segment, `str` is a properly declared and initialized String variable.

{% raw %}
  ```java
  int result = 0;
  if (str.length() > 5)
  {
      if (str.indexOf("A") < 0)
      {
          result = 1;
      }
      else if (str.indexOf("B") < 0)
      {
          result = 2;
      }
  }
  else if (str.indexOf("A") < 0)
  {
      result = 3;
  }
  ```
{% endraw %}

  Which of the following code segments assigns the same value to `result` as the preceding code segment for all values of `str`?

  (A)
{% raw %}
  ```java
  int result = 0;
  if (str.indexOf("A") < 0)
  {
      result = 3;
  }
  else if (str.indexOf("B") < 0)
  {
      result = 2;
  }
  else if (str.length() > 5)
  {
      result = 1;
  }
  ```
{% endraw %}
  (B)
{% raw %}
  ```java
  int result = 0;
  if (str.indexOf("A") < 0)
  {
      if (str.length() > 5)
      {
          result = 1;
      }
      else if (str.indexOf("B") < 0)
      {
          result = 2;
      }
      else
      {
          result = 3;
      }
  }
  ```
{% endraw %}
  (C)
{% raw %}
  ```java
  int result = 0;
  if (str.indexOf("A") < 0)
  {
      if (str.length() > 5)
      {
          result = 1;
      }
      else
      {
          result = 3;
      }
  }
  else if (str.indexOf("B") < 0)
  {
      if (str.length() > 5)
      {
          result = 2;
      }
  }
  ```
{% endraw %}
  (D)
{% raw %}
  ```java
  int result = 0;
  if (str.indexOf("B") < 0)
  {
      if (str.length() > 5)
      {
          result = 2;
      }
  }
  else if (str.indexOf("A") < 0)
  {
      if (str.length() > 5)
      {
          result = 1;
      }
      else
      {
          result = 3;
      }
  }
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (C) 与原文等价。原文逻辑：若 length > 5 且无 "A" → 1；若 length > 5、有 "A" 且无 "B" → 2；若 length ≤ 5 且无 "A" → 3。(C) 中：无 "A" 时，length > 5 → 1，否则 → 3；有 "A" 且无 "B" 时，length > 5 → 2，否则保持 0（与原文一致，因为原文在有 "A" 且 length ≤ 5 时 result 也为 0）。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 嵌套 if 的数值追踪

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q16

  Consider the following code segment.

{% raw %}
  ```java
  int start = 4;
  int end = 5;

  if (start < end)
  {
      if (end > 0)
      {
          start += 2;
          end++;
      }
      else
      {
          end += 3;
      }
  }

  if (start < end)
  {
      if (end == 0)
      {
          end += 2;
          start++;
      }
      else
      {
          end += 4;
      }
  }
  ```
{% endraw %}

  What is the value of end after the code segment is executed?

  (A) 5  
  (B) 6  
  (C) 9  
  (D) 10

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    第一组：`start < end`（4 < 5）为 true；`end > 0` 为 true：start = 4 + 2 = 6，end = 5 + 1 = 6。第二组：`start < end`（6 < 6）为 false，整个嵌套块不执行。最终 end = 6。正确答案是 **(B)**。

  </details>

- ### 例题 4 — 嵌套 if 的布尔追踪

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q17

  Consider the following code segment.

{% raw %}
  ```java
  int x = 7;
  int y = 4;
  boolean a = false;
  boolean b = false;

  if (x > y)
  {
      if (x % y >= 3)
      {
          a = true;
          x -= y;
      }
      else
      {
          x += y;
      }
  }

  if (x < y)
  {
      if (y % x >= 3)
      {
          b = true;
          x -= y;
      }
      else
      {
          x += y;
      }
  }
  ```
{% endraw %}

  What are the values of a, b, and x after the code segment is executed?

  (A) a = true, b = true, x = -1  
  (B) a = true, b = false, x = 3  
  (C) a = true, b = false, x = 7  
  (D) a = false, b = false, x = 11

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    第一组：`x > y`（7 > 4）为 true；`x % y >= 3`（7 % 4 = 3 ≥ 3）为 true：a = true，x = 7 − 4 = 3。第二组：`x < y`（3 < 4）为 true；`y % x >= 3`（4 % 3 = 1 ≥ 3）为 false，走 else：x = 3 + 4 = 7，b 保持 false。最终 a = true, b = false, x = 7。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                     |
| ------------------ | -------------------------------------------- | -------------------------------------------- |
| 嵌套 if 结构       | if 内嵌 if / else                            | 一层一层追踪，先外层后内层                   |
| else 配对          | else 与最近的未配对 if 配对                  | 花括号决定归属                               |
| 变量追踪           | 按执行顺序更新变量值                         | 条件边界（≥、<）要精确                       |
| 等价结构转换       | 嵌套 if ↔ else if 链可互相转换               | 保持相同逻辑优先级                           |
