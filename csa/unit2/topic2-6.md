---
layout: default
title: 2.6 Comparing Boolean Expressions
parent: Unit 2
nav_order: 6
---

# 2.6 — Comparing Boolean Expressions

## 2.6.A 德摩根定律（De Morgan's Law）

**德摩根定律**提供了布尔表达式的等价转换规则：

```
!(a && b)  ≡  !a || !b
!(a || b)  ≡  !a && !b
```

{: .important}
> 应用德摩根定律时，把 `&&` 换成 `||`、`||` 换成 `&&`，并对每个子表达式取反。这在把"否定一个复杂条件"转换成等价形式时非常有用。

## 2.6.B 布尔表达式的等价比较

- `(x <= 10) == (y > 25)`：比较两个布尔表达式的值是否**相同**。
- 字符串内容比较必须用 `equals`，不能用 `==`（`==` 比较引用）。

## 2.6.C 对象引用的比较

**两个不同的引用变量可以指向同一个对象**；用 `==` 和 `!=` 比较对象引用，判断的是"是否指向**同一个**对象"，而不是内容是否相同：

```java
String s1 = "abc";
String s2 = s1;        // s1 和 s2 指向同一个 String 对象
System.out.println(s1 == s2);   // true（同一引用）
```

{: .note}
> - 引用可以与 **`null`** 用 `==` / `!=` 比较，判断该引用是否真的指向某个对象：`if (s != null)`。
> - 判断两个**对象内容**是否相等，通常使用类提供的方法（如 String 的 `equals`），而不是 `==`。

- ### 例题 1 — 用德摩根定律判断恒等式

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q16

  In the following code segment, x is a properly declared and initialized boolean variable and y is a properly declared and initialized int variable.

