---
layout: default
title: 1.6 Compound Assignment Operators
parent: Unit 1
nav_order: 6
---

# APCSA Topic 1.6 — Compound Assignment Operators

## 1.6.A 复合赋值运算符（Compound Assignment Operators）

**复合赋值运算符（Compound Assignment Operators）**：Java 提供了一组复合赋值运算符，可将算术运算与赋值合并为一个操作。其通用形式为 `variable op= expression`，等价于 `variable = variable op expression`。

| 运算符 | 用法示例 | 等价于      |
| ------ | -------- | ----------- |
| `+=`   | `x += 5` | `x = x + 5` |
| `-=`   | `x -= 3` | `x = x - 3` |
| `*=`   | `x *= 2` | `x = x * 2` |
| `/=`   | `x /= 4` | `x = x / 4` |
| `%=`   | `x %= 3` | `x = x % 3` |

**后置递增运算符（Post-Increment Operator `++`）**：`x++` 等价于 `x = x + 1`，将变量 x 的值加 1 后再存回 x。

**后置递减运算符（Post-Decrement Operator `--`）**：`x--` 等价于 `x = x - 1`，将变量 x 的值减 1 后再存回 x。

{: .extra}
> **Exclusion statement**：前缀形式（如 `++x`、`--x`）以及将递增/递减运算符嵌入其他表达式中使用（如 `arr[x++]`）均不在 AP CSA 考试范围内。考试中 `++` 和 `--` 仅以独立语句形式出现。

- ### 例题 1 — 复合赋值与递增运算

    > Source: AP Classroom Unit 1 Progress Check MCQ Part B, Q4

    ```
    int x = 0;
    x++;
    x += 1;
    x = x + 1;
    x -= -1;
    System.out.println(x);
    ```

    What is printed when the code segment is executed?

    (A) 1
    (B) 2
    (C) 3
    (D) 4

    分析与解答：
    x 初始化为 0。`x++` 使 x 变为 1；`x += 1` 使 x 变为 2；`x = x + 1` 使 x 变为 3；`x -= -1` 等价于 `x = x - (-1)`，即 `x = x + 1`，使 x 变为 4。最终输出 4。**正确答案是 (D)。** 

- ### 例题 2 — 复合赋值运算符 *= 与 ++

    > Source: AP Classroom Unit 1 Progress Check MCQ Part B, Q5

    Which of the following code segments can be used to print the output 2526?

    (A)

    ```
    int val = 5;
    val *= val;
    System.out.print(val);
    val++;
    System.out.print(val);
    ```

    (B)

    ```
    int val = 5;
    val *= val;
    System.out.print(val);
    val *= 1;
    System.out.print(val);
    ```

    (C)

    ```
    int val = 5;
    val += val;
    System.out.print(val);
    val++;
    System.out.print(val);
    ```

    (D)

    ```
    int val = 5;
    val += val;
    System.out.print(val);
    val *= 1;
    System.out.print(val);
    ```

    分析与解答：
    选项 (A) 中，`val *= val` 等价于 `val = val * val`，5 × 5 = 25，打印 25；`val++` 使 val 变为 26，打印 26，输出 2526。选项 (B) 输出 2525；选项 (C) 输出 1011；选项 (D) 输出 1010。**正确答案是 (A)。**

### 例题 3 — 复合赋值运算符 *= 与调试

> Source: AP Classroom Unit 1 Progress Check MCQ Part B, Q6

```
int x = 0;            // line 1
x++;                  // line 2
System.out.print(x);  // line 3
x += 1;               // line 4
System.out.print(x);  // line 5
x *= 2;               // line 6
System.out.print(x);  // line 7
x *= 4;               // line 8
System.out.print(x);  // line 9
```

The code segment is intended to produce the following output. The code segment does not work as intended.

```
1248
```

Which of the following changes can be made so that the code segment works as intended?

(A) Interchanging lines 2 and 4
(B) Interchanging lines 6 and 8
(C) Changing line 6 to `x += 2;`
(D) Changing line 8 to `x *= 2;`

分析与解答：
当前代码执行过程：x = 0 → `x++` → x = 1，打印 1 → `x += 1` → x = 2，打印 2 → `x *= 2` → x = 4，打印 4 → `x *= 4` → x = 16，打印 16。实际输出为 12416，预期为 1248。将第 8 行 `x *= 4` 改为 `x *= 2` 后，x（此时为 4）乘以 2 得 8，打印 8。**正确答案是 (D)。** [pdf_18]

### 例题 4 — 后置递增与复合赋值组合

> Source: AP Classroom New Unit 1 Topic Questions MCQ, Q20

```
int a = 4;
int b = 5;
a++;
b++;
int c = a + b;
a -= 1;
System.out.println(a + c);
```

What is printed as a result of executing the code segment?

(A) 10
(B) 13
(C) 14
(D) 15

分析与解答：
a = 4，b = 5。`a++` 使 a 变为 5；`b++` 使 b 变为 6。`c = a + b = 5 + 6 = 11`。`a -= 1` 等价于 `a = a - 1 = 5 - 1 = 4`。`a + c = 4 + 11 = 15`，输出 15。**正确答案是 (D)。** [pdf_17]