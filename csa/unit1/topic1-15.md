---
layout: default
title: 1.15 String Manipulation
parent: Unit 1
nav_order: 15
---

# 1.15 — String Manipulation

## 1.15.A String 的常用方法

**String 对象**表示一个字符序列，可以通过**字符串字面量**或 **String 构造方法**创建。`String` 类属于 `java.lang` 包，**默认可用，无需 import**。

```java
String s1 = "hello";              // 用字符串字面量创建
String s2 = new String("hello");  // 用构造方法创建
```

AP CSA 考试中 String 是**不可变（immutable）**对象——调用 String 方法不会修改原字符串，而是返回一个新字符串。

**拼接（Concatenation）：** 两个 String 对象可以用 `+` 或 `+=` 连接，产生**新的 String 对象**；**原始值（int/double/boolean）**与 String 拼接时会被自动转换为字符串：

```java
String name = "Java";
name += "!";              // name 变为 "Java!"（新对象）
String msg = "总数：" + 42; // "总数：42"（int 42 自动转字符串）
```

| 方法                              | 作用                                                       | 示例                                      |
| --------------------------------- | ---------------------------------------------------------- | ----------------------------------------- |
| `str.length()`                    | 返回字符串中字符的个数                                     | `"CompSci".length()` → 7                  |
| `str.substring(a)`                | 返回从索引 a 到末尾的子串                                  | `"comp".substring(1)` → "omp"             |
| `str.substring(a, b)`             | 返回从索引 a 到 b-1 的子串（含 a 不含 b）                  | `"computer".substring(3, 5)` → "pu"       |
| `str.indexOf(str2)`               | 返回 str2 第一次出现的位置，找不到返回 **-1**              | `"science".indexOf("n")` → 4              |
| `str.equals(other)`               | 比较两个字符串的**内容**是否相等（不要用 `==`）            | `"ab".equals("ab")` → true                |
| `str1 + str2`（拼接）             | 连接字符串                                                 | `"A" + "B"` → "AB"                        |

{: .important}
> **索引从 0 开始。** `"CompSci".length()` 为 7，最后一个字符的索引是 `length() - 1` = 6。
>
> `substring(a, b)` 返回的是 `[a, b)` 区间：**包含 a，不包含 b**。`"computer".substring(3, 5)` 返回 "pu"（索引 3、4 两个字符）。
>
> 调用 String 方法**不会改变**原字符串。

## 1.15.B 常见的 String 陷阱

- `indexOf` 找不到时返回 **-1**；把 -1 当作 `substring` 的参数会抛 `StringIndexOutOfBoundsException`。
- `==` 比较引用（是否同一对象），`equals` 比较内容。
- `substring` 的参数可以是**变量**。

- ### 例题 1 — substring 提取子串

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q16

  Consider the following code segment.

  ```java
  String one = "computer";
  String two = "science";
  String concat = /* missing code */;
  System.out.println(concat);
  ```

  Which of the following expressions can be used to replace `/* missing code */` so that the code segment prints the string "pun"?

  (A) `one.substring(3, 4) + two.substring(4, 4)`  
  (B) `one.substring(3, 5) + two.substring(4, 5)`  
  (C) `one.substring(4, 5) + two.substring(5, 5)`  
  (D) `one.substring(4, 6) + two.substring(5, 6)`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `"computer"` 中索引 3、4 的字符是 'p'、'u'，`substring(3, 5)` 返回 "pu"；`"science"` 中索引 4 的字符是 'n'，`substring(4, 5)` 返回 "n"。拼接得 "pun"。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 最后一个字符的索引

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q17

  Consider the following code segment, which is intended to create a String that consists of the last character in word and assign it to the variable lastChar.

  ```java
  String word = /* initialization not shown */;  // line 1
  int len = word.length();                       // line 2
  String lastChar = word.substring(len);         // line 3
  ```

  Which of the following best describes why this code segment will not work as intended?

  (A) substring needs to be called with two parameters, so the method call in line 3 should be changed to `word.substring(len, len + 1)`.  
  (B) len is not the correct index of the last character in word, so the method call in line 3 should be changed to `word.substring(len - 1)`.  
  (C) len is not the correct index of the last character in word, so the method call in line 3 should be changed to `word.substring(len + 1)`.  
  (D) substring cannot be called with a variable as the parameter, so the method call in line 3 should be changed to `word.substring(word.length())`.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    字符串索引从 0 开始，最后一个字符的索引是 `word.length() - 1`。`word.substring(len)` 从索引 len（越界）开始取子串，会抛异常或得到错误结果。应改为 `word.substring(len - 1)`。正确答案是 **(B)**。

  </details>

