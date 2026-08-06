---
layout: default
title: 2.3 if Statements
parent: Unit 2
nav_order: 3
---

# 2.3 — if Statements

## 2.3.A if / else if / else 语句

**if 语句**根据布尔条件决定是否执行某段代码：

{% raw %}
```java
if (条件) {
    // 条件为 true 时执行
} else if (另一条件) {
    // 第一个条件为 false 且第二个为 true 时执行
} else {
    // 所有条件均为 false 时执行
}
```
{% endraw %}

{: .note}
> - **选择语句（selection statements）**改变语句的**顺序执行**流程——if 语句是其中一种。
> - **单路选择（one-way selection，if）**：只有条件为 true 时执行指定代码段。
> - **双路选择（two-way selection，if-else）**：条件为 true 执行一段，为 false 执行另一段。
> - 独立的 `if` 语句会**依次检查**所有条件；`if-else if` 链在某个条件满足后会**跳过**后续分支。

## 2.3.B 用 if 语句实现选择逻辑

- 每个条件独立判断时，注意**条件之间的重叠**：`n >= 10` 和 `n <= 50` 同时成立时两个 if 都会执行。
- 折扣、费用计算等场景常需要"先判条件、再执行操作"的组合。

- ### 例题 1 — 多个独立 if 语句

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q7

  In the following code segment, n is a properly declared and initialized int variable.

{% raw %}
  ```java
  boolean result = false;
  if (n >= 10)
  {
      result = true;
  }
  if (n <= 50)
  {
      result = true;
  }
  System.out.println(result);
  ```
{% endraw %}

  Which of the following best describes the behavior of the code segment?

  (A) It prints true for all possible values of n.  
  (B) It prints false for all possible values of n.  
  (C) It prints true if n is between 10 and 50, inclusive, and prints false otherwise.  
  (D) It prints false if n is between 10 and 50, inclusive, and prints true otherwise.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    两个**独立的 if** 依次执行：n ≥ 10 时 result = true；n ≤ 50 时 result = true。任意整数 n 要么 ≥ 10，要么 ≤ 50（或两者都满足），所以 result 恒为 true。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 条件赋值追踪

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q8

  Consider the following code segment.

{% raw %}
  ```java
  int quant = 20;
  int unitPrice = 4;
  int ship = 8;
  int total;

  if (quant > 10)
  {
      unitPrice = 3;
  }
  if (quant > 20)
  {
      ship = 0;
  }
  total = quant * unitPrice + ship;
  ```
{% endraw %}

  What is the value of `total` after this code segment is executed?

  (A) 20  
  (B) 60  
  (C) 68  
  (D) 88

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    quant = 20：第一个条件 `quant > 10` 为 true，unitPrice 变为 3；第二个条件 `quant > 20` 为 false，ship 保持 8。`total = 20 * 3 + 8 = 68`。正确答案是 **(C)**。

  </details>

- ### 例题 3 — if 中的费用计算

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part A, Q9

  The following code segment is intended to print the total cost of a stay in a room at a particular hotel. The int variable `numNights` represents the length of the stay, in nights, and the double variable `dailyRate` represents the room base cost for each night of the stay. For stays that are longer than five nights, there is a 10% discount applied to the room base cost for all nights during the stay. In addition to the room cost, the hotel charges a $25 resort fee for each night of the stay. The resort fee is not eligible for the 10% discount for stays that are longer than five nights.

  ```java
  int numNights = /* some initial value */;
  double dailyRate = /* some initial value */;
  double totalCost = numNights * dailyRate;
  /* missing code */
  System.out.println(totalCost);
  ```

  Which of the following can be used to replace `/* missing code */` so that the code segment works as intended?

  (A)
{% raw %}
  ```java
  if (numNights > 5)
  {
      totalCost *= 0.9;
      totalCost += (numNights * 25);
  }
  ```
{% endraw %}
  (B)
{% raw %}
  ```java
  if (numNights > 5)
  {
      totalCost *= 0.9;
  }
  totalCost += (numNights * 25);
  ```
{% endraw %}
  (C)
{% raw %}
  ```java
  totalCost += (numNights * 25);
  if (numNights > 5)
  {
      totalCost *= 0.9;
  }
  ```
{% endraw %}
  (D)
{% raw %}
  ```java
  totalCost += 25;
  if (numNights > 5)
  {
      totalCost *= 0.9;
  }
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    折扣只针对房费（`totalCost *= 0.9` 应发生在加度假费**之前**），度假费 $25/晚对所有住宿都收取且不打折。选项 (B)：先对房费打 9 折（若超过 5 晚），再把度假费加到 totalCost（不受折扣影响）。选项 (A) 把度假费也放在 if 里，短于 5 晚时漏收度假费；(C)(D) 顺序错误，度假费也享受了折扣或只加了一次。正确答案是 **(B)**。

  </details>

- ### 例题 4 — if-else if 链（天气选择）

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q4

  Consider the following code segment.

{% raw %}
  ```java
  int temp = 75;
  String choice;
  boolean hasSibling = false;

  if (temp < 70)
  {
      choice = "Indoors";
  }
  else
  {
      choice = "Outdoors";
  }
  if (hasSibling)
  {
      choice += " with sibling";
  }
  ```
{% endraw %}

  What is the value of choice after executing the code segment?

  (A) "Indoors"  
  (B) "Outdoors"  
  (C) "Indoors with sibling"  
  (D) "Outdoors with sibling"

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `75 < 70` 为 false，走 else 分支：choice = "Outdoors"。`hasSibling` 为 false，第二个 if 不执行。最终 choice 为 "Outdoors"。正确答案是 **(B)**。

  </details>

- ### 例题 5 — if-else if 与折扣叠加

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q23

  Consider the following code segment.

{% raw %}
  ```java
  double regularPrice = 100.0;
  boolean onClearance = true;
  boolean hasCoupon = false;

  double finalPrice = regularPrice;
  if (onClearance)
  {
      finalPrice -= finalPrice * 0.25;
  }
  if (hasCoupon)
  {
      finalPrice -= 5.0;
  }
  System.out.println(finalPrice);
  ```
{% endraw %}

  What is printed as a result of executing the code segment?

  (A) 20.0  
  (B) 25.0  
  (C) 70.0  
  (D) 75.0

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    finalPrice 初始为 100.0。`onClearance` 为 true：finalPrice = 100.0 − 100.0 × 0.25 = 75.0。`hasCoupon` 为 false，第二个 if 不执行。输出 75.0。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                     |
| ---------------- | -------------------------------------------- | -------------------------------------------- |
| if 语句结构      | `if` / `else if` / `else`                    | 条件满足后 else if 链跳过后续分支            |
| 独立 if vs 链    | 独立 if 依次全部判断；链只执行第一个满足的   | n ≥ 10 与 n ≤ 50 两个独立 if 恒真            |
| 变量追踪         | 逐个执行语句，记录变量变化                   | 注意条件边界（> 与 >=）                      |
| 费用/折扣计算    | 先折扣后加费；折扣不能作用于度假费           | 操作的顺序影响最终结果                       |
