---
layout: default
title: 1.1 Introduction to Algorithms, Programming, and Compilers
parent: Unit 1
nav_order: 1
---

# 1.1 — Introduction to Algorithms, Programming, and Compilers

---

## 1.1.A 算法与程序

**算法（Algorithm）** 是一组有限的、明确的步骤，用于解决一个问题或完成一个任务。算法**不依赖于特定的编程语言**——我们可以用自然语言、流程图或伪代码来描述它。

**程序（Program）** 是用某种编程语言实现的算法。一个程序将算法翻译成计算机能够理解和执行的指令。

{: .note}
> 同一个算法可以用不同的编程语言实现，但算法本身的逻辑保持不变。

- ### 例题 1 — 用文字描述算法

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part A, Q1

  A certain algorithm assigns each integer to a string, as given below.

  - For each integer from 1 to 3, the string is the integer itself. For example, the integer 1 is assigned to the string "1".
  - For each integer greater than 3, the string is "too many".

  Which of the following best describes the behavior of the algorithm?

  (A) The algorithm prints the string assigned to the integer 5.  
  (B) The algorithm prints the string assigned to the integer 3.  
  (C) The algorithm assigns a string to the integer 5.  
  (D) The algorithm assigns a string to each integer from 1 to 5.

  <details markdown="block>
    <summary><b>点击查看解答</b></summary>
  
    **分析与解答：**  
    题目描述了一个算法：对于 1 到 3 的整数，分别赋值为该整数本身对应的字符串；对于大于 3 的整数，赋值为 "too many"。题目问的是算法的行为描述。选项 (A) 和 (B) 使用了"prints"（打印输出），但算法描述中只说了"assigns"（赋值），并未涉及输出。选项 (C) 只描述了赋值给 5 这一个整数，范围过窄。选项 (D) 正确地描述了算法给 1 到 5 的每个整数都进行了赋值。因此正确答案是 **(D)**。

  </details>

- ### 例题 2 — 用步骤描述算法

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part A, Q2

  A certain algorithm is described as follows:

  **Step 1:** Compute the value of `num1 + num2`.
  **Step 2:** Divide the sum from Step 1 by 2.
  **Step 3:** Compute the value of `num1 * num2`.
  **Step 4:** Divide the result from Step 3 by the result from Step 2.

  Which of the following best describes the result of this algorithm?

  (A) The algorithm computes the product of the two numbers divided by the average of the two numbers.  
  (B) The algorithm computes the average of the two numbers.  
  (C) The algorithm computes the product of the two numbers added to the average of the two numbers.  
  (D) The algorithm computes the sum of the two numbers divided by the product of the two numbers.  

  <details markdown="block>
    <summary><b>点击查看解答</b></summary>
  
    **分析与解答：**  
    让我们一步步追踪：

    - Step 1: `num1 + num2`（两数之和）
    - Step 2: `(num1 + num2) / 2`（两数的平均值）
    - Step 3: `num1 * num2`（两数之积）
    - Step 4: `(num1 * num2) / ((num1 + num2) / 2)`（积除以平均值）

    因此，最终结果是两数之积除以两数的平均值。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 用流程图描述算法

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part A, Q3

  Consider the following algorithm that uses the integer variables `a`, `b`, and `c`.

  **Step 1:** Set `a` to 1.
  **Step 2:** Set `b` to 2.
  **Step 3:** Set `c` to `a + b`.
  **Step 4:** Display the value of `c`.

  Which of the following is the same algorithm described in a different way?

  (A) Set `a` to 1. Set `b` to 2. Set `c` to `a * b`. Display `c`.  
  (B) Set `a` to 1. Set `b` to 2. Set `c` to `a + b`. Display `c`.  
  (C) Set `a` to 2. Set `b` to 1. Set `c` to `a + b`. Display `c`.  
  (D) Set `a` to 1. Set `b` to 2. Set `c` to `a + b`. Display `a + b`.  

  <details markdown="block>
    <summary><b>点击查看解答</b></summary>
  
    **分析与解答：**  
    同一个算法意味着相同的步骤序列。原算法执行：

    1. a = 1
    2. b = 2
    3. c = a + b（即 1 + 2 = 3）
    4. 显示 c 的值（即 3）

    选项 (B) 完全匹配。注意选项 (D) 虽然计算相同，但最后一步显示的是 `a + b` 而不是 `c`，所以描述方式不同，输出**行为**可能不同（题目问的是"described in a different way"即不同的描述方式，这里 (D) 改变的是输出方式，与原算法不等价）。正确答案是 **(B)**。

  </details>

