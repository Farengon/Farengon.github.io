---
layout: default
title: 4.8 ArrayList Methods
parent: Unit 4
nav_order: 8
---

# 4.8 — ArrayList Methods

## 4.8.A ArrayList 的创建

**ArrayList** 是**可变长度**的对象列表，用泛型指定元素类型：

```java
ArrayList<Thing> al = new ArrayList<Thing>();   // 只能存储 Thing 对象
ArrayList<Integer> ages = new ArrayList<Integer>();
```

{: .note}
> - ArrayList 只能存储**对象**，不能存储基本类型——存整数要用包装类 `Integer`。
> - `new ArrayList<Integer>()` 是标准创建语法。
> - **ArrayList 的大小可变（mutable in size）**，且存储的是**对象引用**。
> - **`ArrayList` 类属于 `java.util` 包**，使用前需要 **import 语句**（`import java.util.ArrayList;` 或 `import java.util.*;`）。
> - **泛型 `ArrayList<E>`**：类型参数 E 指定元素类型，例如 `ArrayList<String>` 只能存 String。

## 4.8.B ArrayList 的常用方法

| 方法                          | 作用                                       |
| ----------------------------- | ------------------------------------------ |
| `add(元素)`                   | 在末尾添加元素                             |
| `add(索引, 元素)`             | 在指定索引插入元素（后续元素后移）         |
| `get(索引)`                   | 返回指定索引的元素                         |
| `set(索引, 元素)`             | 替换指定索引的元素，返回旧值               |
| `remove(索引)`                | 删除指定索引的元素（后续元素前移）         |
| `size()`                      | 返回元素个数                               |

{: .important}
> - `add(0, x)` 在头部插入；`remove(i)` 后，索引 i 之后的元素**前移一位**。
> - 追踪 ArrayList 操作时，每执行一个方法都重新画出列表内容。

- ### 例题 1 — ArrayList 声明

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q7

  Consider the following statement, which is intended to create an ArrayList named al to store only elements of type Thing. Assume that the Thing class has been properly defined and includes a no-parameter constructor.

  ```java
  ArrayList<Thing> al = /* missing code */;
  ```

  Which of the following can be used to replace `/* missing code */` so that the statement works as intended?

  (A) `new Thing();`  
  (B) `new ArrayList<Thing>();`  
  (C) `new ArrayList(Thing);`  
  (D) `new ArrayList<>(Thing);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    创建 ArrayList 要使用 `new ArrayList<Thing>()`，类型参数 Thing 写在尖括号内。选项 (B) 正确。正确答案是 **(B)**。

  </details>

- ### 例题 2 — add 方法追踪

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q8

  Consider the following code segment.

  ```java
  ArrayList<Integer> ages = new ArrayList<Integer>();
  ages.add(18);
  ages.add(20);
  ages.add(1, 15);
  ```

  What are the contents of ages after executing the code segment?

  (A) [15, 18, 20]  
  (B) [18, 15, 20]  
  (C) [18, 20, 15]  
  (D) [20, 15, 18]

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `add(18)` → [18]；`add(20)` → [18, 20]；`add(1, 15)` 在索引 1 插入 15 → [18, 15, 20]。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 多种方法组合

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q9

  Consider the following code segment.

  ```java
  ArrayList<Integer> nums = new ArrayList<Integer>();
  nums.add(3);
  nums.add(2);
  nums.add(1);
  nums.add(0);
  nums.add(0, 4);
  nums.set(3, 2);
  nums.remove(3);
  nums.add(2, 0);
  ```

  Which of the following represents the contents of nums after the code segment is executed?

  (A) [2, 3, 2, 1, 0]  
  (B) [4, 0, 0, 1, 3]  
  (C) [4, 2, 0, 2, 0]  
  (D) [4, 3, 0, 2, 0]

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    逐步追踪：add 3,2,1,0 → [3,2,1,0]；add(0,4) → [4,3,2,1,0]；set(3,2) 把索引 3 改为 2 → [4,3,2,2,0]；remove(3) 删除索引 3 → [4,3,2,0]；add(2,0) 在索引 2 插入 0 → [4,3,0,2,0]。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 前置条件（非空）

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q10

  Consider the following method.

{% raw %}
  ```java
  public static void processNumbers(ArrayList<Integer> numbers)
  {
      int last = numbers.size() - 1;
      numbers.add(0, numbers.get(last));
      numbers.remove(last + 1);
  }
  ```
{% endraw %}

  Which of the following best describes the preconditions necessary for the method to run without error?

  (A) The ArrayList must be sorted from smallest to largest.  
  (B) The ArrayList must contain at least one element.  
  (C) The ArrayList must contain at least two elements.  
  (D) The ArrayList must contain only positive Integer values.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `numbers.get(last)` 要求 `last = size() - 1` 是合法索引，即列表至少要有 **1 个元素**（size ≥ 1）。正确答案是 **(B)**。

  </details>

- ### 例题 5 — 首尾交换

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q11

  Consider the following code segment.

{% raw %}
  ```java
  ArrayList<Integer> nums = new ArrayList<Integer>();
  nums.add(12);
  nums.add(13);
  nums.add(15);
  nums.add(10);

  if (nums.get(0) > nums.get(nums.size() - 1))
  {
      int x = nums.get(0);
      nums.set(0, nums.get(nums.size() - 1));
      nums.set(nums.size() - 1, x);
  }
  ```
{% endraw %}

  Which of the following best describes the behavior of the code segment?

  (A) It compares all values in nums and places nums in order from smallest to largest.  
  (B) It compares all values in nums and places nums in order from largest to smallest.  
  (C) It compares the first and last elements in nums and swaps them if the first element is larger than the last.  
  (D) It compares the first and last elements in nums and swaps them if the first element is smaller than the last.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    代码把索引 0 的元素与 `nums.size() - 1`（最后一个元素）比较，若第一个元素更大，则用 set 交换两者。只比较首尾两个元素，不是全排序。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| ArrayList 创建   | `new ArrayList<类型>()`                      | 只能存对象，整数用 Integer                     |
| add / add(i, x)  | 末尾添加 / 指定位置插入                      | 插入后后续元素后移                             |
| set / remove     | 替换 / 删除元素                              | 删除后后续元素前移                             |
| size()           | 元素个数，最大索引 size()-1                  | 空列表时 size()-1 非法                         |
| 逐方法追踪       | 每步重画列表内容                             | 组合操作要按顺序逐步执行                       |
