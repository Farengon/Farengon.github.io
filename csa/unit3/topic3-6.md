---
layout: default
title: "3.6 Methods: Passing and Returning References of an Object"
parent: Unit 3
nav_order: 6
---

# 3.6 — Methods: Passing and Returning References of an Object

## 3.6.A 引用传递（Passing References）

当**对象**作为方法参数传递时，传的是对象的**引用（内存地址）**——方法内对对象所做的修改会**影响原对象**。

{: .note}
> - **基本类型**按值传递：方法内修改参数不会影响原变量。
> - **对象（引用类型）**按引用传递：方法内通过引用修改对象的属性，会**反映到原对象**上。
> - 传递对象引用时，参数被初始化为**该引用的副本**——不会创建对象的独立副本；若参数指向**可变对象**，方法内对它的修改会影响原对象（EK 3.6.A.1）。
> - **String 是不可变对象**：方法内对 String 参数的"修改"实际是创建新字符串，原 String 不变。

## 3.6.B 返回引用（Returning References）

方法可以返回对象的引用——返回的是**原对象的引用**，而不是新副本（EK 3.6.A.2）。私有数据（private 实例变量）只有在**类内部**的方法中才能直接访问。

{: .important}
> **私有访问限制（EK 3.6.A.3）：** 方法**不能**访问参数所引用对象的私有数据和方法——**除非**该参数的类型与方法所属的类是**同一个类**（即方法定义在持有该私有数据的类内部）。

- ### 例题 1 — String 不可变与引用返回

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q4

  Consider the following method.

  ```java
  public String mystery(String message, int x)
  {
      message = message.substring(x);
      return message;
  }
  ```

  The following code segment appears in a method in the same class as mystery.

  ```java
  String str1 = "abcde";
  String str2 = mystery(str1, 3);
  ```

  Which of the following best describes the behavior of this code segment?

  (A) str1 is modified by the call to mystery; str1 and str2 are equal in value after executing the code segment.  
  (B) str1 is modified by the call to mystery; str1 and str2 have differing values after executing the code segment.  
  (C) str1 is not modified by the call to mystery; str1 and str2 are equal in value after executing the code segment.  
  (D) str1 is not modified by the call to mystery; str1 and str2 have differing values after executing the code segment.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    String 不可变，方法中 `message = message.substring(x)` 只是让局部参数 message 指向新字符串，**不会修改 str1**。方法返回的 "de" 赋给 str2，所以 str1 = "abcde"、str2 = "de"，值不同。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 访问私有实例变量

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q5

  Consider the following class definition.

  ```java
  public class Location
  {
      private int row, col;

      public Location()
      { /* implementation not shown */ }
  }
  ```

  The following method is intended to create a copy of a Location object.

  ```java
  public Location clone(Location loc)
  {
      Location loc1 = new Location();
      loc1.row = loc.row;
      loc1.col = loc.col;
      return loc1;
  }
  ```

  Which of the following best describes the conditions under which the method works as intended?

  (A) The method will run correctly only if it is defined in a class other than Location.  
  (B) The method will run correctly only if it is defined inside the Location class.  
  (C) The method will always run correctly.  
  (D) The method will never run correctly.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    方法访问了 `loc.row` 和 `loc.col`，它们是 Location 类的 **private 实例变量**，只能在 **Location 类内部**访问。因此该方法必须定义在 Location 类内部才能编译。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 通过对象调用访问器

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q6

  Consider the following class definition.

  ```java
  public class Item
  {
      // maintains the price of an item
      private int price;

      public int getPrice()
      {
          return price;
      }
  }
  ```

  The following method appears in a class other than Item. The method is intended to calculate and return the sales tax of the item specified by the parameter myItem. The sales tax will be calculated as the cost of the item times the value of the parameter taxRate.

  ```java
  public double getTax(Item myItem, double taxRate)
  {
      double cost = /* missing code */;
      return cost * taxRate;
  }
  ```

  Which of the following expressions can be used to replace `/* missing code */` so that this method works as intended?

  (A) `Item.price`  
  (B) `myItem.price`  
  (C) `Item.getPrice()`  
  (D) `myItem.getPrice()`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    getTax 在 Item 类**外部**，无法直接访问私有变量 `price`（选项 A、B 错误）。getPrice 是实例方法，应通过对象 `myItem` 调用：`myItem.getPrice()`。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 局部变量遮蔽实例变量

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q18

  Consider the following Worker class. The class includes the method getEarnings, which is intended to return the total amount earned by the worker.

  ```java
  public class Worker
  {
      private double hourlyRate;
      private double hoursWorked;
      private double earnings;

      public Worker(double rate, double hours)
      {
          hourlyRate = rate;
          hoursWorked = hours;
      }

      private void calculateEarnings()
      {
          double earnings = 0.0;                  // 局部变量，遮蔽实例变量
          earnings = hourlyRate * hoursWorked;
      }

      public double getEarnings()
      {
          calculateEarnings();
          return earnings;                        // 返回的是实例变量（仍为默认值 0.0）
      }
  }
  ```

  The following code segment appears in a method in a class other than Worker. The code segment is intended to print the value 800.0, but instead prints a different value because of an error in the Worker class.

  ```java
  Worker bob = new Worker(20.0, 40.0);
  System.out.println(bob.getEarnings());
  ```

  Which of the following best explains why an incorrect value is printed?

  (A) The private instance variables hourlyRate and hoursWorked should be declared public.  
  (B) The private method calculateEarnings should be declared public.  
  (C) The variable earnings in the calculateEarnings method is a local variable.  
  (D) The variables hourlyRate and hoursWorked in the calculateEarnings method are local variables.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    calculateEarnings 方法中声明的 `double earnings` 是**局部变量**，它遮蔽了同名的实例变量。方法给局部变量赋值 800.0，但 getEarnings 返回的是**实例变量 earnings**（从未被赋值，保持默认值 0.0）。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 对象按引用传递     | 方法内修改对象属性会影响原对象               | 与基本类型按值传递对比                         |
| String 不可变      | 方法内"修改"String 不影响原字符串            | str1 不变，str2 是返回值                       |
| 私有访问           | private 实例变量只能在类内部访问             | 外部类必须通过 public 方法访问                 |
| 局部变量遮蔽       | 同名局部变量遮蔽实例变量                     | 赋值给了局部变量，实例变量未被修改             |
