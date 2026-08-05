---
layout: default
title: 1.3 Expressions and Output
parent: Unit 1
nav_order: 3
---

# 1.3 — Expressions and Output

## 1.3.A 输出：System.out.print 和 System.out.println

**System.out.print** 和 **System.out.println** 用于在计算机屏幕上显示信息。两者的区别在于：**System.out.println** 在显示信息后将光标移动到**新的一行**，而 **System.out.print** 不会。 

```java
System.out.print("Hello ");   // 输出后不换行
System.out.println("World");  // 输出后换行
System.out.println("Done");   // 输出后换行
```

输出结果：

```
Hello World
Done
```

- ### 例题 1 — 选择正确的输出语句

    > Source: AP Classroom Unit 1 Progress Check: MCQ Part A, Q8

    Which of the following code segments will print the word Hello?

    (A) `System.out.print("Hello");`  
    (B) `System.out.print(Hello);`  
    (C) `"System.out.print(Hello)";`  
    (D)

    ```
    System.out.print(He);
    System.out.print(llo);
    ```

    **分析与解答：**  
    在 Java 中，字符串字面量必须用双引号括起来。选项 (A) 正确地使用了 `System.out.print("Hello")`，将字符串字面量 `"Hello"` 作为参数传递给 print 方法。选项 (B) 缺少引号，编译器会将 `Hello` 当作变量名处理。选项 (C) 将整个语句放在引号中，变成了一段字符串。选项 (D) 会输出 `Hello`，但分成两次输出，中间没有空格。正确答案是 **(A)**。 [pdf_9]

---

## 1.3.B 字符串字面量与转义序列

**字面量（Literal）** 是代码中对固定值的表示。

**字符串字面量（String Literal）** 是由双引号括起来的一串字符序列。

```java
System.out.println("Hello, World!");   // "Hello, World!" 是一个字符串字面量
System.out.println("42");              // "42" 是字符串，不是整数 42
```

**转义序列（Escape Sequence）** 是以反斜杠 `\` 开头的特殊字符序列，在**字符串**中具有特殊含义。AP CSA 课程中涉及的转义序列包括： 

| 转义序列 | 含义            |
| -------- | --------------- |
| `\"`     | 双引号          |
| `\\`     | 反斜杠          |
| `\n`     | 换行（newline） |

```java
System.out.println("She said, \"Hello!\"");  // 输出: She said, "Hello!"
System.out.println("Line1\nLine2");           // 输出两行
System.out.println("Path: C:\\Files");        // 输出: Path: C:\Files
```

- ### 例题 2 — 转义序列的行为

    > Source: AP Classroom Unit 1 Progress Check: MCQ Part A, Q9

    Consider the following statement.

    ```java
    System.out.print("AP \n Computer \n Science \n A \n rocks");
    ```

    Which of the following best describes the behavior of this statement?

    (A) It prints five lines of text, each separated by a line break indicated by the escape sequence `\n`.  
    (B) It prints four lines of text because the escape sequence `\n` appears four times in the string literal.  
    (C) It prints one line of text because the printed value is a single string literal.  
    (D) It prints nothing due to a syntax error.

    **分析与解答：**  
    字符串中的每个 `\n` 转义序列都会产生一个换行。字符串中共有四个 `\n`，因此将输出五行文本（"AP"、"Computer"、"Science"、"A"、"rocks" 各占一行）。注意 `System.out.print` 不会在末尾自动添加换行，但 `\n` 本身已经产生了换行效果。正确答案是 **(A)**。 [pdf_9]

