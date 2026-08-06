---
layout: default
title: 4.16 Recursion
parent: Unit 4
nav_order: 16
---

# 4.16 — Recursion

## 4.16.A 递归的基本结构

**递归（Recursion）** 是方法调用自身来解决问题的方法。递归方法必须有两个部分：

1. **基本情况（Base Case）**：停止递归的条件，直接返回结果。
2. **递归情况（Recursive Case）**：把问题缩小，调用自身。

{% raw %}
```java
public static int mystery(int n)
{
    if (n < 10)              // 基本情况
    {
        return n;
    }
    return (n % 10) + mystery(n / 10);   // 递归情况
}
```
{% endraw %}

{: .important}
> 追踪递归时，**逐层展开**调用，最后**从最内层开始**逐层返回结果。注意每层调用的参数如何变化（如 n/10、n-2、substring(1) 等）。

## 4.16.B 追踪递归的要点

- 画出每一层的调用与返回值。
- 基础情况不满足时继续递归；满足时开始返回。
- 返回值逐层组合（加法、拼接等）。

{: .important}
> **每次递归调用都有自己独立的局部变量（包括参数）**。参数值记录递归的进度，就像循环控制变量记录循环的进度一样。追踪时不要把不同调用层的变量混为一谈。

## 4.16.C 递归与迭代的等价性

**任何递归解法都可以用迭代（循环）实现，反之亦然**——递归只是另一种形式的重复（repetition）。

{% raw %}
```java
// 递归版：求 1 到 n 的和
public static int sumRec(int n)
{
    if (n <= 0)
    {
        return 0;
    }
    return n + sumRec(n - 1);
}

// 等价的迭代版
public static int sumIter(int n)
{
    int sum = 0;
    for (int i = 1; i <= n; i++)
    {
        sum += i;
    }
    return sum;
}
```
{% endraw %}

{: .note}
> **Exclusion Statement：** 编写递归代码不在 AP CSA 考试范围内——考试只要求**追踪（trace）**递归方法的结果。

- ### 例题 5 — 递归的局部变量与参数

  > **Source:** 大纲 EK 4.16.A.2 改编

  追踪 `mystery(3)`（方法见上：`if (n < 10) return n; else return n + mystery(n - 1)`）：

  - 调用 `mystery(3)`：参数 n = 3（这一层自己的局部变量）。3 < 10？不，走递归：3 + `mystery(2)`。
  - 调用 `mystery(2)`：参数 n = 2（**新的独立参数**，与上一层的 n 互不影响）。2 < 10？不：2 + `mystery(1)`。
  - 调用 `mystery(1)`：参数 n = 1。1 < 10？是 → 返回 1。
  - 逐层返回：`mystery(1)` = 1 → `mystery(2)` = 2 + 1 = 3 → `mystery(3)` = 3 + 3 = 6。

  每一层都有自己独立的 n，这就是"参数值记录递归进度"的含义。

- ### 例题 1 — 数位求和递归

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q16

  Consider the following method.

{% raw %}
  ```java
  public static int mystery(int n)
  {
      if (n < 10)
      {
          return n;
      }
      return (n % 10) + mystery(n / 10);
  }
  ```
{% endraw %}

  Assume that the int variable num is properly declared and initialized to a value greater than 0. Which of the following best describes the value returned by the call `mystery(num)`?

  (A) The value of num  
  (B) The rightmost digit of num  
  (C) The sum of the digits of num  
  (D) Two times the rightmost digit of num

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    递归情况取出最右边的数字 `n % 10`，加上对 `n / 10` 的递归调用结果。基础情况（一位数）返回自身。因此返回值是 num 各数位之和。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 递归中除零

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q17

  The following recursive method is intended to return true if origNum is divisible by each digit in numsToDivideBy, and to return false otherwise. For example, `isDivisible(236, 24)` should return true because 236 is divisible by both 2 and 4. The method does not always work as intended.

{% raw %}
  ```java
  public static boolean isDivisible(int origNum, int numsToDivideBy)
  {
      if (numsToDivideBy == 0)
      {
          return true;
      }
      else if (origNum % (numsToDivideBy % 10) != 0)
      {
          return false;
      }
      else
      {
          return isDivisible(origNum, numsToDivideBy / 10);
      }
  }
  ```
{% endraw %}

  Which of the following method calls can be used to demonstrate that the method does not work as intended?

  (A) `isDivisible(120, 12)`  
  (B) `isDivisible(135, 5)`  
  (C) `isDivisible(225, 105)`  
  (D) `isDivisible(296, 341)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (C)：第一次调用 `isDivisible(225, 105)`，检查 105 % 10 = 5，225 % 5 = 0 通过，递归调用 `isDivisible(225, 10)`。此时 `10 % 10 = 0`，表达式 `225 % 0` 抛出 **ArithmeticException**（方法没有检查除数为 0 的情况）。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 递减递归追踪

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q18

  Consider the following recursive method.

{% raw %}
  ```java
  public static int mystery(int x)
  {
      if (x <= 0)
      {
          return 5;
      }
      else
      {
          return x + mystery(x - 2);
      }
  }
  ```
{% endraw %}

  What is returned as a result of the method call `mystery(5)`?

  (A) 8  
  (B) 13  
  (C) 14  
  (D) 20

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    逐层展开：`mystery(5)` = 5 + `mystery(3)`；`mystery(3)` = 3 + `mystery(1)`；`mystery(1)` = 1 + `mystery(-1)`；`mystery(-1)` 触发基础情况返回 5。回代：1 + 5 = 6 → 3 + 6 = 9 → 5 + 9 = 14。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 递归重建字符串

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q21

  Consider the following recursive method.

{% raw %}
  ```java
  public static String doSomething(String str)
  {
      if (str.length() < 1)
      {
          return "";
      }
      else
      {
          return str.substring(0, 1) + doSomething(str.substring(1));
      }
  }
  ```
{% endraw %}

  Assume that myString is a properly declared and initialized String object. Which of the following best describes the result of the call `doSomething(myString)`?

  (A) The method call returns a String containing the contents of myString unchanged.  
  (B) The method call returns a String containing the contents of myString with the order of the characters reversed from their order in myString.  
  (C) The method call returns a String containing all but the first character of myString.  
  (D) The method call returns a String containing only the first and second characters of myString.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    每次递归取第一个字符拼在前面，再对剩余部分递归。由于每次都是"首字符 + 剩余递归结果"，字符顺序保持不变，最终把整个字符串**原样重建**。正确答案是 **(A)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 递归结构           | 基础情况 + 递归情况                          | 基础情况必须能终止递归                         |
| 逐层追踪           | 展开调用 → 最内层返回 → 逐层回代             | 注意每层参数变化                               |
| 独立局部变量       | 每次调用有自己的参数与局部变量               | 不同调用层变量互不影响                         |
| 递归 ↔ 迭代        | 任何递归都可改写为循环，反之亦然             | 递归是另一种形式的重复                         |
| 除零陷阱           | 递归过程中可能产生 % 0                       | 检查基础情况是否覆盖所有情况                   |
| 返回值组合         | 加法/拼接等                                  | mystery(5) = 5+3+1+5 = 14                      |
| 字符串递归         | 首字符 + 剩余递归 → 原样重建                 | 若改为 剩余 + 首字符 才反转                    |
| 考试范围           | 只考追踪递归结果，不考编写递归               | Exclusion：Writing recursive code              |
