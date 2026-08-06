---
layout: default
title: 4.10 Implementing ArrayList Algorithms
parent: Unit 4
nav_order: 10
---

# 4.10 — Implementing ArrayList Algorithms

## 4.10.A ArrayList 算法要点

在 ArrayList 上实现算法时，注意：

- **旋转（rotation）**：`add(size, remove(0))` 把第一个元素移到末尾。
- **遍历中删除**：相邻重复元素会被跳过（见 4.9），需调整索引或倒序遍历。
- **倒序处理**：`for (i = size()-1; i >= 0; i--)` 从后往前访问。
- **边界**：删除/访问索引必须在 [0, size()-1] 范围内。

{: .important}
> 增强 for 循环**不能**在遍历时用 `remove`（会抛 ConcurrentModificationException），删除操作应使用标准 for 循环。

{: .note}
> **大纲要求的标准 ArrayList 算法（EK 4.10.A.1）：** 与数组算法类似，利用 ArrayList 遍历可以求**最小/最大值**、**和/平均值**、判断**至少一个/所有**元素是否满足属性、统计元素个数、访问连续元素对、判断重复、**平移/旋转**、**反转**、**插入**、**删除**。
>
> **同时遍历多个集合（EK 4.10.A.2）：** 有些算法需要**同时**遍历多个 String、数组或 ArrayList 对象（例如计算两个列表对应位置元素的和）。

- ### 例题 1 — 旋转复制

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q14

  Consider the following code segment.

  ```java
  ArrayList<Integer> myList = new ArrayList<Integer>();
  myList.add(75);
  myList.add(20);
  myList.add(99);

  ArrayList<Integer> yourList = new ArrayList<Integer>();
  /* missing code */
  ```

  After the code segment is executed, yourList should contain [20, 99, 75].

  Which of the following can replace `/* missing code */` to produce this result?

  (A)
{% raw %}
  ```java
  int initialSize = myList.size();
  for (int i = 0; i < initialSize; i++)
  {
      myList.add(2, myList.remove(0));
      yourList.add(myList.get(0));
  }
  ```
{% endraw %}
  (B)
{% raw %}
  ```java
  int initialSize = myList.size();
  for (int i = 1; i <= initialSize; i++)
  {
      yourList.add(myList.get(i));
  }
  ```
{% endraw %}
  (C)
{% raw %}
  ```java
  for (Integer temp : myList)
  {
      yourList.add(0, temp);
  }
  ```
{% endraw %}
  (D)
{% raw %}
  ```java
  for (Integer temp : myList)
  {
      myList.add(2, myList.remove(0));
      yourList.add(temp);
  }
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (A)：每轮 `remove(0)` 取第一个元素放到索引 2（末尾），`yourList.add(myList.get(0))` 把新的第一个元素加入 yourList。第 1 轮：myList 变 [20,99,75]，yourList 加 20；第 2 轮：myList 变 [99,75,20]，yourList 加 99；第 3 轮：myList 变 [75,20,99]，yourList 加 75。yourList = [20,99,75]。选项 (B) 索引越界；(C)(D) 结果不对。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 倒序遍历删除

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q16

  Consider the following method.

{% raw %}
  ```java
  public void removeAll(int target, ArrayList<Integer> list)
  {
      for (int index = list.size(); index >= 0; index--)   // Line 3
      {
          if (list.get(index) == target)                   // Line 5
          {
              list.remove(index);
          }
      }
  }
  ```
{% endraw %}

  The method is intended to remove all values matching a target value from its ArrayList parameter. However, it is not working as intended.

  Which of the following changes can be made so that the method works as intended?

  (A) In line 3, changing the loop initialization to `index = list.size() - 1`  
  (B) In line 3, changing the loop condition to `index > 0`  
  (C) In line 3, changing the loop increment to `index++`  
  (D) In line 5, changing the list access expression to `list.get(target)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    列表最大合法索引是 `size() - 1`，而循环从 `list.size()` 开始，第一轮 `list.get(size())` 就**越界**抛异常。改为从 `size() - 1` 开始即可（倒序遍历删除是安全的）。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 隔一个删一个

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q17

  The following code segment initializes and processes an ArrayList of String elements. The loop is intended to delete every other element in the ArrayList starting with the first element.