---

## 1.1.B 从源代码到可执行程序

**编程过程：** 程序员编写 **源代码（source code）** → 保存在 `.java` 文件中 → 使用 **编译器（compiler）** 翻译成字节码（bytecode, `.class` 文件）→ Java 虚拟机（JVM）执行字节码。

**集成开发环境（IDE）：** 如 Eclipse、IntelliJ、VS Code、AP CSA 考试中使用的 **Java 环境**。IDE 集成了编辑器、编译器、调试器和错误检查工具，帮助程序员更高效地编写和调试代码。

**关键流程：**

```
源代码 (.java) → [编译器 (javac)] → 字节码 (.class) → [JVM (java)] → 运行结果
```

{: .note}
> **为什么 Java 需要编译 + 执行两个步骤？**  
> Java 编译一次生成字节码，字节码可以在任何安装了 JVM 的平台上运行（"Write Once, Run Anywhere"）。编译阶段可以提前发现语法错误，避免程序在运行时崩溃。

---

## 1.1.C 编程错误类型

AP CSA 考试中，编程错误分为三大类：

| 错误类型       | 英文术语                       | 解释                                                         | 检测时机                     |
| -------------- | ------------------------------ | ------------------------------------------------------------ | ---------------------------- |
| **语法错误**   | **Syntax Error**               | 违反编程语言的语法规则，如漏写分号、花括号不匹配、拼写错误关键字 | 编译时（编译器检测）         |
| **逻辑错误**   | **Logic Error**                | 程序能运行，但结果不正确，如公式写错、条件判断用反           | 运行时（不报错，但输出错误） |
| **运行时错误** | **Run-Time Error**             | 程序在运行过程中崩溃，如除以零、数组越界                     | 运行时（程序崩溃）           |

**Exception**是一种运行时错误。本课程后续涉及的异常有：

- [ArithmeticException](/csa/unit1/topic1-3.md#除零错误)

- ### 例题 4 — 识别逻辑错误

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part A, Q4

  Consider the following algorithm.

  **Step 1:** Read the number `num`.
  **Step 2:** Set `result` to `num * 2`.
  **Step 3:** Display `result`.

  The algorithm is intended to display the square of the number `num`. Which of the following best describes the error in the algorithm?

  (A) The algorithm contains a syntax error.  
  (B) The algorithm contains a logic error.  
  (C) The algorithm contains a run-time error.  
  (D) The algorithm contains no errors.  

  <details markdown="block>
    <summary><b>点击查看解答</b></summary>
  
    **分析与解答：**  
    算法的目的是计算 `num` 的平方（`num * num`），但实际计算的是 `num * 2`（两倍）。程序可以正常执行，不会编译报错，也不会崩溃，但输出的结果不是预期的平方值。这种错误属于**逻辑错误**。正确答案是 **(B)**。

  </details>

- ### 例题 5 — 识别语法错误

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part A, Q5

  Consider the following code segment.

  ```java
  int a = 5
  int b = 10;
  int c = a + b;
  System.out.println(c);
  ```

  Which of the following best describes the error in the code segment?

  (A) The code segment contains a syntax error.  
  (B) The code segment contains a logic error.  
  (C) The code segment contains a run-time error.  
  (D) The code segment contains no errors.  

  <details markdown="block>
    <summary><b>点击查看解答</b></summary>
  
    **分析与解答：**  
    在 Java 中，每条语句必须以分号（`;`）结束。`int a = 5` 后面缺少了分号，这是一个**语法错误**，编译器会在编译时检测到并报错。正确答案是 **(A)**。

  </details>

- ### 例题 6 — 识别运行时错误

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part A, Q6

  Consider the following code segment.

  ```java
  int x = 10;
  int y = 0;
  int z = x / y;
  System.out.println(z);
  ```

  Which of the following best describes the error in the code segment?

  (A) The code segment contains a syntax error.  
  (B) The code segment contains a logic error.  
  (C) The code segment contains a run-time error.  
  (D) The code segment contains no errors.

  <details markdown="block>
    <summary><b>点击查看解答</b></summary>
  
    **分析与解答：**  
    语法上没有错误。但执行到 `x / y` 时，`y = 0`，在 Java 中整数除以零会抛出 `ArithmeticException`，导致程序崩溃。这是一个**运行时错误**。正确答案是 **(C)**。

  </details>