- ### 例题 3 — indexOf 与运行时错误

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q18

  The following code segment is intended to assign to newWord the result created by removing the first occurrence of "a" from word. Assume that the String variable word has been properly declared and initialized. This code segment works for some, but not all, values of word.

  ```java
  int aLoc = word.indexOf("a");
  String newWord = word.substring(0, aLoc) + word.substring(aLoc + 1);
  ```

  Which of the following conditions best describes the condition in which this code segment will not work as intended and will result in a runtime error?

  (A) "a" is the first character in word.  
  (B) "a" is the last character in word.  
  (C) word does not contain the character "a".  
  (D) word contains only a sequence of multiple "a" characters.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    当 word 中不含 "a" 时，`indexOf("a")` 返回 **-1**。把 -1 作为 `substring` 的参数会抛出 `StringIndexOutOfBoundsException`。正确答案是 **(C)**。

  </details>

- ### 例题 4 — substring 不改变原字符串

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q6

  Consider the following code segment.

  ```java
  String str = "CompSci";
  System.out.println(str.substring(0, 3));
  int num = str.length();
  ```

  What is the value of num after the code segment is executed?

  (A) 3  
  (B) 4  
  (C) 6  
  (D) 7

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `"CompSci"` 长度为 7。调用 `substring` 不会改变 str 的值，因此 `str.length()` 仍为 7。正确答案是 **(D)**。

  </details>

- ### 例题 5 — substring 单参数与拼接

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q7

  Consider the following code segment.

  ```java
  String temp = "comp";
  System.out.print(temp.substring(0) + " "
      + temp.substring(1) + " "
      + temp.substring(2) + " "
      + temp.substring(3));
  ```

  What is printed as a result of executing the code segment?

  (A) `comp`  
  (B) `comp com co c`  
  (C) `comp omp mp p`  
  (D) `comp comp comp comp`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    单参数 `substring(n)` 返回从索引 n 到末尾的子串：`substring(0)` → "comp"，`substring(1)` → "omp"，`substring(2)` → "mp"，`substring(3)` → "p"。用空格拼接得 "comp omp mp p"。正确答案是 **(C)**。

  </details>

- ### 例题 6 — indexOf 与 substring 组合

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q22

  In the following code segment, mon and tue are properly declared String variables.

  ```java
  String str1 = mon.substring(0, mon.indexOf(" "));
  String str2 = tue.substring(tue.indexOf(" ") + 1);
  System.out.println(str1 + " and " + str2);
  ```

  For which of the following values of mon and tue will the code segment print "cloudy and foggy"?

  |        | mon                  | tue                    |
  | ------ | -------------------- | ---------------------- |
  | (A)    | "cloudy today"       | "foggy tomorrow"       |
  | (B)    | "cloudy today"       | "tomorrow foggy"       |
  | (C)    | "today cloudy"       | "foggy tomorrow"       |
  | (D)    | "today cloudy"       | "tomorrow foggy"       |

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    对 `"cloudy today"`：`indexOf(" ")` 为 6，`substring(0, 6)` 得 "cloudy"。对 `"tomorrow foggy"`：`indexOf(" ")` 为 8，`substring(9)` 得 "foggy"。输出 "cloudy and foggy"。选项 (B) 正确。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点                     | 关键内容                                          | 考试提示                                           |
| ------------------------ | ------------------------------------------------- | -------------------------------------------------- |
| String 创建              | 字面量或构造方法；java.lang 包默认可用            | `new String("hi")` 与 `"hi"` 均可                  |
| 索引从 0 开始            | 最后一个字符索引 = `length() - 1`                 | substring(len) 越界                               |
| substring(a, b)          | 返回 [a, b)，含 a 不含 b                          | `"computer".substring(3, 5)` → "pu"                |
| 字符串不可变             | 方法调用不改变原字符串                            | substring 后 length() 不变                         |
| 拼接                     | `+` / `+=` 产生新字符串；原始值自动转字符串       | `"总数：" + 42` → "总数：42"                       |
| indexOf 返回 -1          | 找不到目标返回 -1，用作 substring 参数会抛异常    | 先判断 indexOf >= 0 再使用                        |
| 单参数 substring         | 从指定索引到末尾                                  | `"comp".substring(1)` → "omp"                      |
| equals vs ==             | `equals` 比较内容，`==` 比较引用                  | 比较字符串内容必须用 equals                        |
