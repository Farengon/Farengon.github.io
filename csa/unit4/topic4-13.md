---
layout: default
title: 4.13 Implementing 2D Array Algorithms
parent: Unit 4
nav_order: 13
---

# 4.13 — Implementing 2D Array Algorithms

## 4.13.A 二维数组算法

在二维数组上实现算法时，关键是**明确遍历的维度**：

- **按行判断**：固定行 r，遍历该行的所有列。
- **行列变换**：把 `mat[r][c]` 复制到新位置（如倒序行）。
- **条件累加/判断**：逐元素检查条件。

{: .note}
> "该行所有元素都为正"的判断模式：先假设全正（初始值 `true`），一旦发现非正元素就改为 `false`。

## 4.13.B 常见模式

| 模式               | 关键写法                                   |
| ------------------ | ------------------------------------------ |
| 行内全正判断       | `allPositive = true`，遇 `<= 0` 改 false   |
| 行倒序复制         | `changedMat[rows - row - 1][col] = mat[row][col]` |
| 行/列求和          | 固定行（列）遍历另一维                     |

{: .note}
> **大纲要求的标准 2D 数组算法（EK 4.13.A.1）：** 利用 2D 数组遍历可以——
> - 求**最小值/最大值**（整个数组或指定行/列/子区域）
> - 计算**和或平均值**（整个数组或指定行/列/子区域）
> - 判断**是否至少有一个元素**具有特定属性
> - 判断**是否所有元素**都具有特定属性
> - 统计具有特定属性的**元素个数**
> - 访问**所有连续元素对**
> - 判断**是否有重复元素**
> - **平移或旋转**某行的元素（左/右）或某列的元素（上/下）
> - **反转**某行或某列元素的顺序

- ### 例题 1 — 行内全正判断

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q7

  The following method is intended to return true if all elements in row `x` of the 2D array nums are positive and false otherwise.

{% raw %}
  ```java
  /**
   * Precondition: x is a valid row index of nums.
   */
  public static boolean allPositiveInRow(int[][] nums, int x)
  {
      boolean allPositive = /* initial value */;
      for (int y = 0; y < nums[0].length; y++)
      {
          if (nums[x][y] <= 0)
          {
              allPositive = /* updated value */;
          }
      }
      return allPositive;
  }
  ```
{% endraw %}

  Which of the following replacements for `/* initial value */` and `/* updated value */` can be used so that the method works as intended?

  (A) Replace `/* initial value */` with true and replace `/* updated value */` with true.  
  (B) Replace `/* initial value */` with true and replace `/* updated value */` with false.  
  (C) Replace `/* initial value */` with false and replace `/* updated value */` with true.  
  (D) Replace `/* initial value */` with false and replace `/* updated value */` with false.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    先假设该行全为正（`allPositive = true`）；一旦发现元素 `<= 0`，就把它改为 `false`。这是"先假设成立、遇反例推翻"的模式。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 行倒序复制

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q8

  Consider the following code segment.

  {% raw %}
  ```java
  int[][] mat = {{1, 2, 3, 4},
                 {1, 2, 3, 4},
                 {5, 6, 7, 8},
                 {5, 6, 7, 8}};

  int numRows = mat.length;
  int numCols = mat[0].length;
  int[][] changedMat = new int[numRows][numCols];

  for (int row = 0; row < numRows; row++)
  {
      for (int col = 0; col < numCols; col++)
      {
          changedMat[numRows - row - 1][col] = mat[row][col];
      }
  }
  ```
  {% endraw %}

  Which of the following represents the contents of changedMat after executing this code segment?

  (A)
{% raw %}
  ```
  {5, 6, 7, 8}
  {5, 6, 7, 8}
  {1, 2, 3, 4}
  {1, 2, 3, 4}
  ```
{% endraw %}
  (B)
{% raw %}
  ```
  {1, 2, 3, 4}
  {5, 6, 7, 8}
  {1, 2, 3, 4}
  {5, 6, 7, 8}
  ```
{% endraw %}
  (C)
{% raw %}
  ```
  {4, 3, 2, 1}
  {4, 3, 2, 1}
  {8, 7, 6, 5}
  {8, 7, 6, 5}
  ```
{% endraw %}
  (D)
{% raw %}
  ```
  {1, 2, 3, 4}
  {1, 2, 3, 4}
  {5, 6, 7, 8}
  {5, 6, 7, 8}
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    赋值目标行是 `numRows - row - 1`：row=0（第 1 行 {1,2,3,4}）复制到第 4 行；row=1 复制到第 3 行；row=2（{5,6,7,8}）复制到第 2 行；row=3 复制到第 1 行。列不变。结果是行的**上下倒序**。正确答案是 **(A)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 行内判断           | 初始 true，遇反例改 false                    | "全部满足"型判断用此模式                       |
| 行列变换           | 目标索引用公式计算                           | 行倒序：rows - row - 1                         |
| 遍历维度           | 固定行遍历列 / 固定列遍历行                  | 明确题目统计的是行还是列                       |
| 逐元素条件         | 检查每个元素的属性                           | 注意索引 x（行）与 y（列）                    |
