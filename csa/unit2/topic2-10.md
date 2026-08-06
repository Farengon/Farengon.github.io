---
layout: default
title: 2.10 Implementing String Algorithms
parent: Unit 2
nav_order: 10
---

# 2.10 — Implementing String Algorithms

## 2.10.A 字符串遍历与处理

处理字符串的算法通常结合**循环**与 **String 方法**：

- `str.length()`：字符串长度。
- `str.substring(a, b)`：取子串（含 a 不含 b）。
- `str.indexOf(target)`：查找目标首次出现的位置，找不到返回 -1。
- `str.equals(other)`：比较内容（不能用 `==`）。

{: .important}
> **字符串不可变**：`substring` 等方法返回新字符串，原字符串不变。用 `result += ...` 拼接时，每轮循环都会产生新字符串。

## 2.10.B 常见字符串算法

| 算法           | 关键思路                                                     |
| -------------- | ------------------------------------------------------------ |
| 逆序/重排子串  | 控制循环变量从后往前或按步长取子串                           |
| 统计字符出现   | 用 `indexOf` + 截取剩余部分，循环统计到 -1 为止              |
| 提取首字母     | `substring(0, 1)` 取第一个字符                               |
| 创建首字母缩写 | 找到空格，取空格后一个字符                                   |

- ### 例题 1 — 按步长取子串重排

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q12

  Consider the following code segment.

  ```java
  String str = "ABCDEF";
  String result = "";
  /* missing code */
  System.out.println(result);
  ```

  Which of the following can be used to replace `/* missing code */` so that this code segment prints the string `"EFCDAB"`?

  (A)
  ```java
  for (int j = str.length() - 1; j >= 0; j -= 1)
  {
      result += str.substring(j, j + 1);
  }
  ```
  (B)
  ```java
  for (int j = str.length() - 1; j >= 0; j -= 2)
  {
      result += str.substring(j, j + 2);
  }
  ```
  (C)
  ```java
  for (int j = str.length() - 2; j >= 0; j -= 1)
  {
      result += str.substring(j, j + 2);
  }
  ```
  (D)
  ```java
  for (int j = str.length() - 2; j >= 0; j -= 2)
  {
      result += str.substring(j, j + 2);
  }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (D)：j 从 4 开始，每次 -2：j=4 取 `substring(4, 6)` = "EF"；j=2 取 `substring(2, 4)` = "CD"；j=0 取 `substring(0, 2)` = "AB"。结果 "EFCDAB"。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 统计 "a" 的出现次数

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q13

  In the following code segment, str is a properly declared and initialized string. The code segment is intended to count the number of times that "a" appears in str.

  ```java
  int count = 0;
  String temp = str;
  int loc = temp.indexOf("a");
  while (loc >= 0)
  {
      /* missing code */
  }
  ```

  Which of the following can be used to replace `/* missing code */` so that the code segment works as intended?

  (A)
  ```java
  count++;
  temp = str.substring(loc + 1);
  ```
  (B)
  ```java
  count++;
  loc++;
  temp = str.substring(loc);
  ```
  (C)
  ```java
  count++;
  temp = temp.substring(loc);
  loc = temp.indexOf("a");
  ```
  (D)
  ```java
  count++;
  temp = temp.substring(loc + 1);
  loc = temp.indexOf("a");
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    找到 "a" 后 count+1，然后把 temp 更新为**从该 "a" 之后开始**的子串，并重新查找下一个 "a"。选项 (D) 用 `temp.substring(loc + 1)` 去掉已统计的部分，再更新 loc。选项 (A) 始终从原 str 截取会死循环；(C) 没有去掉已找到的 "a"。正确答案是 **(D)**。

  </details>

