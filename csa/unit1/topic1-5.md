---
layout: default
title: 1.5 Casting and Range of Variables
parent: Unit 1
nav_order: 5
---

# 1.5 — Casting and Range of Variables

## 1.5.A 类型转换（Casting）

**类型转换（Casting）** 是将一种基本数据类型的值转换为另一种基本数据类型的过程。在 Java 中，`(int)` 和 `(double)` 可用于在 `double` 值和 `int` 值之间进行转换。

```java
double d = 3.14;
int i = (int) d;     // i = 3

int x = 5;
double y = (double) x;  // y = 5.0
```

**截断（Truncation）：** 将 `double` 值强制转换为 `int` 值时，小数部分被直接截断（舍弃），**不做四舍五入**。

```java
double d = 7.999;
int i = (int) d;     // i = 7，不是 8
```

**自动扩宽（Automatic Widening）：** 某些情况下，`int` 值会被自动扩宽为 `double` 值，不需要显式转换。常见场景包括：将 `int` 赋值给 `double` 变量；`int` 与 `double` 进行算术运算时，`int` 自动扩宽为 `double`。

```java
int x = 5;
double y = x;          // 自动扩宽：y = 5.0

double result = 3 + 2.0;   // 3 自动扩宽为 3.0，结果为 5.0
```

**四舍五入（Rounding）：** 对于非负数，使用 `(int)(x + 0.5)` 将 `double` 四舍五入到最接近的整数。对于负数，使用 `(int)(x - 0.5)`。

```java
double x = 4.2;
int rounded = (int)(x + 0.5);   // (int)(4.7) = 4

double y = 7.6;
int roundedY = (int)(y + 0.5);  // (int)(8.1) = 8
```

- ### 例题 1 — 显式转换与自动扩宽

    > Source: AP CSA Course and Exam Description (Sample Exam Questions)

    ```java
    double q = 15.0;
    int r = 2;
    double x = (int) (q / r);
    double y = q / r;
    System.out.println(x + " " + y);
    ```

    What is printed?

    (A) 7.0 7.0
    (B) 7.0 7.5
    (C) 7.5 7.0
    (D) 7.5 7.5

    **分析与解答：**  
    `q / r` → 15.0 / 2，int 的 `r` 自动扩宽为 2.0，结果为 7.5。`(int)(7.5)` 截断小数部分，得到 int 值 7。将 7 赋值给 `double x`，自动扩宽为 7.0。`y = q / r` = 15.0 / 2 = 7.5（自动扩宽）。输出为 7.0 7.5。正确答案是 (B)。

- ### 例题 2 — 类型转换与截断

    > Source: Unit 1 Progress Check MCQ Part B, Q1

    ```java
    double a = 7;
    int b = (int) (a / 2);
    double c = (double) b / 2;
    System.out.print(b);
    System.out.print(" ");
    System.out.print(c);
    ```

    What is printed?

    (A) 3 1.0
    (B) 3 1.5
    (C) 3.5 1.5
    (D) 3.5 1.75

    分析与解答：
    `double a = 7;` → a = 7.0（int 7 自动扩宽为 double）。`a / 2` → 7.0 / 2 = 3.5。`(int)(3.5)` 截断小数，b = 3。`(double) b / 2` → (double) 3 / 2 → 3.0 / 2 = 1.5（注意：(double) 只作用于 b，2 自动扩宽）。输出为 3 1.5。正确答案是 (B)。

- ### 例题 3 — 先截断后相加 vs 先相加后截断

    > Source: APCSA 2024 MCQ, Q5

    ```java
    double valOne = 5.75;
    double valTwo = 2.75;
    int x = (int) valOne + (int) valTwo;
    int y = (int) (valOne + valTwo);
    System.out.println(x + "" + y);
    ```

    What is printed?

    (A) 77
    (B) 78
    (C) 79
    (D) 98
    (E) 99

    分析与解答：
    `(int) valOne` = (int) 5.75 = 5，`(int) valTwo` = (int) 2.75 = 2，x = 5 + 2 = 7。`valOne + valTwo` = 5.75 + 2.75 = 8.5，y = (int) 8.5 = 8。输出为 78。正确答案是 (B)。

