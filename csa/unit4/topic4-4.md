---
layout: default
title: 4.4 Array Traversals
parent: Unit 4
nav_order: 4
---

# 4.4 — Array Traversals

## 4.4.A 标准 for 循环遍历

**遍历（Traversal）** 是逐个访问数组中每个元素的过程：

{% raw %}
```java
for (int i = 0; i < arr.length; i++)
{
    System.out.println(arr[i]);
}
```
{% endraw %}

{: .important}
> - 用 `arr.length` 作为循环上限，避免越界。
> - 标准 for 循环可以**读取**，也可以**修改**数组元素。

## 4.4.B 增强 for 循环（Enhanced for / for-each）

{% raw %}
```java
for (int value : arr)
{
    System.out.println(value);
}
```
{% endraw %}

{: .important}
> - 增强 for 循环变量是数组元素的**副本**：**修改 value 不会改变数组元素**！
> - 增强 for 循环适用于**读取**，不适用于修改元素。
> - **对象引用数组的特例**：若数组存的是**对象引用**，通过增强 for 循环变量**调用方法修改对象属性**是可行的——这改变的是对象内部状态，不改变数组里存的引用本身（EK 4.4.A.5）。
> - 增强 for 遍历可以改写为索引 for 或 while 循环（反之亦然）。

## 4.4.C 常见遍历模式

- 求和/求平均：累加所有元素。
- 统计满足条件的元素个数。
- 按索引规律遍历（如 `i += 2` 访问偶数索引）。

- ### 例题 1 — 从后向前赋值

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q11

  The following code segment is intended to set the array numbers to {10, 20, 30, 40}.

  ```java
  int[] numbers = new int[4];
  /* missing code */
  ```

  Which of the following can replace `/* missing code */` so that the code segment will work as intended?

  (A)
{% raw %}
  ```java
  int x = 10;
  for (int value : numbers)
  {
      value = x;
      x += 10;
  }
  ```
{% endraw %}
  (B)
{% raw %}
  ```java
  for (int j = 0; j < numbers.length; j++)
  {
      numbers[j] = j * 10;
  }
  ```
{% endraw %}
  (C)
{% raw %}
  ```java
  numbers[0] = 10;
  for (int j = 0; j < numbers.length; j++)
  {
      numbers[j] = numbers[j] + 10;
  }
  ```
{% endraw %}
  (D)
{% raw %}
  ```java
  numbers[3] = 40;
  for (int j = numbers.length - 1; j > 0; j--)
  {
      numbers[j - 1] = numbers[j] - 10;
  }
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (D)：先设 numbers[3] = 40；然后 j=3 时 numbers[2] = 40−10 = 30；j=2 时 numbers[1] = 30−10 = 20；j=1 时 numbers[0] = 20−10 = 10。结果 {10, 20, 30, 40}。选项 (A) 的增强 for 修改的是副本，数组不变；(B) 得到 {0, 10, 20, 30}；(C) 得到 {20, 10, 10, 10}。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 按步长遍历

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q12

  Consider the following code segment.

{% raw %}
  ```java
  int[] nums = {5, 10, 15, 20, 25, 30};
  for (int k = 0; k < nums.length - 1; k += 2)
  {
      nums[k] = nums[k + 1];
  }
  ```
{% endraw %}

  What are the contents of nums after executing the code segment?

  (A) {5, 5, 15, 15, 25, 25}  
  (B) {10, 10, 20, 20, 25, 30}  
  (C) {10, 10, 20, 20, 30, 30}  
  (D) {10, 15, 20, 25, 30, 30}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    k 取 0、2、4：k=0 时 nums[0] = nums[1] = 10；k=2 时 nums[2] = nums[3] = 20；k=4 时 nums[4] = nums[5] = 30。索引 1、3、5 不变。结果 {10, 10, 20, 20, 30, 30}。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 累积求和遍历

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q13

  Consider the following code segment.

{% raw %}
  ```java
  int[] arr = {10, 20, 30, 40, 50};
  for (int x = 1; x < arr.length - 1; x++)
  {
      arr[x + 1] = arr[x] + arr[x + 1];
  }
  ```
{% endraw %}

  Which of the following represents the contents of arr after the code segment has been executed?

  (A) {10, 20, 50, 90, 50}  
  (B) {10, 20, 50, 90, 140}  
  (C) {10, 30, 60, 100, 50}  
  (D) {10, 30, 60, 100, 150}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    x = 1：arr[2] = 20 + 30 = 50；x = 2：arr[3] = 50 + 40 = 90；x = 3：arr[4] = 90 + 50 = 140。注意 arr[2]、arr[3] 已被更新，后续计算使用更新后的值。结果 {10, 20, 50, 90, 140}。正确答案是 **(B)**。

  </details>

- ### 例题 4 — 增强 for 修改无效

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q15

  Consider the following code segment.

{% raw %}
  ```java
  int[] arr1 = {2, 4, 6, 8, 10};
  int num = 0;
  for (int val : arr1)
  {
      num += 10;
  }
  ```
{% endraw %}

  Which of the following best describes the behavior of the code segment?

  (A) The loop adds 10 to each element in arr1.  
  (B) The loop adds 10 to num once for each element in arr1.  
  (C) The loop adds the value of each element in arr1 to num.  
  (D) The loop does not change the value of num because it uses an enhanced for loop.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    增强 for 循环对 arr1 中**每个元素**迭代一次，每次循环执行 `num += 10`。num 最终为 10 × 5 = 50。循环体没有修改数组元素。正确答案是 **(B)**。

  </details>

- ### 例题 5 — 遍历统计

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q17

  In the following code segment, data is an int array with at least two elements.

{% raw %}
  ```java
  int answer = 0;
  for (int val : data)
  {
      if (data[0] < val)
      {
          answer++;
      }
  }
  System.out.println(answer);
  ```
{% endraw %}

  Which of the following best describes the value printed by the code segment?

  (A) The number of negative elements in data  
  (B) The number of positive elements in data  
  (C) The number of elements in data that are greater than the first element in data  
  (D) The number of elements in data that are less than the first element in data

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    增强 for 循环把每个元素与**第一个元素 data[0]** 比较，统计大于 data[0] 的元素个数。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 标准 for 遍历    | `for (i=0; i<arr.length; i++)`               | 可以读写元素                                   |
| 增强 for 遍历    | `for (类型 变量 : 数组)`                     | 变量是副本，修改无效                           |
| 按步长遍历       | `i += 2` 访问偶数索引                         | 注意循环边界 `length - 1`                      |
| 累积计算         | 后一个元素依赖前一个更新后的值               | 逐轮追踪                                      |
| 遍历统计         | if 条件满足时计数                             | 比较对象是 data[0]                             |