- ### 例题 3 — 创建首字母缩写（Acronym）

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q14

  An acronym is formed by extracting the first letter of each word in a phrase of one or more words. For example, the acronym of the phrase "Laugh Out Loud" is "LOL", and the acronym of the phrase "If you know you know" is "Iykyk".

  A phrase must meet the following conditions.

  - The phrase has exactly one space between each word.
  - The phrase does not have leading or trailing spaces.
  - The final word in the phrase has at least two characters.

  In the following code segment, the String variable phrase has been properly declared and initialized such that it meets these conditions. The code segment is intended to create the acronym of the String stored in phrase and store it in the variable text.

  ```java
  String temp = phrase;
  String text = temp.substring(0, 1);
  int i = temp.indexOf(" ");
  while (i > 0)
  {
      /* missing code */
  }
  ```

  Which of the following can be used to replace `/* missing code */` so that the code segment works as intended?

  (A)
  ```java
  text += temp.substring(0, 1);
  temp = temp.substring(i + 1);
  i = temp.indexOf(" ");
  ```
  (B)
  ```java
  temp = temp.substring(i + 1);
  text += temp.substring(0, 1);
  i = temp.indexOf(" ");
  ```
  (C)
  ```java
  text += temp.substring(i, i + 1);
  i = i + 1;
  ```
  (D)
  ```java
  text += temp.substring(i, i + 1);
  i = temp.indexOf(" ");
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    循环每次：先截掉当前单词（`temp.substring(i + 1)`），再取新 temp 的第一个字符拼接到 text，然后找下一个空格。选项 (B) 顺序正确：先去掉已处理的单词，再取新单词首字母，再更新 i。正确答案是 **(B)**。

  </details>

- ### 例题 4 — 累积前缀子串

  > **Source:** AP Classroom Unit 2 Progress Check: MCQ Part B, Q15

  Consider the following code segment.

  ```java
  String str = "qrstu";
  String result = "";
  for (int j = 0; j < str.length(); j++)
  {
      result += str.substring(0, j + 1);
  }
  System.out.println(result);
  ```

  What, if anything, is printed as a result of executing this code segment?

  (A) `rrsrstrstu`  
  (B) `qqrqrsqrst`  
  (C) `qqrqrsqrstqrstu`  
  (D) Nothing is printed because an IndexOutOfBoundsException occurs.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    每轮循环取 `substring(0, j+1)`：j=0 → "q"；j=1 → "qr"；j=2 → "qrs"；j=3 → "qrst"；j=4 → "qrstu"。拼接得 "qqrqrsqrstqrstu"。正确答案是 **(C)**。

  </details>

- ### 例题 5 — 统计 "a" 后不跟 "b"

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q24

  Consider the following code segment.

  ```java
  String str = "a black cat sat on a table";
  int counter = 0;
  for (int i = 0; i < str.length() - 1; i++)
  {
      if (str.substring(i, i + 1).equals("a") && !str.substring(i + 1, i + 2).equals("b"))
      {
          counter++;
      }
  }
  System.out.println(counter);
  ```

  What is printed as a result of executing the code segment?

  (A) 1  
  (B) 2  
  (C) 3  
  (D) 5

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    统计位置 i 处是 "a" 且 i+1 处不是 "b" 的次数。字符串中 "a" 出现的位置：索引 2（a空格）、6（ac）、9（at）、15（at）、20（a空格）——共 5 处都不是 "a" 后面紧跟 "b"（只有索引 2 的 "a black" 中 "a" 后是空格，不算 "b"；注意 "a black" 中第一个 "a" 后是空格）。等等，需要仔细数：字符串为 "a black cat sat on a table"，所有 "a"：位置 0（后跟空格 ✓）、位置 2（后跟空格... 实际上 "a black"：位置 0 是 "a"，位置 2 是 "a"？让我重数：a(0)空格(1)b(2)l(3)a(4)c(5)k(6)空格(7)c(8)a(9)t(10)空格(11)s(12)a(13)t(14)空格(15)o(16)n(17)空格(18)a(19)空格(20)t(21)a(22)b(23)l(24)e(25)。"a" 出现在 0、4、9、13、19、22。检查每个 "a" 后一位：0 后是空格 ✓；4 后是 c ✓；9 后是 t ✓；13 后是 t ✓；19 后是空格 ✓；22 后是 b ✗。共 5 个满足条件。正确答案是 **(D)**。

  </details>

- ### 例题 6 — 按条件拼接字符

  > **Source:** AP Classroom New Unit 2 TopicQuestion MCQ, Q25

  Consider the following code segment.

  ```java
  String word = "Computer Science";
  String str = "";
  for (int k = 0; k < word.length(); k++)
  {
      if (k % 3 == 0)
      {
          str = word.substring(k, k + 1) + str;
      }
  }
  System.out.println(str);
  ```

  What is printed as a result of executing the code segment?

  (A) `ci tm`  
  (B) `eeStm`  
  (C) `ncepC`  
  (D) `eeSepC`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `k % 3 == 0` 在 k = 0, 3, 6, 9, 12, 15 时为 true。这些位置的字符：k=0 'C'、k=3 'p'、k=6 'e'、k=9 'r'、k=12 'c'、k=15 'S'。由于是**每次拼到 str 前面**（`str = char + str`），最终顺序反转：S c r e p C，即 "ScrepC"... 等等，题目答案给的是 "eeSepC"。让我重新核对：word = "Computer Science"。索引：0:C, 1:o, 2:m, 3:p, 4:u, 5:t, 6:e, 7:r, 8:(空格), 9:S, 10:c, 11:i, 12:e, 13:n, 14:c, 15:e。k%3==0 的位置：0(C), 3(p), 6(e), 9(S), 12(e), 15(e)。逐个拼到前面：k=0 → "C"；k=3 → "pC"；k=6 → "epC"；k=9 → "SepC"；k=12 → "eSepC"；k=15 → "e eSepC" = "eeSepC"。输出 "eeSepC"。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                     |
| ---------------- | -------------------------------------------- | -------------------------------------------- |
| 字符串遍历       | length / substring / indexOf 组合使用        | 循环边界：`j < str.length()`                 |
| 统计出现次数     | indexOf + 截断剩余部分                       | 截断必须基于 temp 而非原 str                 |
| 首字母缩写       | 取空格后一字符                               | 先去掉已处理单词再取首字母                   |
| 前缀累积         | substring(0, j+1) 拼接                       | 字符串不可变，+= 每次产生新串                |
| 条件拼接         | 满足条件时把字符拼到前面                     | 拼到前面会反转顺序                           |
