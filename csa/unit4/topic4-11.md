---
layout: default
title: 4.11 2D Array Creation and Access
parent: Unit 4
nav_order: 11
---

# 4.11 — 2D Array Creation and Access

## 4.11.A 二维数组的创建

**二维数组（2D Array）** 是"数组的数组"，用两个方括号访问元素：`table[行][列]`。

{% raw %}
```java
int[][] table = {{9, 8, 7}, {6, 5, 4}, {3, 2, 1}};   // 3 行 3 列
int[][] board = new int[5][4];                        // 5 行 4 列
```
{% endraw %}

{: .important}
> - `table.length` 是**行数**（第一维长度）。
> - `table[0].length` 是**列数**（第二维长度）。
> - 行索引和列索引都从 **0** 开始。
> - 总元素数 = `arr.length * arr[0].length`（行数 × 列数）。
> - 用 `new` 创建二维数组时，所有元素初始化为**默认值**：int → 0，double → 0.0，boolean → false，引用类型 → null。
> - 二维数组可以存储**基本类型**或**对象引用**。

{: .note}
> **Exclusion Statement：** **非矩形（Nonrectangular）二维数组**（每行列数不同的 2D 数组）不在 AP CSA 考试范围内。

## 4.11.B 二维数组的访问

```java
table[2][1]   // 第 3 行第 2 列的元素
```

初始化列表 {% raw %}`{{r0c0, r0c1, ...}, {r1c0, ...}, ...}`{% endraw %} 中，外层花括号的每个元素是一个**行**。

- ### 例题 1 — 行列索引

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q1

  Consider the following code segment.

  {% raw %}
  ```java
  int[][] table = {{9, 8, 7}, {6, 5, 4}, {3, 2, 1}};
  System.out.println(table[2][1]);
  ```
  {% endraw %}

  What value is printed as a result of executing the code segment?

  (A) 2  
  (B) 3  
  (C) 4  
  (D) 6

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `table[2][1]`：第一个方括号是**行索引**（第 3 行 {3, 2, 1}），第二个方括号是**列索引**（该行第 2 个元素）。第 3 行第 2 个元素是 2。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 行列奇偶性质

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q2

  Consider the following code segment, which is intended to create and initialize the two-dimensional array num so that columns with an even index will contain only even integers and columns with an odd index will contain only odd integers.

  ```java
  int[][] num = /* missing code */;
  ```

  Which of the following initialization lists could replace `/* missing code */` so that the code segment will work as intended?

  (A) {% raw %}{{0, 1, 2}, {4, 5, 6}, {8, 3, 6}}{% endraw %}  
  (B) {% raw %}{{1, 2, 3}, {3, 4, 5}, {5, 6, 7}}{% endraw %}  
  (C) {% raw %}{{2, 1, 4}, {5, 2, 3}, {2, 7, 1}}{% endraw %}  
  (D) {% raw %}{{2, 4, 6}, {1, 3, 5}, {6, 4, 2}}{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (A)：列 0（偶数索引）含 0、4、8（全偶数）；列 1（奇数索引）含 1、5、3（全奇数）；列 2（偶数索引）含 2、6、6（全偶数）。符合要求。其他选项某列混有奇偶。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 总元素个数

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q3

  The following method is intended to return the total number of elements in the 2D array arr. The method does not work as intended.

{% raw %}
  ```java
  public int totalElements(int[][] arr)
  {
      return arr.length * arr.length;   // Line 3
  }
  ```
{% endraw %}

  Which of the following changes can be made so that the code segment works as intended?

  (A) Changing line 3 to `return (arr.length - 1) * (arr.length - 1);`  
  (B) Changing line 3 to `return arr.length + arr.length;`  
  (C) Changing line 3 to `return (arr.length - 1) * (arr[0].length - 1);`  
  (D) Changing line 3 to `return arr.length * arr[0].length;`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `arr.length` 是行数，`arr[0].length` 是列数。总元素数 = **行数 × 列数** = `arr.length * arr[0].length`。原代码用 `arr.length * arr.length` 把行数乘自己，错误。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 二维数组结构     | 数组的数组：`table[行][列]`                  | 外层 { } 每个元素是一行                       |
| 行列索引         | 行、列都从 0 开始                            | table[2][1] 是第 3 行第 2 列                   |
| 行数列数         | `arr.length` = 行数，`arr[0].length` = 列数  | 总元素 = 行数 × 列数                           |
| 初始化列表       | 每行一个花括号                                | 检查每列数值是否符合要求                       |
