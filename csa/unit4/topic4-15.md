---
layout: default
title: 4.15 Sorting Algorithms
parent: Unit 4
nav_order: 15
---

# 4.15 — Sorting Algorithms

## 4.15.A 选择排序（Selection Sort）

**选择排序** 每轮从未排序部分选出**最小值**，放到已排序部分的末尾：

```java
public static void selectionSort(int[] arr)
{
    for (int j = 0; j < arr.length - 1; j++)
    {
        int minIndex = j;
        for (int k = j + 1; k < arr.length; k++)
        {
            if (arr[k] < arr[minIndex])
            {
                minIndex = k;
            }
        }
        if (j != minIndex)
        {
            int temp = arr[j];
            arr[j] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
}
```

{: .important}
> - 每完成一轮外层循环，**最小/次小**的元素就位一个。
> - 完成 k 轮后，前 k 个位置已经排好。
> - 交换发生在 `j != minIndex` 时（元素已在正确位置则不用交换）。
> - 内层循环遍历到 `arr.length - 1`（包含最后一个元素），写错边界会导致最后一个元素不被处理。

- ### 例题 1 — 两轮排序后的状态

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q13

  The following method is a correct implementation of the selection sort algorithm. The method correctly sorts the elements of arr so that they appear in order from least to greatest.

  ```java
  public static void selectionSort(int[] arr)
  {
      for (int j = 0; j < arr.length - 1; j++)
      {
          int minIndex = j;
          for (int k = j + 1; k < arr.length; k++)
          {
              if (arr[k] < arr[minIndex])
              {
                  minIndex = k;
              }
          }
          int temp = arr[j];
          arr[j] = arr[minIndex];
          arr[minIndex] = temp;
      }
  }
  ```

  Which of the following could be the contents of arr after two passes of the outer loop (i.e., when j = 1 at the point indicated by the end of the outer loop)?

  (A) {10, 20, 50, 40, 30}  
  (B) {10, 30, 50, 40, 20}  
  (C) {20, 10, 50, 40, 30}  
  (D) {20, 30, 50, 40, 10}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选择排序完成两轮后，**最小的两个元素**一定在前两个位置且已排好序。选项 (A) 中前两个位置是 10、20，即原数组 {30, 40, 10, 50, 20} 排序两轮后的状态。选项 (B)(D) 前两个位置 (10,30)、(20,30) 不满足"两个最小元素"；(C) 首元素 20 不是最小值。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 排序的边界错误

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q14

  The following method is intended to sort an array of integers into ascending order.

  ```java
  public static void sort(int[] arr)
  {
      for (int j = 0; j < arr.length - 1; j++)
      {
          int minIndex = j;
          for (int k = j + 1; k < arr.length - 1; k++)   // 注意：k < arr.length - 1
          {
              if (arr[k] < arr[minIndex])
              {
                  minIndex = k;
              }
          }
          int temp = arr[minIndex];
          arr[minIndex] = arr[j];
          arr[j] = temp;
      }
  }
  ```

  This method works as intended for some, but not all, int arrays. Which of the following arrays can be used to show that the method does not work as intended?

  (A) {1, 2, 3, 4, 5}  
  (B) {1, 2, 3, 5, 4}  
  (C) {1, 2, 4, 3, 5}  
  (D) {1, 3, 2, 4, 5}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    内层循环条件写成 `k < arr.length - 1`，导致**最后一个元素永远不被考虑**。选项 (B) {1, 2, 3, 5, 4} 只有最后一个元素 4 不在正确位置，排序时它永远不会被比较，方法无法把它排好，从而证明方法有缺陷。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 交换次数统计

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part C, Q15

  Consider the following correct implementation of the selection sort algorithm.

  ```java
  public static void selectionSort(int[] elements)
  {
      for (int j = 0; j < elements.length - 1; j++)
      {
          int minIndex = j;
          for (int k = j + 1; k < elements.length; k++)
          {
              if (elements[k] < elements[minIndex])
              {
                  minIndex = k;
              }
          }
          if (j != minIndex)
          {
              int temp = elements[j];
              elements[j] = elements[minIndex];
              elements[minIndex] = temp;   // line 17
          }
      }
  }
  ```

  The following declaration and method call appear in a method in the same class as selectionSort.

  ```java
  int[] arr = {30, 40, 10, 50, 20};
  selectionSort(arr);
  ```

  How many times is the statement `elements[minIndex] = temp;` in line 17 of the method executed as a result of the call to selectionSort?

  (A) 2  
  (B) 3  
  (C) 4  
  (D) 5

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    逐轮分析 {30, 40, 10, 50, 20}：① j=0 最小是 10（索引 2），交换 30↔10 → {10,40,30,50,20}（1 次）。② j=1 最小是 20（索引 4），交换 40↔20 → {10,20,30,50,40}（1 次）。③ j=2，minIndex=2（30 已在位），不交换。④ j=3 最小是 40（索引 4），交换 50↔40 → {10,20,30,40,50}（1 次）。共 3 次。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 选择排序过程       | 每轮选最小放前面                             | k 轮后前 k 个已排序                            |
| 排序后状态判断     | 前 k 个位置是最小的 k 个元素                 | 用这个性质反推                               |
| 内层边界           | 必须遍历到 arr.length - 1                    | 边界写错 → 最后一个元素不参与                  |
| 交换次数           | `j != minIndex` 时才交换                     | 元素已在正确位置时不交换                       |