- ### 例题 3 — 字符串字面量的语法

    > Source: AP Classroom New Unit 1 TopicQuestion MCQ, Q21

    Consider the following code segment.

    ```java
    System.out.print(I do not fear computers. );   // Line 1
    System.out.println(I fear the lack of them.);  // Line 2
    System.out.println(--Isaac Asimov);            // Line 3
    ```

    The code segment is intended to produce the following output but may not work as intended.

    ```
    I do not fear computers. I fear the lack of them.
    --Isaac Asimov
    ```

    Which change, if any, can be made so that the code segment produces the intended output?

    (A) In line 1, print should be changed to println.  
    (B) The statement `System.out.println()` should be inserted between lines 2 and 3.  
    (C) In lines 1, 2, and 3, the text that appears in parentheses should be enclosed in quotation marks.  
    (D) No change is needed; the code segment works correctly as is.

    **分析与解答：**
    在 Java 中，所有字符串字面量都必须用双引号（`"`）括起来。原代码中的文本没有加引号，编译器会将它们当作变量名或标识符处理，导致编译错误。选项 (A) 和 (B) 都不能解决缺少引号的问题。选项 (C) 正确地将文本用双引号括起，使其成为合法的字符串字面量。选项 (D) 错误，因为代码无法编译通过。正确答案是 **(C)**。 [pdf_19]

---

## 1.3.C 算术表达式

**算术表达式（Arithmetic Expression）** 由数值、变量和运算符构成，包括 `int` 类型和 `double` 类型的表达式。 [pdf_2]

**算术运算符：** 加法 `+`、减法 `-`、乘法 `*`、除法 `/`、取余 `%`。


### 运算结果的数据类型

{: .important}
> - 两个 `int` 值进行算术运算，结果类型为 `int`。
> - 运算中至少有一个 `double` 值，结果类型为 `double`。

```java
int a = 5 + 3;        // 5 + 3 = 8，int 类型
double b = 5.0 + 3;   // 5.0 + 3 = 8.0，double 类型（int 自动提升为 double）
double c = 5 + 3.0;   // 5 + 3.0 = 8.0，double 类型
```

{: .extra}
> **Exclusion Statement：** 结果为特殊 double 值（如无穷大和 NaN）的表达式不在 AP CSA 考试范围内。

### 整数除法与浮点数除法

{: .important}
> - 两个 `int` 值相除，结果只保留商的**整数部分**（截断，不四舍五入）。
> - 运算中至少有一个 `double` 值，结果保留完整的商。 [pdf_2]

```java
int x = 7 / 2;        // 结果是 3（整数除法，小数部分被截断）
double y = 7.0 / 2;   // 结果是 3.5（double 除法）
double z = 7 / 2;     // 结果是 3.0！先做整数除法 7 / 2 = 3，再赋值给 double
```

### 取余运算符（%）

取余运算符 `%` 计算一个数除以另一个数的**余数**。

```java
int remainder = 17 % 5;   // 17 ÷ 5 = 3 余 2，remainder = 2
```

> **Exclusion Statement：** 被除数 a 小于 0，以及除数 b 小于等于 0 的情况不在 AP CSA 考试范围内。

### 运算符优先级

运算符可以组合成复合表达式。在编译时，数值根据**运算符优先级（Operator Precedence）** 与运算符结合，决定分组方式。可以使用圆括号 `()` 修改优先级。 

{: .note}
> **优先级规则（从高到低）：**

> 1. 圆括号 `()`
> 2. 乘法 `*`、除法 `/`、取余 `%`（同级，从左到右计算）
>  3. 加法 `+`、减法 `-`（同级，从左到右计算）

```java
int result = 5 + 10 * 2;        // 10 * 2 先算 → 5 + 20 = 25
int result2 = (5 + 10) * 2;     // 5 + 10 先算 → 15 * 2 = 30
int result3 = 17 % 5 + 3;       // 17 % 5 = 2 → 2 + 3 = 5
```

### 除零错误

尝试用整数零除以整数会抛出 `ArithmeticException`。

```java
int x = 10 / 0;   // 运行时错误：ArithmeticException（整数除零）
double y = 10.0 / 0.0;   // 结果为 Infinity（无穷大，不在考试范围内）
```

- ### 例题 4 — 运算符优先级

    > Source: AP Classroom New Unit 1 TopicQuestion MCQ, Q1

    Consider the following code segment.

    ```java
    int a = 5;
    int b = 8;
    int c = 3;
    System.out.println(a + b / c * 2);
    ```

    What is printed as a result of executing the code segment?

    (A) 2  
    (B) 6  
    (C) 8  
    (D) 9

    **分析与解答：**

    按照运算符优先级规则，`/` 和 `*` 优先级高于 `+`，且同级从左到右计算。因此执行顺序为：

    1. `b / c` → `8 / 3` → `2`（整数除法）
    2. `2 * 2` → `4`
    3. `a + 4` → `5 + 4` → `9`

    正确答案是 **(D)**。 

