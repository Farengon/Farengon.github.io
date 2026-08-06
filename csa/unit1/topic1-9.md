---
layout: default
title: 1.9 Method Signatures
parent: Unit 1
nav_order: 9
---

# 1.9 — Method Signatures

## 1.9.A 方法签名（Method Signature）

**方法签名（Method Signature）** 由**方法名**、**参数的数量、类型和顺序**组成（返回值类型不属于方法签名的一部分，但通常与方法签名一起出现在方法的完整声明中）。

```java
public void printSum(int x, double y)   // 签名：printSum(int, double)
public void printProduct(double x, int y) // 签名：printProduct(double, int)
```

{: .important}
> 调用方法时，实参（actual argument）必须与形参（formal parameter）在**数量、类型、顺序**上匹配，否则代码无法编译。

## 1.9.B 方法调用与参数传递

- 调用方法时，实参的值被复制给形参（**值传递**，pass by value）。
- 方法返回类型 `void` 表示方法不返回任何值。
- 同一个类中可以直接用方法名调用；带对象的方法用 `对象.方法(实参)` 调用。

- ### 例题 1 — 方法间调用与参数传递

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q13

  Consider the following descriptions of two methods that appear in the same class.

  | Method Signature            | Explanation                                             |
  | --------------------------- | ------------------------------------------------------- |
  | `public void methodA(int arg)` | Calls methodB with the value of `arg * 10`              |
  | `public void methodB(int arg)` | Displays the value of `arg + 10`                        |

  Consider the call `methodA(4)`, which appears in a method in the same class. What, if anything, is printed as a result of the call `methodA(4)`?

  (A) 40  
  (B) 50  
  (C) 140  
  (D) Nothing is printed.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `methodA(4)` 把 4 存入形参 arg，然后调用 `methodB(arg * 10)`，即 `methodB(40)`。`methodB(40)` 计算 `40 + 10 = 50` 并打印。最终输出 50。正确答案是 **(B)**。

  </details>

- ### 例题 2 — void 方法与多次调用

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q14

  Consider the following description of method printValues.

  | Method Signature                       | Explanation                                                              |
  | -------------------------------------- | ------------------------------------------------------------------------ |
  | `public void printValues(int numTimes, int val)` | Prints the value of val a total of numTimes times, then moves the cursor to a new line. |

  Consider the following code segment, which appears in the same class as printValues.

  ```java
  printValues(2, 3);
  printValues(4, 5);
  ```

  What is printed as a result of executing the code segment?

  (A) `222` then `44444`  
  (B) `222` then `33333`  
  (C) `33` then `5555`  
  (D) `55` then `4444`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    第一次调用 `printValues(2, 3)`：numTimes = 2，val = 3，打印 `33`；第二次调用 `printValues(4, 5)`：numTimes = 4，val = 5，打印 `5555`。正确答案是 **(C)**。

  </details>

- ### 例题 3 — boolean 参数的方法

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q15

  Consider the following description of method printSomething.

  | Method Signature                         | Explanation                                             |
  | ---------------------------------------- | ------------------------------------------------------- |
  | `public void printSomething(int num, boolean val)` | Prints the value of val immediately followed by the value of `num - 1`. |

  Consider the following code segment, which appears in the same class as printSomething.

  ```java
  printSomething(1, true);
  printSomething(2, true);
  ```

  What is printed as a result of executing the code segment?

  (A) `0true1true`  
  (B) `1true2true`  
  (C) `true0true1`  
  (D) `true1true2`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    第一次调用 `printSomething(1, true)`：val = true，num - 1 = 0，输出 `true0`；第二次调用 `printSomething(2, true)`：val = true，num - 1 = 1，输出 `true1`。合并为 `true0true1`。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 实参类型必须匹配形参

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q23

  Consider the following method signatures.

  | Method Signature                  | Explanation                 |
  | --------------------------------- | --------------------------- |
  | `public void printSum(int x, double y)`   | Prints the sum of x and y  |
  | `public void printProduct(double x, int y)` | Prints the product of x and y |

  Consider the following code segment.

  ```java
  int num1 = 5;
  double num2 = 10.0;
  printSum(num1, num2);
  System.out.println();
  printProduct(num1, num2);
  ```

  What, if anything, is printed as a result of executing the code segment?

  (A) `15` then `50`  
  (B) `15` only  
  (C) `50` only  
  (D) Nothing is printed because the code does not compile.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `printProduct(double, int)` 要求第二个实参是 `int`，但代码传入的 `num2` 是 `double`。实参类型与形参不匹配导致**编译错误**，整个代码段无法运行。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                         |
| ------------------ | -------------------------------------------- | ------------------------------------------------ |
| 方法签名           | 方法名 + 参数的数量、类型、顺序              | 返回值类型不属于签名                             |
| 实参 vs 形参       | 实参的值复制给形参（值传递）                 | 实参必须与形参在数量、类型、顺序上匹配           |
| void 方法          | 不返回值，只执行操作                         | 调用后不能用在赋值语句右侧                       |
| 类型匹配           | `int` 实参可传给 `double` 形参，反之不行     | double 实参传给 int 形参 → 编译错误              |
