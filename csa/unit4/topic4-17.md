---
layout: default
title: 4.17 Recursive Searching and Sorting
parent: Unit 4
nav_order: 17
---

# 4.17 — Recursive Searching and Sorting

## 4.17.A 递归遍历（Recursive Traversals）

**递归（Recursion）** 不仅可以用于数学计算，还可以用来**遍历** `String`、数组和 `ArrayList` 对象——用递归代替循环，逐个访问元素。

```java
// 用递归遍历数组（打印每个元素）
public static void traverse(int[] arr, int index)
{
    if (index >= arr.length)          // 基础情况：遍历完毕
    {
        return;
    }
    System.out.println(arr[index]);
    traverse(arr, index + 1);         // 递归调用：访问下一个元素
}
```

{: .note}
> 递归遍历的关键：**基础情况**（索引越界时停止）+ **递归调用**（参数推进，如 `index + 1`）。参数值记录遍历进度，就像循环控制变量记录循环进度一样。

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

## 4.17.B 二分查找（Binary Search）

**二分查找（Binary Search）** 是一种在**有序**（sorted）数组或 `ArrayList` 中查找目标的高效算法：

{: .important}
> **使用二分查找的前提：数据必须已经有序（升序或降序）！**

**算法过程：**

1. 从集合的**中间元素**开始比较。
2. 若中间元素 == 目标值，查找成功。
3. 若目标值 **小于** 中间元素，则在**左半部分**继续查找。
4. 若目标值 **大于** 中间元素，则在**右半部分**继续查找。
5. 每轮都**排除一半**元素，直到找到目标或区间为空。

```java
// 递归版二分查找：在 [low, high] 区间内查找 target
public static int binarySearch(int[] arr, int target, int low, int high)
{
    if (low > high)                    // 基础情况：区间为空，未找到
    {
        return -1;
    }
    int mid = (low + high) / 2;        // 中间索引
    if (arr[mid] == target)
    {
        return mid;
    }
    else if (target < arr[mid])
    {
        return binarySearch(arr, target, low, mid - 1);   // 找左半部分
    }
    else
    {
        return binarySearch(arr, target, mid + 1, high);  // 找右半部分
    }
}
```

{: .note}
> - **效率**：二分查找每次排除一半元素，**通常比线性查找更高效**（线性查找要逐个检查）。
> - 二分查找可以用**递归**实现，也可以用**循环（迭代）**实现，两者等价。
> - 大纲只要求**线性查找**和**二分查找**两种搜索算法，其他搜索算法不在考试范围内。

- ### 例题 3 — 二分查找的迭代追踪

  二分查找在有序数组 `{2, 5, 8, 12, 16, 23, 38, 56, 72, 91}` 中查找目标值 23。

  模拟过程（数组长度 10，索引 0–9）：

  - 第 1 轮：low=0, high=9，mid = (0+9)/2 = 4 → arr[4] = 16。23 > 16 → 查找右半部分。
  - 第 2 轮：low=5, high=9，mid = (5+9)/2 = 7 → arr[7] = 56。23 < 56 → 查找左半部分。
  - 第 3 轮：low=5, high=6，mid = (5+6)/2 = 5 → arr[5] = 23。**找到！**返回索引 5。

  只需 **3 轮**就找到目标，而线性查找需要 6 次比较——体现了二分查找的效率优势。

---

## 4.17.C 归并排序（Merge Sort）

**归并排序（Merge Sort）** 是一种**递归排序算法**，可以对数组或 `ArrayList` 排序。它采用**分治法（divide and conquer）**：

1. **分解（Divide）**：把数组从中间分成两半，递归地对两半分别排序。
2. **合并（Merge）**：把两个已排序的子数组合并成一个有序数组。

```java
// 归并排序主方法：排序 arr 的 [low, high] 区间
public static void mergeSort(int[] arr, int low, int high)
{
    if (low < high)
    {
        int mid = (low + high) / 2;
        mergeSort(arr, low, mid);          // 递归排序左半部分
        mergeSort(arr, mid + 1, high);     // 递归排序右半部分
        merge(arr, low, mid, high);        // 合并两个有序部分
    }
}
```

**合并过程（merge）**：用两个指针分别遍历左右两个有序子数组，每次取较小者放入临时数组，最后把剩余元素和临时结果复制回原数组。

{: .note}
> - 大纲要求掌握**选择排序、插入排序、归并排序**三种排序算法（其他排序算法不在考试范围内）。
> - 归并排序是**递归**算法；选择排序和插入排序是**迭代**算法。
> - 需要能追踪每一轮迭代/递归的结果。

- ### 例题 4 — 归并排序过程追踪

  对数组 `{38, 27, 43, 3, 9, 82, 10}` 进行归并排序，追踪分解与合并过程：

  **分解（不断对半切分，直到每个子数组只有一个元素）：**

  ```
  [38, 27, 43, 3, 9, 82, 10]
  ├── [38, 27, 43]          └── [3, 9, 82, 10]
  │   ├── [38]  [27, 43]         ├── [3, 9]  [82, 10]
  │   │        ├── [27] [43]     │    ├── [3] [9]   ├── [82] [10]
  ```

  **合并（自底向上，把有序子数组合并）：**

  ```
  [27, 43] 合并 → [27, 43]；[3] [9] → [3, 9]；[82] [10] → [10, 82]
  [38] + [27, 43] → [27, 38, 43]；[3, 9] + [10, 82] → [3, 9, 10, 82]
  [27, 38, 43] + [3, 9, 10, 82] → [3, 9, 10, 27, 38, 43, 82]
  ```

  最终数组有序：`{3, 9, 10, 27, 38, 43, 82}`。

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 递归遍历           | 递归可遍历 String、数组、ArrayList           | 基础情况 + 参数推进                            |
| 二分查找前提       | 数据必须**有序**                             | 无序数据不能用二分查找                         |
| 二分查找过程       | 从中间开始，每轮排除一半                     | 追踪每轮的 low/high/mid                        |
| 二分查找效率       | 比线性查找更高效                             | 递归与迭代实现等价                             |
| 归并排序           | 递归排序：分解 + 合并                        | 掌握每轮分解/合并的结果                        |
| 搜索/排序范围     | 只考线性、二分查找；选择、插入、归并排序     | 其他算法不在考试范围内                         |
