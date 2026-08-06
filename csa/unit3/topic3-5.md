---
layout: default
title: "3.5 Methods: How to Write Them"
parent: Unit 3
nav_order: 5
---

# 3.5 — Methods: How to Write Them

## 3.5.A 方法的组成

**方法（Method）** 定义类的一个行为。方法声明包括：

{% raw %}
```java
public double getPrice()     // 访问修饰符 + 返回类型 + 方法名 + 参数列表
{
    return price;            // 方法体（return 语句返回结果）
}
```
{% endraw %}

- **返回类型（return type）**：`void` 表示不返回任何值；其他类型（如 `int`、`double`、`String`）必须用 `return` 返回匹配类型的值。
- **参数（parameters）**：方法需要的输入。
- **方法体（body）**：实现方法功能的语句。

{: .important}
> - 返回类型为 `void` 的方法**不能**用 `return 值;`。
> - 返回类型非 void 的方法**必须**在所有路径上都有 `return` 语句。
> - 方法内可以访问**实例变量**，也可以声明**局部变量**。

## 3.5.B 访问器与修改器方法

- **访问器方法（Accessor Method）**：让外部类**获取**实例变量/类变量的**值副本**，是**非 void** 方法（有返回值）。如 `getPrice()`。
- **修改器方法（Mutator Method）**：**改变**实例变量/类变量的值，通常（但不一定）是 **void** 方法。如 `setPrice(double p)`、`updateX(int amount)`。

{% raw %}
```java
public double getPrice()              // 访问器：返回值副本
{
    return price;
}

public void setPrice(double newPrice) // 修改器：改变实例变量
{
    price = newPrice;
}
```
{% endraw %}

## 3.5.C 编写方法时常见错误

- 方法返回类型的错误（该 void 却 return 值）。
- 引用了未定义的变量（如把构造方法的参数当作方法内变量）。
- 局部变量遮蔽实例变量。
- 局部变量不能在方法内声明 `public`/`private`（局部变量没有访问修饰符）。

- ### 例题 1 — 方法修改实例变量

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q1

  Consider the following class definition.

{% raw %}
  ```java
  public class MyClass
  {
      private int x;

      public MyClass(int start)
      {
          x = start;
      }

      public void updateX(int amount)
      {
          x += amount;
      }
  }
  ```
{% endraw %}

  Suppose that tester is a properly instantiated reference to a MyClass object and num is an int value. Which of the following best describes the conditions under which the value of the instance variable x is unchanged as a result of the call `tester.updateX(num)`?

  (A) When num is 0  
  (B) When num is 1  
  (C) When num is positive.  
  (D) When num is negative

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `updateX` 把 amount 加到 x 上。当 num = 0 时，`x += 0` 不改变 x 的值。正确答案是 **(A)**。

  </details>

- ### 例题 2 — return 字符串拼接

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q2

  Consider the following class definition.

{% raw %}
  ```java
  public class XYPoint
  {
      private int x;
      private int y;

      public XYPoint(int xVal, int yVal)
      {
          x = xVal;
          y = yVal;
      }

      public String getPoint()
      {
          /* missing code */
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than XYPoint.

  ```java
  XYPoint p1 = new XYPoint(3, -2);
  XYPoint p2 = new XYPoint(4, 0);
  System.out.println(p1.getPoint());
  System.out.println(p2.getPoint());
  ```

  This code segment is intended to produce the following output.

  ```
  (3, -2)
  (4, 0)
  ```

  Which of the following statements can be used to replace `/* missing code */` so that this code segment produces the intended output?

  (A) `System.out.println("(x, y)");`  
  (B) `System.out.println("(" + x + ", " + y + ")");`  
  (C) `return "(x, y)";`  
  (D) `return "(" + x + ", " + y + ")";`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    getPoint 的返回类型是 String，应使用 `return` 返回格式化的字符串，用实例变量 x、y 的实际值拼接。选项 (D) `return "(" + x + ", " + y + ")";` 正确。选项 (A)(B) 使用 println 输出而非 return，且 (A) 返回字面量 "(x, y)" 不含实际值。正确答案是 **(D)**。

  </details>

- ### 例题 3 — 除零异常

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q3

  Consider the following class definition.

{% raw %}
  ```java
  public class Fraction
  {
      private int numerator;
      private int denominator;

      public Fraction(int n, int d)
      {
          numerator = n;
          denominator = d;
      }

      double getDecimal()
      {
          return (double) numerator / denominator;
      }
  }
  ```
{% endraw %}

  Suppose that `fr` is a properly instantiated reference to a Fraction object. Which of the following best describes the conditions under which the call `fr.getDecimal()` will fail to return a value?

  (A) When the instance variables numerator and denominator have the same value  
  (B) When the instance variables numerator and denominator have different values  
  (C) When the instance variable denominator is equal to 0  
  (D) When the instance variable denominator is negative

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `getDecimal` 执行除法 `numerator / denominator`。当分母 `denominator` 为 0 时抛出 `ArithmeticException`，方法无法正常返回。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 方法实现（RentalCar）

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q4

  Consider the following class definition.

{% raw %}
  ```java
  public class RentalCar
  {
      private double dailyRate;    // the fee per rental day
      private double mileageRate;  // the fee per mile driven

      public RentalCar(double daily, double mileage)
      {
          dailyRate = daily;
          mileageRate = mileage;
      }

      public double calculateFee(int days, int miles)
      {
          /* missing code */
      }
  }
  ```
{% endraw %}

  The calculateFee method is intended to calculate the total fee for renting a car. The total fee is equal to the number of days of the rental, days, times the daily rental rate plus the number of miles driven, miles, times the per mile rate.

  Which of the following code segments can be used to replace `/* missing code */` so that the calculateFee method works as intended?

  (A) `return dailyRate + mileageRate;`  
  (B) `return (daily * dailyRate) + (mileage * mileageRate);`  
  (C) `return (daily * days) + (mileage * miles);`  
  (D) `return (days * dailyRate) + (miles * mileageRate);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    总费用 = 天数 × 每日费率 + 英里数 × 每英里费率。每日费率存在实例变量 `dailyRate`，每英里费率存在 `mileageRate`，天数和英里数是参数 days、miles。选项 (D) `return (days * dailyRate) + (miles * mileageRate);` 正确。选项 (B)(C) 引用了未定义的 daily/mileage。正确答案是 **(D)**。

  </details>

