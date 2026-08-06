---
layout: default
title: 4.3 Array Creation and Access
parent: Unit 4
nav_order: 3
---

# 4.3 — Array Creation and Access

## 4.3.A 数组的创建

**数组（Array）** 是**固定长度**的同类型元素的集合。创建数组：

{% raw %}
```java
int[] sequence = new int[3];   // 长度为 3 的 int 数组，默认值 {0, 0, 0}
String[] names = new String[4]; // 长度为 4 的 String 数组，默认值 {null, null, null, null}
int[] scores = {85, 92, 78};    // 用初始化列表直接赋值
```
{% endraw %}

{: .important}
> - 数组长度**创建后不能改变**。
> - 索引从 **0** 开始，最后一个元素的索引是 `length - 1`。
> - 基本类型数组的默认值：`int` → 0，`double` → 0.0，`boolean` → false；引用类型数组 → `null`。
> - 访问 `array[索引]` 时，索引越界会抛 **ArrayIndexOutOfBoundsException**。

## 4.3.B 数组的访问与修改

```java
sequence[0] = 5;     // 修改索引 0 的元素
int x = sequence[1]; // 读取索引 1 的元素
```

- ### 例题 1 — 数组长度与默认值

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q7

  Consider the following code segment.

  ```java
  /* missing code */
  sequence[1] = 1;
  sequence[2] = 2;
  ```

  Which of the following code segments can be used to replace `/* missing code */` so that the code segment sets the contents of the array to {0, 1, 2}?

  (A) `int[] sequence;`  
  (B) `int[] sequence = new int[1];`  
  (C) `int[] sequence = new int[2];`  
  (D) `int[] sequence = new int[3];`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    需要访问索引 0、1、2，数组长度必须至少为 3。`new int[3]` 创建 {0, 0, 0}，再设置 sequence[1] = 1、sequence[2] = 2，得到 {0, 1, 2}（索引 0 保持默认值 0）。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 数组越界

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q8

  The following code segment is intended to set the contents of the array names to {"Ana", "Billy", "Cathy", "Darius"}. The code segment does not work as intended.

  ```java
  String[] names = new String[3];   // Line 1
  names[0] = "Ana";                 // Line 2
  names[1] = "Billy";               // Line 3
  names[2] = "Cathy";               // Line 4
  names[3] = "Darius";              // Line 5
  ```

  Which of the following changes can be made so that the code segment works as intended?

  (A) Changing line 1 to `String[] names = new String[4];`  
  (B) Changing line 1 to `String[] names = new names[3];`  
  (C) Changing line 5 to `names[2] = "Darius";`  
  (D) Removing line 5

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    长度为 3 的数组索引范围是 0 到 2，访问 names[3] 会抛 `ArrayIndexOutOfBoundsException`。把长度改为 4 就可以存 4 个字符串。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 复合赋值修改元素

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q9

  Consider the following code segment.

{% raw %}
  ```java
  int[] scores = {85, 92, 78, 90, 88};
  scores[1] *= 2;
  scores[2] += 10;
  ```
{% endraw %}

  Which of the following best describes the behavior of lines 2 and 3 in the code segment?

  (A) Line 2 doubles the first element in the array and line 3 adds 10 to the second element.  
  (B) Line 2 doubles the second element in the array and line 3 adds 10 to the third element.  
  (C) Line 2 doubles the third element in the array and line 3 adds 10 to the fourth element.  
  (D) Lines 2 and 3 do not change the contents of the array.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `scores[1] *= 2` 把**索引 1（第二个元素）** 92 翻倍为 184；`scores[2] += 10` 把**索引 2（第三个元素）** 78 加 10 变为 88。正确答案是 **(B)**。

  </details>

- ### 例题 4 — 元素赋值追踪

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q10

  Consider the following code segment.

{% raw %}
  ```java
  int[] arr = {1, 2, 3, 4, 5};
  arr[1] = 4;
  arr[3] = 2;
  ```
{% endraw %}

  Which of the following represents the contents of arr after the code segment has been executed?

  (A) {1, 2, 3, 4, 1}  
  (B) {1, 3, 3, 1, 5}  
  (C) {1, 4, 3, 2, 5}  
  (D) {4, 2, 2, 4, 5}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `arr[1] = 4` 把索引 1（第二个元素）改为 4；`arr[3] = 2` 把索引 3（第四个元素）改为 2。数组变为 {1, 4, 3, 2, 5}。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 数组创建         | `new 类型[长度]` 或初始化列表                | 长度固定，创建后不可变                         |
| 默认值           | int→0，double→0.0，引用→null                 | new 出来的基本类型数组元素有默认值             |
| 索引范围         | 0 到 length-1                                | 访问越界 → ArrayIndexOutOfBoundsException     |
| 元素访问修改     | `arr[i] = 值`、`arr[i] += 值`                | 注意索引从 0 开始                              |
