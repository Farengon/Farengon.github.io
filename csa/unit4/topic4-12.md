---
layout: default
title: 4.12 2D Array Traversals
parent: Unit 4
nav_order: 12
---

# 4.12 — 2D Array Traversals

## 4.12.A 遍历二维数组

标准遍历用**嵌套 for 循环**：外层遍历行，内层遍历列。

```java
for (int r = 0; r < mat.length; r++)        // 遍历行
{
    for (int c = 0; c < mat[0].length; c++) // 遍历列
    {
        System.out.print(mat[r][c]);
    }
    System.out.println();
}
```

{: .note}
> 增强 for 遍历二维数组：外层遍历每个一维数组（行），内层遍历行内元素。

## 4.12.B 部分遍历（按行/按列规律）

- **奇数行**：外层 `r` 从 1 开始，`r += 2`。
- **三角区域**：内层循环上限依赖外层 `r`（如 `c <= r`）。
- 追踪时**逐行**列出每个元素。

{: .important}
> 内层循环的边界常写成 `num.length`（行数）而**不是** `r.length`（该行长度），当每行列数不同或行数≠列数时会导致错误——正确写法应使用 `r.length`（每行自己的长度）。

- ### 例题 1 — 三角区域输出

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q4

  Consider the following code segment.

  {% raw %}
  ```java
  int[][] mat = {{1, 2, 3, 4},
                 {5, 6, 7, 8},
                 {8, 7, 6, 5},
                 {4, 3, 2, 1}};

  for (int r = 0; r < mat.length; r++)
  {
      /* missing code */
  }
  ```
  {% endraw %}

  This code segment is intended to produce the following output.

  ```
  1
  56
  876
  4321
  ```

  Which of the following can be used to replace `/* missing code */` so that the code segment works as intended?

  (A)
  ```java
  for (int c = 0; c <= r; c++)
  {
      System.out.print(mat[c][r] + " ");
  }
  System.out.println();
  ```
  (B)
  ```java
  for (int c = 0; c <= r; c++)
  {
      System.out.print(mat[r][c] + " ");
  }
  System.out.println();
  ```
  (C)
  ```java
  for (int c = 1; c < r; c++)
  {
      System.out.print(mat[r][c] + " ");
  }
  System.out.println();
  ```
  (D)
  ```java
  for (int c = 0; c <= r; c++)
  {
      System.out.print(mat[r][c] + " ");
  }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    期望输出是每行的**前 r+1 个元素**（三角区域），且要换行。选项 (B)：外层 r 遍历行，内层 c 从 0 到 r，打印 `mat[r][c]`，每行结束 println 换行。r=0 打印 mat[0][0]=1；r=1 打印 mat[1][0]=5、mat[1][1]=6……与期望一致。选项 (A) 访问的是 mat[c][r]（转置）；(C) 起点 1 漏掉首元素；(D) 缺少换行。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 奇数行求和

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q5

  Consider the following code segment.

  ```java
  int[][] board = new int[5][4];
  /* code to initialize board */

  int total = 0;
  for (int r = 1; r < board.length; r += 2)
  {
      for (int c = 0; c < board[0].length; c++)
      {
          total += board[r][c];
      }
  }
  ```

  Which of the following best describes the value of total as a result of executing the code segment?

  (A) It contains the sum of elements in even-numbered rows.  
  (B) It contains the sum of elements in odd-numbered rows.  
  (C) It contains the sum of elements in even-numbered columns.  
  (D) It contains the sum of elements in odd-numbered columns.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    外层 r 从 1 开始、每次 +2，只遍历**奇数索引行**（1、3）；内层遍历该行所有列。total 是所有奇数行的元素和。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 内层边界错误

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q6

  Consider the following method, sumRows, which is intended to traverse all the rows in the two-dimensional (2D) integer array num and print the sum of all the elements in each row.

  ```java
  public static void sumRows(int[][] num)
  {
      for (int[] r : num)
      {
          int sum = 0;
          for (int j = 0; j < num.length; j++)
          {
              sum += r[j];
          }
          System.out.print(sum + " ");
      }
  }
  ```

  For example, if num contains {% raw %}{{3, 5}, {6, 8}}{% endraw %}, then sumRows(num) should print the following.

  ```
  8 14
  ```

  The method does not always work as intended.

  For which of the following two-dimensional array input values does sumRows not work as intended?

  (A) {% raw %}{{10, -18}, {48, 17}}{% endraw %}  
  (B) {% raw %}{{-5, 2, 0}, {4, 11, 0}}{% endraw %}  
  (C) {% raw %}{{4, 1, 7}, {-10, -11, -12}}{% endraw %}  
  (D) {% raw %}{{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    内层循环上限写的是 `num.length`（**行数**），而应使用 `r.length`（每行自己的长度）。选项 (C) 有 2 行、每行 3 个元素：内层只迭代 2 次（j=0,1），每行只加前两个元素，漏掉第三个，输出错误。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 修改条件（行 vs 列）

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q9

  In the following code segment, board is a properly declared and initialized 2D array of int values.

  ```java
  int sum = 0;
  for (int r = 0; r < board.length; r++)      // Line 2
  {
      for (int c = 0; c < board[0].length; c++)  // Line 4
      {
          if (c % 2 != 0)                      // Line 6
          {
              sum += board[r][c];              // Line 8
          }
      }
  }
  ```

  The code segment is intended to compute the sum of all elements in all rows that have odd-numbered row indices. However, the code segment is not working as intended. Which of the following changes can be made so that the code segment works as intended?

  (A) Changing line 2 to `for (int r = 0; r < board.length; r += 2)`  
  (B) Changing line 4 to `for (int c = 1; c < board[0].length; c += 2)`  
  (C) Changing line 6 to `if (r % 2 != 0)`  
  (D) Changing line 8 to `sum += board[c][r];`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    题目要求统计**奇数索引行**的所有元素，但第 6 行判断的是 `c % 2 != 0`（奇数列）。应改为判断行索引：`if (r % 2 != 0)`。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 标准遍历           | 外层行、内层列                               | mat[r][c]，r 行 c 列                           |
| 内层边界           | 用 `r.length`（每行长度）而非 num.length      | 行列数不同时会出错                             |
| 部分遍历           | r 从 1 起 += 2 → 奇数行；c <= r → 三角区域    | 逐行列出元素追踪                               |
| 条件位置           | 判断行条件用 r，判断列条件用 c                | 意图与代码要匹配                               |
| 换行输出           | 每行结束 println()                            | 漏掉换行输出格式错误                           |