- ### 例题 5 — 局部变量不能有访问修饰符

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q9

  Consider the following class definition.

{% raw %}
  ```java
  public class Circle
  {
      private double radius;

      public double computeArea()
      {
          private double pi = 3.14159;
          public double area = pi * radius * radius;
          return area;
      }
  }
  ```
{% endraw %}

  Which of the following best explains why the computeArea method will not compile?

  (A) Local variables declared inside a method cannot be declared as public or private.  
  (B) Local variables declared inside a method must all be private.  
  (C) Local variables declared inside a method must all be public.  
  (D) Local variables used inside a method must be declared before the method header.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    方法内部的**局部变量**不能使用 `public` 或 `private` 访问修饰符——只有实例变量（类成员）才能有访问修饰符。正确答案是 **(A)**。

  </details>

- ### 例题 6 — 未定义变量

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q10

  Consider the following class definition. The class does not compile.

{% raw %}
  ```java
  public class Info
  {
      private String name;
      private int number;

      public Info(String n, int num)
      {
          name = n;
          number = num;
      }

      public void changeName(String newName)
      {
          name = newName;
      }

      public int addNum(int n)
      {
          num += n;
          return num;
      }
  }
  ```
{% endraw %}

  Which of the following best explains why the class will not compile?

  (A) The class is missing an accessor method.  
  (B) The instance variables name and number should be designated public instead of private.  
  (C) The return type for the Info constructor is missing.  
  (D) The variable num is not defined in the addNum method.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `num` 只是构造方法的参数，只在构造方法内有效。addNum 方法中使用 `num` 时它并未被定义（实例变量是 `number` 而不是 `num`），导致编译错误。正确答案是 **(D)**。

  </details>

- ### 例题 7 — void 方法不能 return 值

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q14

  Consider the following class definition. The raisePrice method is intended to increase the value of the instance variable price by the value of the parameter amount. The method does not work as intended.

{% raw %}
  ```java
  public class Toy
  {
      private String name;
      private double price;

      public Toy(String n, double p)
      {
          name = n;
          price = p;
      }

      public void raisePrice(double amount)   // Line 12
      {
          return price + amount;              // Line 14
      }
  }
  ```
{% endraw %}

  Which of the following changes can be made so that the Toy class compiles without error and the method raisePrice works as intended?

  (A) Replacing line 12 with `public raisePrice(double amount)`  
  (B) Replacing line 12 with `public double raisePrice(double amount)`  
  (C) Replacing line 14 with `price += amount;`  
  (D) Replacing line 14 with `return price += amount;`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    raisePrice 的目的是**修改**实例变量 price，是 void 的 mutator 方法，不应该返回值。第 14 行应改为 `price += amount;`（没有 return）。选项 (C) 正确。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                     |
| ------------------ | -------------------------------------------- | -------------------------------------------- |
| 方法声明           | 修饰符 + 返回类型 + 方法名 + 参数列表 + 方法体 | void 不返回值                               |
| return 语句        | 非 void 必须返回匹配类型的值                 | return 值用于访问器方法                       |
| 局部变量           | 方法内声明，无访问修饰符                     | 局部变量不能 public/private                   |
| 未定义变量         | 方法内只能使用参数、局部变量、实例变量       | 构造方法参数在其他方法中不可用                 |
| 方法类型选择       | mutator 用 void，accessor 用返回类型         | raisePrice 是修改 → void + `price += amount`  |
