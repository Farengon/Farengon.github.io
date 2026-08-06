---
layout: default
title: 4.6 Using Text Files
parent: Unit 4
nav_order: 6
---

# 4.6 — Using Text Files

## 4.6.A 用 Scanner 读取文本文件

**文件（File）** 是程序不运行时也能持久保存数据的存储位置，程序执行时可以从中读取数据。用 **Scanner** 读取文本文件：

```java
File file = new File("input.txt");   // 创建 File 对象（参数为文件名）
Scanner scan = new Scanner(file);    // 把 Scanner 连接到文件
```

**Scanner 的常用方法：**

| 方法                | 作用                         |
| ------------------- | ---------------------------- |
| `nextInt()`         | 读取下一个 int 值            |
| `nextDouble()`      | 读取下一个 double 值         |
| `next()`            | 读取下一个字符串（以空白分隔）|
| `nextLine()`        | 读取一整行                   |
| `hasNext()`         | 是否还有下一个输入项         |

{: .note}
> - `nextInt()` 会跳过空白（包括换行），按"下一个 token"读取。文件中的 `1`、`2`、`3` 无论在一行还是多行，都能被三个 `nextInt()` 依次读到。
> - **`File` 和 `IOException` 类属于 `java.io` 包**，使用前需要 **import 语句**（`import java.io.*;`）。
> - 使用 `File` 类时必须声明：如果提供的文件名无法打开该如何处理——常用方法是在方法头加上 **`throws IOException`**（EK 4.6.A.4/A.5）。

## 4.6.B 文件读取的循环模式

{% raw %}
```java
while (fileInput.hasNext())
{
    double temp = fileInput.nextDouble();
    // 处理 temp
}
```
{% endraw %}

{: .important}
> - 循环中**每轮只读取一次**数据并保存到临时变量，避免重复读取。
> - `Integer.parseInt(scan.next())` 可以把字符串形式的数字转成 int。

- ### 例题 1 — nextInt 的分隔符

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q1

  In the following code segment, a valid Scanner object named scan is created to read from the text file input.txt.

  ```java
  File readFile = new File("input.txt");
  Scanner scan = new Scanner(readFile);

  int firstIn = scan.nextInt();
  int secondIn = scan.nextInt();
  int thirdIn = scan.nextInt();
  ```

  Which of the following could be the contents of input.txt so that the variables firstIn, secondIn, and thirdIn are each assigned a valid value by the code segment?

  (A) `123`  
  (B)
  ```
  1
  2
  3
  ```
  (C) `1,2,3`  
  (D) `firstIn: 1 secondIn: 2 thirdIn: 3`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `nextInt()` 以**空白**（空格、换行、制表符）作为分隔符。选项 (B) 中 1、2、3 各占一行，也能被依次读取为三个 int。选项 (A) 的 "123" 是一个整数；(C) 用逗号分隔不是空白；(D) 含有非数字内容。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 累加正数

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q2

  In the following code segment, a valid Scanner object named fileInput is created to read from the text file numbers.txt. Assume that the text file contains only numerical data and spaces.

{% raw %}
  ```java
  File numData = new File("numbers.txt");
  Scanner fileInput = new Scanner(numData);

  double sum = 0.0;
  while (fileInput.hasNext())
  {
      /* missing code */
  }
  System.out.println(sum);
  ```
{% endraw %}

  Which of the following can be used to replace `/* missing code */` so that the code segment prints the sum of the positive numbers in the file?

  (A)
{% raw %}
  ```java
  if (fileInput > 0)
  {
      sum = sum + fileInput;
  }
  ```
{% endraw %}
  (B)
{% raw %}
  ```java
  if (fileInput.nextDouble() > 0)
  {
      sum = sum + fileInput.nextDouble();
  }
  ```
{% endraw %}
  (C)
{% raw %}
  ```java
  double temp = fileInput.nextDouble();
  if (temp > 0)
  {
      sum = sum + temp;
  }
  ```
{% endraw %}
  (D)
{% raw %}
  ```java
  double temp = fileInput.nextDouble();
  if (temp > 0)
  {
      sum = sum + fileInput.nextDouble();
  }
  ```
{% endraw %}

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    每轮循环先 `nextDouble()` 读取一个值存入 temp，再判断 temp 是否为正并累加。选项 (C) 每轮只读一次，正确。选项 (B)(D) 在判断后又调用一次 `nextDouble()`，会**跳过**一个值（每轮读两个、加一个）。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 循环读取最后一个值

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q3

  A text file named data.txt has the following contents. Assume that the file contains no spaces.

  ```
  123
  456
  789
  ```

  In the following code segment, a valid Scanner object named source is created to read from the text file.

{% raw %}
  ```java
  int x = 0;
  File text = new File("data.txt");
  Scanner source = new Scanner(text);

  while (source.hasNext())
  {
      x = source.nextInt();
  }
  System.out.println(x);
  ```
{% endraw %}

  What is printed as a result of executing the code segment?

  (A) 0  
  (B) 123  
  (C) 789  
  (D) 123456789

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环每次把读取的 int 赋给 x：x = 123 → 456 → 789。循环结束时 x 保存的是**最后一个**值 789。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 字符串转数字

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q6

  A text file named grades.txt has the following contents.

  ```
  89 92 90 88 79 85 77
  ```

  In the following code segment, a valid Scanner object named scan is created to read from the text file. The code segment is intended to store the values from grades.txt into an int array.

{% raw %}
  ```java
  File gradeFile = new File("grades.txt");
  Scanner scan = new Scanner(gradeFile);

  int[] reportCard = new int[7];
  for (int i = 0; i < reportCard.length; i++)
  {
      int currentGrade = /* missing expression */;
      reportCard[i] = currentGrade;
  }
  ```
{% endraw %}

  Which of the following can replace `/* missing expression */` so that the code segment works as intended?

  (A) `Double.parseDouble(scan.next())`  
  (B) `Integer.parseInt(scan.next())`  
  (C) `Integer.parseInt(scan.nextInt())`  
  (D) `Integer.parseInt(scan.nextLine())`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `scan.next()` 返回字符串（如 "89"），`Integer.parseInt` 把它转成 int。选项 (B) 正确。选项 (C) 中 `scan.nextInt()` 已返回 int，不能再传给 parseInt；(A) 返回 double；(D) 的 nextLine 会读到整行。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 文件读取         | `new Scanner(new File(...))`                 | 以空白为分隔符                                 |
| Scanner 方法     | nextInt / nextDouble / next / hasNext        | nextInt 跳过换行                               |
| 循环读取         | 每轮只读一次，存临时变量                     | 重复 nextDouble 会跳过数据                     |
| 字符串转换       | Integer.parseInt / Double.parseDouble        | 把"数字字符串"转成数值                         |
| 循环结果         | 反复赋值时最后是最后一个值                   | x 最终 = 789                                   |
