---
layout: default
title: 3.8 Scope and Access
parent: Unit 3
nav_order: 8
---

# 3.8 — Scope and Access

## 3.8.A 作用域（Scope）

**作用域（Scope）** 定义了变量在哪些代码区域中可见：

- **局部变量（Local Variable）**：在方法（或代码块）内部声明，只在声明处之后的方法/块内可见。
- **实例变量（Instance Variable）**：在类中声明，类的所有方法都可以访问。
- **参数（Parameter）**：只在所属方法内可见。
- **循环变量**：for 循环头声明的变量只在循环内可见（循环结束后消失）。

{: .important}
> **局部变量遮蔽（shadowing）**：当局部变量与实例变量同名时，在方法内部，**局部变量优先**。要访问被遮蔽的实例变量需使用 `this` 关键字（见 3.9）。

## 3.8.B 访问控制（Access）

- `private` 成员只能在本类内部访问。
- `public` 成员任何类都可以访问。
- 局部变量不能被 `public`/`private` 修饰（见 3.5）。

- ### 例题 1 — 局部变量遮蔽实例变量

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q10

  Consider the following class definition.

{% raw %}
  ```java
  public class ComputeObject
  {
      private int limit;
      private int val;

      public ComputeObject()
      {
          limit = 7;
          val = 10;
      }

      public int sumProd(int limit)
      {
          int total = 0;
          for (int val = 0; val < limit; val++)
          {
              total += val;
          }
          total *= val;
          return total;
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than ComputeObject.

  ```java
  ComputeObject s = new ComputeObject();
  System.out.println(s.sumProd(5));
  ```

  Which of the following best describes the behavior of this code segment?

  (A) The sumProd method accumulates the sum of the integers 0 through 4, multiplies the sum by 5, and returns the value 50, which is then printed.  
  (B) The sumProd method accumulates the sum of the integers 0 through 4, multiplies the sum by 10, and returns the value 100, which is then printed.  
  (C) The sumProd method accumulates the sum of the integers 0 through 6, multiplies the sum by 7, and returns the value 147, which is then printed.  
  (D) The sumProd method accumulates the sum of the integers 0 through 6, multiplies the sum by 10, and returns the value 210, which is then printed.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    方法参数 `limit` 遮蔽了实例变量 limit：循环使用参数 limit = 5，val 从 0 累加到 4，total = 0+1+2+3+4 = 10。循环结束后，**循环变量 val 超出作用域**（for 头声明的局部变量循环后消失），`total *= val` 中的 val 是**实例变量 val = 10**。total = 10 × 10 = 100。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 参数遮蔽实例变量

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q11

  Consider the following class definition.

{% raw %}
  ```java
  public class Stars
  {
      private int size;
      private int width;

      public Stars(int n, int w)
      {
          size = n;
          width = w;
      }

      public void draw(int size)
      {
          for (int i = 1; i <= size; i++)
          {
              line(i, width - 1);
          }
      }

      public void line(int n, int width)
      {
          for (int i = 0; i < n; i++)
          {
              for (int j = 0; j < width; j++)
              {
                  System.out.print("*");
              }
          }
          System.out.println();
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than Stars.

  ```java
  Stars s = new Stars(3, 2);
  s.draw(5);
  ```

  What is printed as a result of executing this code segment?

  (A)
  ```
  *
  **
  ***
  ```
  (B)
  ```
  ****
  ****
  ****
  ****
  ****
  ```
  (C) 共打印 15 个 `*`，分为 5 行：1、2、3、4、5 个
  (D) 共打印 25 个 `*`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    构造方法：size = 3，width = 2。`s.draw(5)`：参数 `size`（= 5）遮蔽实例变量 size，draw 循环 i = 1..5 调用 `line(i, width - 1)`。line 中参数 width = 1（遮蔽实例变量 width = 2），每行打印 i × 1 个星号。5 行分别打印 1、2、3、4、5 个星号，共 15 个。选项 (C) 正确。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 局部变量遮蔽的 bug

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q12

  Consider the following class, which models a bank account. The deposit method is intended to update the account balance by a given amount; however, it does not work as intended.

{% raw %}
  ```java
  public class BankAccount
  {
      private String accountOwnerName;
      private double balance;
      private int accountNumber;

      public BankAccount(String name, double initialBalance, int acctNum)
      {
          accountOwnerName = name;
          balance = initialBalance;
          accountNumber = acctNum;
      }

      public void deposit(double amount)
      {
          double balance = balance + amount;
      }
  }
  ```
{% endraw %}

  Which of the following best explains why the deposit method does not work as intended?

  (A) The deposit method must have a return statement.  
  (B) In the deposit method, the variable balance should be replaced by the variable initialBalance.  
  (C) In the deposit method, the variable balance is declared as a local variable and is different from the instance variable balance.  
  (D) The variable balance must be passed to the deposit method.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    deposit 方法内声明了局部变量 `double balance`，它遮蔽了实例变量 balance。`balance = balance + amount` 只修改了局部变量，实例变量 balance **没有被更新**。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 未定义变量的使用

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q18

  Consider the following Worker class.

{% raw %}
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
          double earnings = 0.0;
          earnings = hourlyRate * hoursWorked;
      }

      public double getEarnings()
      {
          calculateEarnings();
          return earnings;
      }
  }
  ```
{% endraw %}

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
    calculateEarnings 中的 `double earnings` 是局部变量，遮蔽了实例变量 earnings。局部变量被赋值为 800.0，但 getEarnings 返回的实例变量 earnings 从未被赋值（默认 0.0）。这是**局部变量遮蔽**导致的错误。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 局部变量作用域     | 方法/块内声明，之后可见，块外不可见          | 循环变量循环后消失                             |
| 参数作用域         | 只在所属方法内可见                           | 参数遮蔽同名实例变量                           |
| 局部变量遮蔽       | 局部变量优先于同名实例变量                   | 修改局部变量不影响实例变量                     |
| 访问控制           | private 仅类内；public 全类可访问             | 类外不能访问 private 成员                      |
