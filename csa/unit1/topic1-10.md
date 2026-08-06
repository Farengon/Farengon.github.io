---
layout: default
title: 1.10 Calling Class Methods
parent: Unit 1
nav_order: 10
---

# 1.10 — Calling Class Methods

## 1.10.A 类方法（Class Methods / Static Methods）

**类方法（Class Method）** 也称为 **static 方法**，它与**类**相关联，而不是与类的某个具体对象相关联。类方法用关键字 `static` 声明，通过**类名 + 点运算符**调用：

```java
int c = AccountManager.generatePasscode();   // 通过类名调用
double tax = PurchaseManager.getTax(100.0);  // 同类内部可直接调用
```

{: .important}
> - 类方法用 `类名.方法名(实参)` 调用。
> - 在**同一个类**内部调用自己的 static 方法时，可以省略类名。
> - 方法有返回值时，返回值必须能被赋值给类型兼容的变量。

## 1.10.B 类方法调用的编译规则

- 通过**类名**调用方法，说明该方法必须是 `static`。
- 通过**对象名**调用方法，说明该方法是非 static 的实例方法。
- 返回值类型必须与接收变量的类型兼容（`double` 返回值可以赋给 `double` 变量）。

- ### 例题 1 — 在其他类中调用 static 方法

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q1

  Consider the following information about the calculateBill method.

  - The method is a static method in the Store class.
  - The method has one int parameter.
  - The method has return type double.
  - The method can be accessed from another class.

  Which of the following code segments, when appearing in a method in a class other than Store, will compile without error?

  (A) `double tot = calculateBill(5);`  
  (B) `double tot = Store.calculateBill(5);`  
  (C) `double tot;` / `tot.calculateBill(5);`  
  (D) `double tot = 5.0;` / `tot.calculateBill();`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    calculateBill 是 Store 类的 static 方法，在其他类中必须用 `Store.calculateBill(5)` 调用（类名 + 点运算符）。实参 5 是合法的 int，返回值 double 赋给 double 变量也匹配。选项 (A) 缺少类名前缀；(C)(D) 错误地"调用"了变量。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 同类内部调用 static 方法

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q2

  Consider the following information about the getTax method.

  - The method is a static method in the PurchaseManager class.
  - The method has one double parameter.
  - The method returns a double equal to its parameter times 0.08.

  The following code segment appears in another method in the PurchaseManager class.

  ```java
  double tax = getTax(100.0);
  System.out.println(tax);
  ```

  What, if anything, is printed as a result of executing the code segment?

  (A) 8.0  
  (B) 108.0  
  (C) Nothing is printed because the method call should be `PurchaseManager.getTax(100.0)`.  
  (D) Nothing is printed because the return value from getTax cannot be assigned to the variable tax.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    方法返回 `100.0 * 0.08 = 8.0`。由于调用代码与 getTax 在**同一个类** PurchaseManager 中，可以直接用方法名调用，无需类名前缀。返回值 8.0 可以赋给 double 变量 tax。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 类名调用要求 static

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q3

  Consider the following information about the generatePasscode method.

  - The method appears in the AccountManager class.
  - The method has no parameters.
  - The method has return type int.
  - The method can be accessed from another class.

  The following code segment appears in a method in a class other than AccountManager class.

  ```java
  int c = AccountManager.generatePasscode();
  System.out.println(c);
  ```

  Which of the following must be true for the code segment to compile without error?

  (A) The generatePasscode method should be designated as void.  
  (B) The generatePasscode method should be designated as static.  
  (C) The AccountManager class should contain another method with the name generatePasscode that has at least one parameter.  
  (D) The AccountManager class should contain another method with the name generatePasscode that has return type double.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    代码用 `AccountManager.generatePasscode()`（类名 + 点运算符）调用，这说明该方法与类相关联，必须声明为 **static**。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 类方法（static） | 与类关联，用 `类名.方法名()` 调用            | 用类名调用 → 方法必须是 static                 |
| 同类内部调用     | 同类中可直接调用本类的 static 方法           | 无需写类名前缀                                 |
| 返回值匹配       | 返回值类型必须与接收变量兼容                 | `double` 返回值 → `double` 变量                |
| 实例方法 vs 类方法 | 用对象调用的是实例方法；用类名调用的是类方法 | 混用会导致编译错误                             |