- ### 例题 5 — 整数除法与类型转换

    > Source: AP CSA Course and Exam Description (Sample Exam Questions)

    Consider the following code segment.

    ```java
    double q = 15.0;
    int r = 2;
    double x = (int) (q / r);
    double y = q / r;
    System.out.println(x + " " + y);
    ```

    What is printed as a result of executing this code segment?

    (A) 7.0 7.0  
    (B) 7.0 7.5  
    (C) 7.5 7.0  
    (D) 7.5 7.5

    **分析与解答：**

    逐步追踪：

    - `q / r` → `15.0 / 2` → `7.5`（至少有一个 double，结果为 double）
    - `(int)(q / r)` → `(int)(7.5)` → `7`（强制类型转换为 int，截断小数部分）
    - `x = 7` → `x = 7.0`（赋值给 double 变量，自动提升为 7.0）
    - `y = q / r` → `y = 7.5`

    因此输出为 `7.0 7.5`。正确答案是 **(B)**。

- ### 例题 6 — 取余运算符与优先级

    > Source: Practice Exam 1 MCQ, Q4

    Consider the following code segment.

    ```java
    int first = 5 + 10 * 2;
    int second = first + first % 2;
    ```

    What is the value of `second` after this code segment is executed?

    (A) 37  
    (B) 30  
    (C) 26  
    (D) 0

    **分析与解答：**

    第一步：计算 `first`。`*` 优先级高于 `+`，所以 `10 * 2 = 20`，然后 `5 + 20 = 25`，`first = 25`。

    第二步：计算 `second`。`%` 优先级高于 `+`，所以先计算 `first % 2` → `25 % 2 = 1`（25 除以 2 余 1），然后 `25 + 1 = 26`，`second = 26`。

    正确答案是 **(C)**。

- ### 例题 7 — 复合表达式（多种运算符组合）

    > Source: AP Classroom Unit 1 Progress Check: MCQ Part A, Q7

    Consider the following code segment.

    ```java
    int a = 1;
    int b = 2;
    int c = 3;
    int d = 4;
    double x = a + b * c % d;
    ```

    What is the value of x after executing the code segment?

    (A) 1.0

    (B) 2.5

    (C) 3.0

    (D) 7.0

    **分析与解答：**

    `*` 和 `%` 优先级相同且高于 `+`，从左到右计算：

    1. `b * c` → `2 * 3 = 6`
    2. `6 % d` → `6 % 4 = 2`（6 除以 4 余 2）
    3. `a + 2` → `1 + 2 = 3`
    4. `x = 3` → `x = 3.0`（赋值给 double 变量）

    正确答案是 **(C)**。

---

## 考点总结

| 考点                        | 核心内容                               | 考试要点                                 |
| --------------------------- | -------------------------------------- | ---------------------------------------- |
| System.out.print vs println | print 不换行，println 换行             | 根据输出格式要求选择正确的方法           |
| 字符串字面量                | 双引号括起来的字符序列                 | 字符串必须用双引号，不能省略             |
| 转义序列                    | `\"`、`\\`、`\n`                       | `\n` 产生换行，注意每个 `\n` 对应一行    |
| 算术运算符                  | `+` `-` `*` `/` `%`                    | 两个 int 运算得 int，有 double 得 double |
| 整数除法                    | int/int 只保留整数部分                 | 7/2=3，不是 3.5                          |
| 取余运算                    | `%` 计算余数                           | 17%5=2，常用于判断奇偶、提取数字         |
| 运算符优先级                | `*` `/` `%` 高于 `+` `-`，同级从左到右 | 使用圆括号可以改变优先级                 |
| 除零错误                    | 整数除以零 → ArithmeticException       | 注意避免除零                             |