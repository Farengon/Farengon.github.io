---
layout: default
title: 4.5 Implementing Array Algorithms
parent: Unit 4
nav_order: 5
---

# 4.5 — Implementing Array Algorithms

## 4.5.A 常用数组算法

将循环与数组结合可实现多种算法：

- **填充数组**：如斐波那契数列（每项 = 前两项之和）。
- **反转数组**：交换首尾对称位置的元素（只需遍历一半）。
- **统计/比较**：逐个元素与基准比较计数。
- **复制/变换**：按规则把原数组的值写入新数组。

{: .important}
> 反转数组的标准写法：
> ```java
> for (int k = 0; k < arr.length / 2; k++)
> {
>     int temp = arr[k];
>     arr[k] = arr[arr.length - k - 1];
>     arr[arr.length - k - 1] = temp;
> }
> ```
> 遍历一半即可，否则会反转两次变回原样。

- ### 例题 1 — 斐波那契数列填充

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q14

  The Fibonacci numbers are a sequence of numbers. The first two numbers are 1 and 1. Each subsequent number is equal to the sum of the previous two numbers. For example, the first seven Fibonacci numbers are 1, 1, 2, 3, 5, 8, and 13.

  The following code segment is intended to fill the fibs array with the first ten Fibonacci numbers. The code segment does not work as intended.

  ```java
  int[] fibs = new int[10];
  fibs[0] = 1;
  fibs[1] = 1;
  for (int j = 1; j < fibs.length; j++)
  {
      fibs[j] = fibs[j - 2] + fibs[j - 1];
  }
  ```

  Which of the following best explains why the code segment does not work as intended?

  (A) In the for loop header, the initial value of j should be 0.  
  (B) In the for loop header, the initial value of j should be 2.  
  (C) The for loop condition should be `j < fibs.length - 1`.  
  (D) The for loop condition should be `j < fibs.length + 1`.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    j 从 1 开始时，第一轮访问 `fibs[j - 2]` 即 `fibs[-1]`，索引越界抛异常。前两项已在循环外初始化，循环应从 j = 2 开始，访问 fibs[0] 和 fibs[1] 计算第三项。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 反转数组（边界错误）

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q16

  The following method is intended to return an array with the values of the parameter letters in reverse order. The method does not work as intended.

  ```java
  public static String[] reverseArray(String[] letters)
  {
      String[] revLetters = new String[letters.length];   // Line 3
      for (int x = 0; x < letters.length; x++)            // Line 4
      {
          revLetters[x] = letters[letters.length - x];    // Line 6
      }
      return revLetters;
  }
  ```

  Which of the following changes can be made so the method returns the intended value?

  (A) Changing line 3 to `String[] revLetters = new String[letters.length - 1];`  
  (B) Changing line 4 to `for (int x = 0; x < letters.length - 1; x++)`  
  (C) Changing line 6 to `revLetters[x] = letters[letters.length - x - 1];`  
  (D) Changing line 6 to `letters[x] = revLetters[letters.length - x];`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    x = 0 时 `letters[letters.length - 0]` 即 `letters[letters.length]` 越界。应为 `letters[letters.length - x - 1]`：x=0 取最后一个、x=1 取倒数第二个，以此类推，实现反转。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 反转数组的循环头

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q18

  In the following code segment, assume that the int array numArr has been properly declared and initialized. The code segment is intended to reverse the order of the elements in numArr. For example, if numArr initially contains {1, 3, 5, 7, 9}, it should contain {9, 7, 5, 3, 1} after the code segment executes.

  ```java
  /* missing loop header */
  {
      int temp = numArr[k];
      numArr[k] = numArr[numArr.length - k - 1];
      numArr[numArr.length - k - 1] = temp;
  }
  ```

  Which of the following can be used to replace `/* missing loop header */` so that the code segment works as intended?

  (A) `for (int k = 0; k < numArr.length / 2; k++)`  
  (B) `for (int k = 0; k < numArr.length; k++)`  
  (C) `for (int k = 0; k < numArr.length / 2; k--)`  
  (D) `for (int k = numArr.length - 1; k >= 0; k--)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环体交换首尾对称元素，只需遍历**前半部分**（`k < numArr.length / 2`）。选项 (B) 遍历全部会把数组反转两次变回原样；(C) 的 k-- 会无限循环；(D) 同样会交换两次。正确答案是 **(A)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 斐波那契填充     | 从 j=2 开始，访问 j-2 和 j-1                 | 初始两项先赋值                                 |
| 反转数组         | 遍历一半，交换对称位置                       | 索引对称公式：length - k - 1                   |
| 越界防护         | 访问前检查索引范围                           | letters.length - x 会越界                      |
| 算法追踪         | 逐轮记录数组变化                             | 依赖前一轮更新后的值                           |
