---
layout: default
title: 4.17 Recursive Searching and Sorting
parent: Unit 4
nav_order: 17
---

# 4.17 — Recursive Searching and Sorting

## 4.17.A 递归查找

递归实现线性查找时，把"在 [start, end] 范围查找"分解为：

```java
public static int locateItem(int[] arr, int goal, int start, int end)
{
    if (start > end)                      // 基础情况：范围为空
    {
        return -1;
    }
    else if (arr[start] == goal)          // 找到目标
    {
        return start;
    }
    else
    {
        return locateItem(arr, goal, start + 1, end);   // 缩小范围继续找
    }
}
```

{: .important}
> - 基础情况必须覆盖"目标在**最后一个位置**"的情况——范围边界要正确处理（如 `start > end` 而非 `start == end`）。
> - 递归查找与循环查找逻辑等价，注意返回值的语义。

## 4.17.B 递归中的条件判断

递归方法中常用 if-else 分支：满足条件更新状态并递归，不满足则走另一分支。追踪时逐层记录状态变化。

- ### 例题 1 — 递归查找的范围边界

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q19

  The following recursive method is intended to return the index of the first occurrence of goal in arr between index start and index end, inclusive. The index of the first occurrence of goal is the index closest to start where goal is found. If goal does not appear in the range of indices from start to end, the method returns -1. However, the method does not work as intended.

  ```java
  /** Precondition: 0 <= start <= end, end < arr.length */
  public static int locateItem(int[] arr, int goal, int start, int end)
  {
      if (start == end)                    // Line 4
      {
          return -1;
      }
      else if (arr[start] == goal)         // Line 8
      {
          return start;                    // Line 10
      }
      else
      {
          return locateItem(arr, goal, start + 1, end);   // Line 14
      }
  }
  ```

  Which of the following changes can be made so that the method works as intended?

  (A) Changing line 4 to `if (start > end)`  
  (B) Changing line 8 to `else if (start == goal)`  
  (C) Changing line 10 to `return arr[start];`  
  (D) Changing line 14 to `return locateItem(arr, goal, start + 1, end + 1);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    原方法在 `start == end` 时直接返回 -1，即使 `arr[start]` 就是目标，也永远**不会检查最后一个位置**。把条件改为 `start > end` 后，`start == end` 时会先检查 `arr[start] == goal`，正确覆盖最后一个位置。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 递归记录变化点

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q20

  Consider the following method.

  ```java
  public static void find(String[] words, int s, int i)
  {
      if (i != words.length)
      {
          if (i == 0 || !(words[s].equals(words[i])))
          {
              s = i;
              System.out.print(s + " ");
          }
          find(words, s, i + 1);
      }
  }
  ```

  The following code segment appears in a method in the same class as find.

  ```java
  String[] furniture = /* missing initialization */;
  find(furniture, 0, 0);
  ```

  Which of the following can be used to replace `/* missing initialization */` so that the code segment prints `0 1 4 6 7`?

  (A) {"Stool", "Chair", "Chair", "Chair", "Stool", "Couch", "Couch", "Table"}  
  (B) {"Table", "Couch", "Couch", "Stool", "Chair", "Chair", "Chair", "Stool"}  
  (C) {"Stool", "Chair", "Chair", "Chair", "Couch", "Couch", "Stool", "Table"}  
  (D) {"Table", "Stool", "Couch", "Couch", "Chair", "Chair", "Chair", "Stool"}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    i=0 时总是打印 0 并 s=0。之后每次 words[i] 与 words[s] **不同**时更新 s 并打印。打印 "0 1 4 6 7" 意味着变化点索引为 1、4、6、7。选项 (C)：索引 0 "Stool"，索引 1 "Chair"（不同，打印 1）；索引 2、3 都是 "Chair"（相同）；索引 4 "Couch"（不同，打印 4）；索引 5 "Couch"（相同）；索引 6 "Stool"（不同，打印 6）；索引 7 "Table"（不同，打印 7）。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 递归查找           | 基础情况 + 缩小范围递归                      | 边界条件 `start > end` 覆盖最后一个位置        |
| 返回值语义         | 返回索引或 -1                                | 递归与循环等价                                 |
| 递归条件分支       | 条件满足更新状态并继续递归                   | 逐层记录 s、i 变化                             |
| 边界修正           | 基础情况不能提前返回而漏检                   | start == end 时也要检查目标                    |
