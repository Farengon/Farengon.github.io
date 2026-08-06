---
layout: default
title: 4.7 Wrapper Classes
parent: Unit 4
nav_order: 7
---

# 4.7 — Wrapper Classes

## 4.7.A 包装类（Wrapper Classes）

**包装类（Wrapper Class）** 把基本类型包装成对象。AP CSA 涉及 `Integer` 和 `Double`：

| 基本类型 | 包装类    | 说明                     |
| -------- | --------- | ------------------------ |
| int      | Integer   | 包装 int 值              |
| double   | Double    | 包装 double 值           |

{: .note}
> `Integer` 和 `Double` 类属于 `java.lang` 包，**默认可用，无需 import**。包装对象是**不可变（immutable）**的——创建后其值不能再改变。

**自动装箱（Autoboxing）与自动拆箱（Unboxing）：**

- **装箱**：`Double d1 = new Double(7.5);` 或 `Integer i = 5;`（自动装箱：int → Integer）。
- **拆箱**：把包装类对象赋给基本类型变量时，Java 自动取出其中的值：`double x = d1;`。

{: .important}
> 把 `Double`（包装类）传给 `double` 形参的方法时，Java 会自动**拆箱**，方法正常执行。

## 4.7.B 字符串与数值的转换

| 方法                          | 作用                     | 示例                                      |
| ----------------------------- | ------------------------ | ----------------------------------------- |
| `Integer.parseInt(str)`       | 字符串 → int             | `Integer.parseInt("34")` → 34             |
| `Double.parseDouble(str)`     | 字符串 → double          | `Double.parseDouble("34")` → 34.0         |

- ### 例题 1 — parseDouble 的使用

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q4

  Which of the following statements will store the value 34.0 in the double variable value?

  (A) `double value = (double) "34";`  
  (B) `double value = Double.parseDouble("34");`  
  (C) `double value = Integer.parseInt("34") + ".0";`  
  (D) `double value = Double.parseDouble("34") + ".0";`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `Double.parseDouble("34")` 把字符串 "34" 解析为 double 值 34.0。选项 (A) 不能把 String 强转为 double；(C) 结果是字符串拼接；(D) 得到 "34.0" 字符串无法赋给 double。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 自动拆箱

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part B, Q5

  Consider the following calculate method.

{% raw %}
  ```java
  public double calculate(double x)
  {
      return x + 1.5;
  }
  ```
{% endraw %}

  The following code segment calls the method calculate in the same class.

  ```java
  Double d1 = new Double(7.5);
  System.out.println(calculate(d1));
  ```

  What, if anything, is printed when the code segment is executed?

  (A) 8.5  
  (B) 9  
  (C) 9.0  
  (D) Nothing is printed because the code does not compile. The actual parameter d1 passed to calculate is a Double, but the formal parameter x is a double.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `d1` 是 Double 包装类对象，值 7.5。calculate 的形参是基本类型 `double`，Java 自动**拆箱**，取出 7.5 传给方法。7.5 + 1.5 = 9.0，打印 9.0。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 包装类           | Integer、Double 包装基本类型                 | 装箱：基本 → 包装；拆箱：包装 → 基本          |
| 自动拆箱         | Double 对象可传给 double 形参                | 不会编译错误                                   |
| 字符串转数值     | Integer.parseInt / Double.parseDouble        | 返回对应基本类型值                             |
| 强制转换限制     | 不能 `(double)` 转换字符串                   | 字符串 → 数值必须用 parse 方法                 |