{% raw %}
  ```java
  boolean a = !x && y > 50000;
  boolean b = !(x || y <= 50000);
  boolean c = !x || y <= 50000;
  boolean d = !(x && y <= 50000);

  if (a == b)
  {
      System.out.println("First");
  }
  if (a == c)
  {
      System.out.println("Second");
  }
  if (b == c)
  {
      System.out.println("Third");
  }
  if (c == d)
  {
      System.out.println("Fourth");
  }
  ```
{% endraw %}

  Which of the following is always printed as a result of executing this code segment?

  (A) First  
  (B) Second  
  (C) Third  
  (D) Fourth

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    对 b 应用德摩根定律：`!(x || y <= 50000)` ≡ `!x && !(y <= 50000)` ≡ `!x && y > 50000`，正好等于 a。所以 `a == b` 恒为 true，"First" 一定被打印。其他表达式之间并非恒等。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 德摩根定律与像素判断

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q17

  An image on a computer is made up of many pixels. Each pixel in the image contains varying amounts of red, green, and blue. A "mainly red" pixel is defined to be one in which the percentage of red is more than 50, and the percentages of green and blue are each less than 10.

  Assume that redPct, greenPct, and bluePct are int variables that have been properly declared and initialized with values representing the percentages of red, green, and blue, respectively, in a pixel.

  Which of the following expressions will evaluate to true for a "mainly red" pixel?

  (A) `(redPct <= 50) || (greenPct >= 10) || (bluePct >= 10)`  
  (B) `(redPct > 50) && (greenPct < 10) || (bluePct < 10)`  
  (C) `!( (redPct <= 50) || (greenPct >= 10) || (bluePct >= 10) )`  
  (D) `!(redPct > 50) && !(greenPct > 10) && !(bluePct > 10)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    "mainly red" 要求：redPct > 50 **且** greenPct < 10 **且** bluePct < 10。选项 (C) 先构造"不是 mainly red"的条件 `(redPct <= 50) || (greenPct >= 10) || (bluePct >= 10)`，再整体取反，等价于 `redPct > 50 && greenPct < 10 && bluePct < 10`。正确答案是 **(C)**。

  </details>

- ### 例题 3 — String 比较必须用 equals

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q18

  In the following code segment, str1 and str2 are String objects. The code segment is intended to print true if str1 and str2 are non-null strings that contain the same sequence of characters. The code segment is intended to print false otherwise.

{% raw %}
  ```java
  boolean result = false;            // line 1
  if (str1 != null && str2 != null)  // line 2
  {
      result = str1 == str2;         // line 4
  }
  System.out.println(result);
  ```
{% endraw %}

  Which of the following best explains the error, if any, in the code segment?

  (A) In line 1, result should be initialized to true.  
  (B) In line 2, str1 and str2 should be compared to null with the equals method.  
  (C) In line 4, str1 and str2 should be compared to each other with the equals method.  
  (D) The code segment contains no errors and works as intended.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    第 2 行用 `!=` 与 null 比较是正确的（null 检查用 `==`/`!=`）。但第 4 行用 `==` 比较两个 String，只会判断它们是否引用**同一个对象**，而不是内容是否相同。要比较字符串内容应使用 `equals` 方法。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 真值表分析

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q8

  In the following Boolean expressions, x and y are properly declared and initialized boolean variables.

  **Expression A:** `x && y`

  **Expression B:** `!x && !y`

  Which of the following best describes the relationship between values produced by Expression A and Expression B?

  (A) Expression A and Expression B evaluate to different values for all values of x and y.  
  (B) Expression A and Expression B evaluate to the same value for all values of x and y.  
  (C) Expression A and Expression B evaluate to the same value only when x and y have the same value.  
  (D) Expression A and Expression B evaluate to the same value only when x and y have different values.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    列真值表：x=true, y=true：A=true, B=false；x=true, y=false：A=false, B=false；x=false, y=true：A=false, B=false；x=false, y=false：A=false, B=true。当 x 和 y 值**不同**时（(true,false) 和 (false,true)），A 与 B 都为 false；x 和 y 值相同时两者不同。正确答案是 **(D)**。

  </details>

- ### 例题 5 — 等价表达式（De Morgan 反向）

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q12

  In the following code segment, the int variables a, b, c, and d have been properly declared and initialized.

{% raw %}
  ```java
  if (a < b || c != d)
  {
      System.out.println("dog");
  }
  else
  {
      System.out.println("cat");
  }
  ```
{% endraw %}

  Which of the following code segments produces the same output as the given code segment for all values of a, b, c, and d?

  (A)
{% raw %}
  ```java
  if (a < b && c != d)
  {
      System.out.println("dog");
  }
  else
  {
      System.out.println("cat");
  }
  ```
{% endraw %}
  (B)
{% raw %}
  ```java
  if (a > b && c == d)
  {
      System.out.println("cat");
  }
  else
  {
      System.out.println("dog");
  }
  ```
{% endraw %}
  (C)
{% raw %}
  ```java
  if (a >= b || c == d)
  {
      System.out.println("cat");
  }
  else
  {
      System.out.println("dog");
  }
  ```
{% endraw %}
  (D)
{% raw %}
  ```java
  if (a >= b && c == d)
  {
      System.out.println("cat");
  }
  else
  {
      System.out.println("dog");
  }
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    原代码在 `a < b || c != d` 为 true 时打印 "dog"。打印 "cat" 的条件是原条件为 false：`!(a < b || c != d)`。对德摩根定律：`!(a < b || c != d)` ≡ `a >= b && c == d`。选项 (D) 中该条件成立时打印 "cat"，否则打印 "dog"，与原代码完全等价。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                       | 考试提示                                   |
| ---------------- | ---------------------------------------------- | ------------------------------------------ |
| 德摩根定律       | `!(a&&b)` = `!a\|\|!b`；`!(a\|\|b)` = `!a&&!b` | 否定复杂条件时使用                         |
| 等价表达式       | 条件取反 + 交换输出分支                        | 验证时用真值表                             |
| 真值表分析       | 列出所有 x、y 组合                             | 布尔表达式恒等式判断                        |
| 引用比较         | `==`/`!=` 判断是否同一对象；可与 null 比较     | 两个变量可指向同一对象                     |
| equals vs ==     | String 内容比较用 `equals`；null 检查用 `==`   | 对象内容相等 ≠ 引用相等                    |
