---
layout: default
title: 4.9 ArrayList Traversals
parent: Unit 4
nav_order: 9
---

# 4.9 — ArrayList Traversals

## 4.9.A ArrayList 的遍历

遍历 ArrayList 使用 `size()` 和 `get(i)`：

```java
for (int i = 0; i < list.size(); i++)
{
    System.out.println(list.get(i));
}
```

也可以使用增强 for：

```java
for (Integer num : list) { ... }
```

{: .note}
> 增强 for 循环中的变量是元素的**副本**，修改它不会改变 ArrayList。

{: .important}
> **遍历时的异常（EK 4.9.A.3/A.4）：**
> - 访问**超出范围**的索引会抛 **IndexOutOfBoundsException**（如 `get(size())`、`remove(size())`）。
> - 在**增强 for 循环**遍历 ArrayList 时**添加或删除元素**会抛 **ConcurrentModificationException**——因此增强 for 中不能增删元素，删除应用标准 for 循环并小心处理索引。

## 4.9.B 遍历时删除元素的陷阱

{: .important}
> **遍历时删除元素**是经典陷阱：`remove(i)` 后，后续元素**前移一位**，若 i 继续递增，会**跳过**一个元素（尤其是相邻的相同元素）。解决方法：删除后 i 减 1（`i--`），或**从后往前遍历**。

- ### 例题 1 — 删除负数（修正版）

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q12

  In the following code segment, numbers is a properly declared ArrayList variable that has been initialized with the following values.

  ```
  [13, 2, -4, 0, 34, -12, -13, 18, -27]
  ```

  ```java
  for (int i = 0; i < numbers.size(); i++)   // Line 1
  {
      if (numbers.get(i) < 0)
      {
          numbers.remove(i);
      }                                      // Line 6
      i--;                                   // Line 7
  }
  ```

  The code segment is intended to remove all negative values from numbers. However, the code segment is not working as intended.

  Which of the following changes can be made so that the code segment works as intended?

  (A) In line 1, changing `i < numbers.size()` to `i < numbers.size() - 1`  
  (B) In line 7, changing `i--;` to `i++;`  
  (C) Removing line 7  
  (D) Switching lines 6 and 7

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    删除元素后，后续元素前移，必须**只在删除发生时**让 i 减 1，然后循环的 i++ 让 i 保持原位置继续检查。当前代码把 `i--` 放在 if 外，每轮都执行（相当于 i 永远不前进，无限循环）。把 `i--` 移到 if 内部（交换 6、7 行）即可。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 按索引步长遍历

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q13

  In the following code segment, intList is properly declared and initialized as an `ArrayList<Integer>` variable.

  ```java
  int someVal = 0;
  for (int i = 0; i < intList.size(); i += 2)
  {
      someVal++;
  }
  System.out.println(someVal);
  ```

  Which of the following best describes the value printed as a result of executing the code segment?

  (A) The sum of all the elements in intList  
  (B) The number of elements in intList  
  (C) The number of even values in intList  
  (D) The number of elements in even-numbered indexes in intList

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环从索引 0 开始，每次 +2，只统计**偶数索引**（0、2、4...）的数量，并不访问元素内容。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 相邻负数删除失败

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q15

  In the following code segment, numbers is a properly declared and initialized `ArrayList` variable.

  ```java
  for (int i = 0; i < numbers.size(); i++)
  {
      if (numbers.get(i) < 0)
      {
          numbers.remove(i);
      }
  }
  ```

  The code segment is intended to remove all negative values from numbers. Which of the following best describes the conditions in which the code segment works as intended?

  (A) The code segment works as intended for all possible contents of numbers.  
  (B) The code segment works as intended only when negative numbers are not in adjacent positions in numbers.  
  (C) The code segment works as intended only when numbers is sorted.  
  (D) The code segment works as intended only when there are no duplicate values in numbers.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    删除元素后剩余元素前移，i 继续 +1 会跳过刚移过来的元素。若两个负数**相邻**，第一个被删后第二个移到当前位置，但 i 已 +1，第二个被跳过，残留负数。只有负数不相邻时才能全部删除。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 求平均值

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q19

  Consider the following code segment.

  ```java
  double x = 0.0;
  for (double number : numbers)
  {
      x += number;
  }
  System.out.println(x / numbers.size());
  ```

  Assume that numbers is an ArrayList that has been initialized with the following Double objects.

  ```
  [10.0, 20.0, 30.0, 40.0, 100.0]
  ```

  What is printed as a result of executing the code segment?

  (A) 20.0  
  (B) 30.0  
  (C) 40.0  
  (D) 200.0

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    增强 for 累加所有元素：10+20+30+40+100 = 200；再除以 size()（5）得 40.0，即平均值。正确答案是 **(C)**。

  </details>

- ### 例题 5 — 相邻长度统计

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q20

  In the following code segment, words is an ArrayList of two or more String objects.

  ```java
  int prev = words.get(0).length();
  int count = 0;

  for (int j = 1; j < words.size(); j++)
  {
      int curr = words.get(j).length();
      if (curr == prev)
      {
          count += 1;
      }
      prev = curr;
  }
  ```

  Which of the following best describes the value assigned to count as a result of executing the code segment?

  (A) The number of elements in words whose length is the same length as the first element.  
  (B) The number of elements in words whose length is the same length as the element immediately preceding it.  
  (C) The number of elements in words whose value is equal to the first element.  
  (D) The number of elements in words whose value is equal to the element immediately preceding it.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环把每个元素的长度与**前一个元素**的长度比较（prev 每轮更新为 curr），统计长度与前一元素相同的元素个数。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 遍历语法           | `list.size()` + `list.get(i)`                | 也可以用增强 for（只读）                       |
| 删除陷阱           | remove 后元素前移，i 要调整                  | 相邻相同元素会被跳过                           |
| 删除修正           | 删除时 i--，或从后往前遍历                   | 注意 i-- 的位置（应只在删除时）                |
| 按步长遍历         | `i += 2` 统计偶数索引                        | 与元素值无关                                   |
| 平均值/相邻比较    | 累加后除以 size()；比较相邻元素              | prev 每轮更新                                  |
