---
layout: default
title: 1.8 Documentation with Comments
parent: Unit 1
nav_order: 8
---

# 1.8 — Documentation with Comments

## 1.8.A 注释（Comments）与文档

**注释（Comments）** 是程序代码中写给人类阅读的说明文字，Java 编译器会**忽略**它们。注释不会影响程序的运行，但能显著提高代码的可读性和可维护性。

Java 中的三种注释形式：

```java
// 单行注释
/* 多行
   注释 */
/** Javadoc 注释（生成 API 文档用） */
```

**Javadoc 注释**（以 `/**` 开头）还可以被工具自动提取生成 API 文档。在 Javadoc 注释中，我们经常用 `@param` 描述方法参数、用 `@return` 描述返回值、用 **Precondition（前置条件）** 描述方法调用前必须满足的条件。

{: .note}
> **Precondition（前置条件）** 是指方法能够正确工作前必须为真的条件。例如，除法方法的前置条件可以是"除数不为 0"。前置条件通常写在方法上方，告诉调用者如何安全地调用该方法。

## 1.8.B 前置条件（Preconditions）

前置条件的常见用途是**防止错误发生**：

- 防止**溢出（overflow）**：要求 `num1 + num2` 在 `int` 的取值范围内。
- 防止**运行时异常**：要求除数 `y != 0`，避免 `ArithmeticException`。
- 保证**输出正确**：要求 `x > y`，确保 `x - y` 为正。

- ### 例题 1 — 防止溢出（Overflow）

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q10

  The following code segment appears in a method. In the code segment, num1 and num2 are int variables. The method is intended to print the sum of num1 and num2.

  ```java
  int result = num1 + num2;
  System.out.println(result);
  ```

  Which of the following preconditions for the method is most appropriate to avoid an overflow error?

  (A) `/** Precondition: num1 and num2 are both positive. */`  
  (B) `/** Precondition: num1 is not equal to num2 */`  
  (C) `/** Preconditions: num1 is between Integer.MIN_VALUE and Integer.MAX_VALUE, inclusive; num2 is between Integer.MIN_VALUE and Integer.MAX_VALUE, inclusive. */`  
  (D) `/** Precondition: (num1 + num2) is between Integer.MIN_VALUE and Integer.MAX_VALUE, inclusive. */`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    溢出错误发生在表达式的结果超出 `int` 的取值范围（小于 `Integer.MIN_VALUE` 或大于 `Integer.MAX_VALUE`）时。即使 num1 和 num2 各自都在范围内，它们的和也可能溢出（例如两个很大的正数相加）。因此正确的前置条件应限制**和**的范围，即选项 (D)。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 防止 ArithmeticException

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q11

  The following code segment appears in a method. In the code segment, `y` is an int variable.

  ```java
  int x = 5 / y;
  System.out.println(x);
  ```

  Which of the following preconditions for the method is most appropriate to avoid an ArithmeticException?

  (A) `/** Precondition: y is equal to 0. */`  
  (B) `/** Precondition: y is less than 5. */`  
  (C) `/** Precondition: y is not equal to 0. */`  
  (D) `/** Precondition: y is not negative. */`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    整数除以 0 会抛出 `ArithmeticException`。要避免该异常，只需保证除数 `y` 不等于 0。选项 (C) 正确。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 保证输出为正

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q12

  The following code segment appears in a method. In the code segment, x and y are double variables.

  ```java
  double result = (x - y) / 2.0;
  System.out.println(result);
  ```

  Which of the following preconditions for the method is most appropriate to ensure that the value printed by the code segment is always positive?

  (A) `/** Precondition: x and y are both positive. */`  
  (B) `/** Precondition: x and y are both even. */`  
  (C) `/** Precondition: x > y */`  
  (D) `/** Precondition: x < y */`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
  若要 `(x - y) / 2.0` 恒为正，则必须 `x - y > 0`，即 `x > y`。选项 (C) 正确。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 综合前置条件判断

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q13

  The following code segment appears in a method. In the code segment, x and y are properly declared and initialized int variables.

  ```java
  System.out.println(x * x * y);
  ```

  Which of the following preconditions for the method is most appropriate to ensure that the value printed by the code segment is always greater than zero?

  (A) x is greater than zero; y is not equal to zero.  
  (B) x is not equal to zero; y is greater than zero.  
  (C) x is even and is not equal to zero; y is not equal to zero.  
  (D) x is not equal to zero; y is even and is not equal to zero.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    无论 x 是正还是负，`x * x` 都是正的；但若 x = 0，则 `x * x * y = 0`，不是正数，所以 x 不能为 0。要让整个乘积为正，只需 y > 0（y 的符号决定最终结果符号）。选项 (B) 正确。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                       | 考试提示                                             |
| ------------------ | ---------------------------------------------- | ---------------------------------------------------- |
| 注释的作用         | 编译器忽略注释；注释提高可读性                 | `//`、`/* */`、`/** */` 三种形式                      |
| Javadoc            | `/** */` 可生成 API 文档，含 `@param`/`@return` | 常见于类与方法的文档说明                             |
| Precondition       | 方法工作前必须为真的条件                       | 通常写在方法上方，用 `/** ... */` 描述               |
| 前置条件的设计     | 防溢出、防除零、保证结果正确                   | 溢出要看**结果**范围；除零要求除数 ≠ 0               |