{% raw %}
  ```java
  ArrayList<String> nameList = new ArrayList<String>();
  nameList.add("Stacey");
  nameList.add("Bob");
  nameList.add("Susan");
  nameList.add("Pete");

  for (int i = 0; i < nameList.size(); i++)
  {
      /* missing code */
  }
  ```
{% endraw %}

  After the code segment is executed, nameList should contain ["Bob", "Pete"].

  Which of the following can replace `/* missing code */` so that the code segment works as intended?

  (A) `nameList.remove(i);`  
  (B)
  ```java
  nameList.remove(i);
  i++;
  ```
  (C)
  ```java
  nameList.set(i, "Bob");
  nameList.set(i, "Pete");
  ```
  (D)
  ```java
  nameList.set(i, "Bob");
  nameList.set(i + 1, "Pete");
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (A)：i=0 删除 "Stacey"（Bob 移到索引 0），列表变 [Bob, Susan, Pete]；i=1 删除 "Susan"（Pete 移到索引 1），列表变 [Bob, Pete]；i=2 时 size()=2 循环退出。恰好隔一个删一个。正确答案是 **(A)**。

  </details>

- ### 例题 4 — 元素复制

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q18

  Consider the following method.

{% raw %}
  ```java
  public static void transform(ArrayList<Integer> items)
  {
      for (int i = items.size() - 1; i >= 0; i--)
      {
          items.add(i, items.get(i));
      }
  }
  ```
{% endraw %}

  The following code segment appears in a method in the same class as transform.

  ```java
  ArrayList<Integer> numbers = new ArrayList<Integer>();
  numbers.add(15);
  numbers.add(4);
  numbers.add(19);
  numbers.add(7);

  transform(numbers);
  ```

  What are the contents of numbers after executing the code segment?

  (A) [15, 4, 4, 19, 19, 7, 7]  
  (B) [15, 4, 19, 7, 7, 19, 4, 15]  
  (C) [15, 4, 19, 7, 15, 4, 19, 7]  
  (D) [15, 15, 4, 4, 19, 19, 7, 7]

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    倒序遍历：i=3 时 `add(3, 7)` → [15,4,19,7,7]；i=2 时 `add(2, 19)` → [15,4,19,19,7,7]；i=1 时 `add(1, 4)` → [15,4,4,19,19,7,7]；i=0 时 `add(0, 15)` → [15,15,4,4,19,19,7,7]。每个元素都在自己前面复制一份。正确答案是 **(D)**。

  </details>

- ### 例题 5 — 相邻 0 删除失败

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q21

  In the code segment shown, myList is an ArrayList of integers. The code segment is intended to remove all elements with the value 0 from myList.

{% raw %}
  ```java
  int j = 0;
  while (j < myList.size())
  {
      if (myList.get(j) == 0)
      {
          myList.remove(j);
      }
      j++;
  }
  ```
{% endraw %}

  The code segment does not always work as intended.

  For which of the following lists does the code segment not produce the correct result?

  (A) [0, 1, 0, 2]  
  (B) [1, 0, 0, 2]  
  (C) [1, 2, 3, 0]  
  (D) [1, 2, 3, 4]

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    j=0 删除第一个 0 后，后续元素前移，但 j 无条件 +1 会跳过移过来的元素。选项 (B) [1, 0, 0, 2]：j=1 删除第一个 0 → [1, 0, 2]；j=2 时指向 2（第二个 0 被跳过），残留一个 0。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 旋转操作           | `add(size, remove(0))` 移到末尾              | 追踪每轮列表变化                               |
| 倒序删除           | `for (i = size()-1; i >= 0; i--)`            | 倒序删除不会跳过元素                           |
| 越界防护           | 从 size()-1 开始，不越界                     | 从 size() 开始 → 越界异常                      |
| 隔一删一           | 每次删除后自动"跳过"一个                     | 不需要手动 i++                                 |
| 相邻重复删除       | 删除后前移会跳过相邻元素                     | 需调整索引或倒序遍历                           |