- ### 例题 4 — 使用 (int)(x + 0.5) 四舍五入

    > Source: Unit 1 Progress Check MCQ Part B, Q2

    Assume that `x` is a double variable with a **positive** value. Which of the following code segments can be used to round `x` to the nearest integer and store the rounded value in the variable `result`?

    (A) `int result = (int) x;`
    (B) `int result = (int) x + 0.5;`
    (C) `int result = (int)(x + 0.5);`
    (D) `int result = (int) x + (int) 0.5;`

    **分析与解答：**  
    (A) 只截断，不四舍五入。(B) 编译错误：(int) x + 0.5 结果为 double，不能赋值给 int。(C) 正确：先加 0.5，再截断，实现四舍五入——若 x = 4.2，4.2 + 0.5 = 4.7，(int) 得 4；若 x = 7.6，7.6 + 0.5 = 8.1，(int) 得 8。(D) (int) x + (int) 0.5 = (int) x + 0 = (int) x，只截断，不四舍五入。正确答案是 (C)。

- ### 例题 5 — 类型转换时机：先除后转 vs 先转后除

    > Source: Practice Exam 1 MCQ, Q8

    ```
    double w = 2.5;
    double x = 5.0;
    double z = (int) w / x;
    System.out.print(z + " ");
    z = (int) (w / x);
    System.out.println(z);
    ```

    What is printed?

    (A) 0.0 0.0
    (B) 0.4 0.0
    (C) 0.4 0.4
    (D) 0.0 0.4

    分析与解答：
    `(int) w / x`：(int) 2.5 = 2，然后 2 / 5.0 → 2.0 / 5.0 = 0.4（自动扩宽）。`(int) (w / x)`：w / x = 2.5 / 5.0 = 0.4，(int) 0.4 = 0，赋值给 double z → 0.0。输出为 0.4 0.0。正确答案是 (B)。

---

## 1.5.B 变量取值范围（Range of Variables）

Java 提供了两个常量来表示 `int` 类型的取值范围：

| 常量                | 含义                          |
| ------------------- | ----------------------------- |
| `Integer.MAX_VALUE` | int 能表示的最大值（2³¹ − 1） |
| `Integer.MIN_VALUE` | int 能表示的最小值（−2³¹）    |

{: .note}
`int` 值在 Java 中用 **4 字节（32 位）** 内存存储，因此 `int` 值必须在 `Integer.MIN_VALUE` 到 `Integer.MAX_VALUE` 之间（含两端）。当表达式的结果超出此范围时，会发生**溢出（overflow）**。

```java
int max = Integer.MAX_VALUE;  // 2147483647
int overflow = max + 1;       // 溢出，结果为 -2147483648
```

- ### 例题 6 — 溢出与 Integer.MAX_VALUE

    > Source: Unit 1 Progress Check MCQ Part B, Q10

    ```java
    int result = num1 + num2;
    System.out.println(result);
    ```

    Which of the following preconditions for the method is most appropriate to avoid an overflow error?

    (A) `/** Precondition: num1 and num2 are both positive. */`
    (B) `/** Precondition: num1 is not equal to num2 */`
    (C) `/** Preconditions: num1 is between Integer.MIN_VALUE and Integer.MAX_VALUE, inclusive. num2 is between Integer.MIN_VALUE and Integer.MAX_VALUE, inclusive. */`
    (D) `/** Precondition: (num1 + num2) is between Integer.MIN_VALUE and Integer.MAX_VALUE, inclusive. */`

    分析与解答：
    溢出发生在表达式结果超出 `int` 的取值范围时。即使 `num1` 和 `num2` 各自在合法范围内，它们的和也可能超出范围。只有确保**和**在 `Integer.MIN_VALUE` 到 `Integer.MAX_VALUE` 之间，才能避免溢出。正确答案是 (D)。

- ### 例题 7 — 整数除法与自动扩宽

    > Source: APCSA 2024 MCQ, Q30

    ```java
    int r = 23;
    int t = 10;
    double a = r % t;
    double b = r / t;
    System.out.println(a + " " + b);
    ```

    What, if anything, is printed?

    (A) 2.0 3.0
    (B) 2.3 3.0
    (C) 3.0 2.0
    (D) 3.0 2.3
    (E) Nothing is printed. A compile-time error occurs because an int value cannot be assigned to a double.

    分析与解答：
    `r % t` = 23 % 10 = 3，赋值给 double a → 自动扩宽为 3.0。`r / t` = 23 / 10 = 2（整数除法，结果截断），赋值给 double b → 自动扩宽为 2.0。输出为 3.0 2.0。int 值可以赋值给 double 变量（自动扩宽），不会编译错误，排除 (E)。正确答案是 (C)。