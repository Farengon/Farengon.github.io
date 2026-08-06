---
layout: default
title: 4.14 Searching Algorithms
parent: Unit 4
nav_order: 14
---

# 4.14 — Searching Algorithms

## 4.14.A 线性查找（Linear Search）

**线性查找** 从数组一端开始，逐个比较元素直到找到目标：

{% raw %}
```java
public static int linearSearch(int[] arr, int value)
{
    for (int j = 0; j < arr.length; j++)
    {
        if (arr[j] == value)
        {
            return j;      // 找到，返回索引
        }
    }
    return -1;             // 没找到，返回 -1
}
```
{% endraw %}

{: .important}
> - 线性查找返回**第一个**匹配元素的索引；找不到返回 **-1**。
> - 若从**后往前**遍历，返回的是**最后一个**匹配元素的索引。
> - 遍历方向改变不影响"找到/未找到"，只影响返回的是第一个还是最后一个。

## 4.14.B 部分范围查找

有时只查找数组的**一部分**（如后半部分）。追踪时注意循环的起止索引和返回时机。

## 4.14.C 在 2D 数组上应用线性查找

对**二维数组**应用线性查找时，需要**先访问每一行**，再对每一行应用线性查找（逐行搜索）：

{% raw %}
```java
// 在 2D 数组中线性查找目标值（返回是否找到）
public static boolean search2D(int[][] arr, int target)
{
    for (int r = 0; r < arr.length; r++)        // 逐行访问
    {
        for (int c = 0; c < arr[r].length; c++) // 对该行应用线性查找
        {
            if (arr[r][c] == target)
            {
                return true;
            }
        }
    }
    return false;
}
```
{% endraw %}

{: .note}
> 2D 数组的线性查找 = **外层循环逐行 + 内层循环逐元素**（每行都做一次线性查找）。

- ### 例题 4 — 2D 数组中的线性查找

  > **Source:** 大纲 EK 4.14.A.2 改编

  在二维数组 {% raw %}`{{3, 1, 4}, {1, 5, 9}}`{% endraw %} 中查找值 5。追踪逐行线性查找：

  - 第 1 行（r=0）：检查 3、1、4——都不是 5。
  - 第 2 行（r=1）：检查 1（不是）、5（**找到**）→ 返回 true。

  若查找值 7：第 1 行检查完没有，第 2 行检查 1、5、9 都没有 → 返回 false。

- ### 例题 1 — 后半部分查找

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q10

  Consider the following method.

{% raw %}
  ```java
  public static int findTarget(int[] nums, int target)
  {
      int answer = -1;
      for (int j = nums.length - 1; j >= nums.length / 2; j--)
      {
          if (nums[j] == target)
          {
              answer = j;
          }
      }
      return answer;
  }
  ```
{% endraw %}

  The following code segment appears in another method in the same class as findTarget.

{% raw %}
  ```java
  int[] arr = {4, 5, 8, 3, 8, 9, 8, 1};
  System.out.println(findTarget(arr, 8));
  ```
{% endraw %}

  What is printed as a result of executing the code segment?

  (A) 2  
  (B) 4  
  (C) 5  
  (D) 6

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环从数组末尾（索引 7）向前遍历到索引 `length/2` = 4（后半部分：索引 4、5、6、7）。这部分的 8 出现在索引 4 和 6，每次匹配都更新 answer，最后一个匹配（索引 6）被保留……等等：j 从 7 到 4 递减，匹配 8 的索引有 6 和 4。遍历顺序 7→6(匹配,answer=6)→5→4(匹配,answer=4)。最终 answer = 4。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 线性查找第一个匹配

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q11

  Consider the following method.

{% raw %}
  ```java
  public static int someSearch(int[] arr, int value)
  {
      for (int j = 0; j < arr.length; j++)
      {
          if (arr[j] == value)
          {
              return j;
          }
      }
      return -1;
  }
  ```
{% endraw %}

  The following code segment appears in a method in the same class as someSearch.

{% raw %}
  ```java
  int[] myNumbers = {1, 2, 5, 2, 6, 3, 3, 5, 3};
  System.out.println(someSearch(myNumbers, 3));
  ```
{% endraw %}

  What is printed as a result of executing the code segment?

  (A) -1  
  (B) 5  
  (C) 6  
  (D) 8

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    从左到右查找 3：索引 5 处是第一个 3，方法立即 `return 5`。虽然后面还有 3（索引 6、8），但遇到第一个匹配就返回。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 反向查找的影响

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q12

  Consider the method linearSearch, which takes an ArrayList of Integer elements and a target int value as parameters and returns the index of the first appearance of the target value in the list or -1 if the target value does not appear in the list.

{% raw %}
  ```java
  public static int linearSearch(ArrayList<Integer> elements, int target)
  {
      for (int j = 0; j < elements.size(); j++)   // Line 3
      {
          if (elements.get(j) == target)
          {
              return j;
          }
      }
      return -1;
  }
  ```
{% endraw %}

  Which of the following describes how replacing line 3 with `for (int j = (elements.size() - 1); j >= 0; j--)` will affect the behavior of linearSearch?

  (A) The modification has no effect: the modified method will continue to return the index of the first appearance of the target value in the list, or -1 if the target value does not appear in the list.  
  (B) The modified method will return the index of the last appearance of the target value in the list, or -1 if the target value does not appear in the list.  
  (C) The modified method will throw an IndexOutOfBoundsException.  
  (D) The modified method will return -1 regardless of the inputs.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    改为从后往前遍历后，遇到的第一个匹配就是**最后一次出现**的位置，方法返回目标值最后一次出现的索引（找不到仍返回 -1）。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 线性查找         | 逐个比较，返回第一个匹配索引                 | 找不到返回 -1                                  |
| 遍历方向         | 正序→第一个；倒序→最后一个                   | 只影响返回哪个匹配，不影响是否找到             |
| 部分范围查找     | 循环起止索引限定查找范围                     | 追踪后半部分时注意起始索引                     |
| 立即返回         | 找到即 return，不继续遍历                    | 多个匹配时返回最先遇到的                       |
| 2D 数组查找      | 先逐行访问，再对每行线性查找                 | 外层行循环 + 内层元素循环                      |
