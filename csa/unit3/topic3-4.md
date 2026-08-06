---
layout: default
title: 3.4 Constructors
parent: Unit 3
nav_order: 4
---

# 3.4 — Constructors

## 3.4.A 构造方法（Constructor）

**构造方法（Constructor）** 在创建对象时被调用，用于**初始化对象的实例变量**：

```java
public class Person
{
    private String name;

    public Person(String n)   // 构造方法：与类同名，无返回类型
    {
        name = n;
    }
}
```

{: .important}
> - 构造方法的名字**必须与类名完全相同**。
> - 构造方法**没有返回类型**（连 `void` 都不写）。
> - 用 `new 类名(实参)` 调用构造方法。
> - 若没有写任何构造方法，Java 会自动提供**无参构造方法（default constructor）**，实例变量取默认值（`int` → 0，`String`/引用类型 → `null`，`boolean` → false）。
> - 构造方法通常声明为 `public`，这样其他类才能创建对象。

## 3.4.B 默认值

| 类型     | 默认值   |
| -------- | -------- |
| int      | 0        |
| double   | 0.0      |
| boolean  | false    |
| 引用类型 | null     |

- ### 例题 1 — 构造方法实现

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q10

  Consider the following class definition.

  ```java
  public class Person
  {
      private String name;
      /* missing constructor */
  }
  ```

  The following statement, which is located in a method in a different class, creates a new Person object with its attribute name initialized to "Washington".

  ```java
  Person p = new Person("Washington");
  ```

  Which of the following can be used to replace `/* missing constructor */` so that the object p is correctly created?

  (A)
  ```java
  private Person(String n)
  {
      name = n;
  }
  ```
  (B)
  ```java
  public Person()
  {
      name = n;
  }
  ```
  (C)
  ```java
  public Person(String n)
  {
      name = n;
  }
  ```
  (D)
  ```java
  public Person(String name)
  {
      String n = name;
  }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    构造方法需要被其他类调用，必须声明为 `public`；`new Person("Washington")` 传入一个 String 实参，构造方法要有 String 形参并把值赋给实例变量 name。选项 (C) 满足所有要求。选项 (A) 是 private（外部无法调用）；(B) 无参不匹配；(D) 没有把参数赋值给实例变量。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 构造方法中的赋值错误

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q11

  Consider the following Student class.

  ```java
  public class Student
  {
      private String name;
      private int age;

      public Student(String studentName, int studentAge)
      {
          name = studentName;
          studentAge = age;     // 注意：方向写反了
      }
  }
  ```

  The following code segment appears in a class other than Student.

  ```java
  Student myStudent = new Student("Bobby", 25);
  ```

  Which of the following best describes the state of the object myStudent as a result of executing this code segment?

  (A) myStudent has been initialized such that name contains the string "Bobby" and age is 0.  
  (B) myStudent has been initialized such that name contains the string "Bobby" and age is 25.  
  (C) myStudent has been initialized such that name is null and age is 0.  
  (D) myStudent has been initialized such that name is null and age is 25.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `name = studentName` 把 "Bobby" 赋给 name。但 `studentAge = age` 方向写反了：把**实例变量 age 的默认值 0** 赋给了参数 studentAge，实例变量 age **从未被赋值**，保持默认值 0。所以 name = "Bobby"，age = 0。正确答案是 **(A)**。

  </details>

- ### 例题 3 — 默认构造方法

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q12

  Consider the following class definition.

  ```java
  public class Dog
  {
      private String name;
      private int age;

      public String getName()
      {
          return name;
      }

      public int getAge()
      {
          return age;
      }
  }
  ```

  The following segment appears in a class other than Dog.

  ```java
  Dog fido = new Dog();
  System.out.print("name: " + fido.getName());
  System.out.print(", age: " + fido.getAge());
  ```

  What is printed as a result of executing this code segment?

  (A) `name: , age: 0`  
  (B) `name: null, age: 0`  
  (C) `name: null, age: null`  
  (D) Nothing is printed. An error occurs because the Dog class does not contain a no-parameter constructor.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    Dog 类没有定义任何构造方法，Java 自动提供无参构造方法。实例变量取默认值：String name 为 `null`，int age 为 0。输出 "name: null, age: 0"。正确答案是 **(B)**。

  </details>

- ### 例题 4 — 变量声明与构造

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q6

  The following code segment is intended to calculate the circumference of a circle whose diameter diam is 1.5. The circumference of a circle is equal to its diameter times pi.

  ```java
  /* missing declarations */
  circ = pi * diam;
  ```

  Which of the following variable declarations are most appropriate to replace `/* missing declarations */` in the code segment?

  (A)
  ```java
  int pi = 3.14159;
  int diam = 1.5;
  final int circ;
  ```
  (B)
  ```java
  final int pi = 3.14159;
  int diam = 1.5;
  int circ;
  ```
  (C)
  ```java
  final double pi = 3.14159;
  double diam = 1.5;
  double circ;
  ```
  (D)
  ```java
  final double diam = 1.5;
  final double circ = 0.0;
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    circ、diam 存储的是小数，应用 `double` 类型；pi 是常量，用 `final` 修饰且类型为 `double`。选项 (C) 正确。正确答案是 **(C)**。

  </details>

- ### 例题 5 — 构造方法调用

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q7

  Consider the following partial Person class definition. The instance variable adult should be set to true if the person's age is at least 18 years old, and should be set to false otherwise.

  ```java
  public class Person
  {
      private String name;
      private int age;
      private boolean adult;

      public Person(String n, int a)
      {
          name = n;
          age = a;
          if (age >= 18)
          {
              adult = true;
          }
          else
          {
              adult = false;
          }
      }
  }
  ```

  Which of the following statements, when appearing in a method in a class other than Person, will correctly create an instance of a Person object that represents an adult person?

  (A) `Person p = new Person("Homer", 23);`  
  (B) `Person p = new Person("Homer", "23");`  
  (C) `Person p = new Person("Homer", true);`  
  (D) `Person p = new Person("Homer", 17);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    构造方法要求一个 String 和一个 int 实参。选项 (A) 传入 "Homer"（String）和 23（int），23 ≥ 18，adult 会被设为 true，正确创建了"成人"对象。选项 (B)(C) 参数类型错误；(D) 的 17 < 18 不是成人。正确答案是 **(A)**。

  </details>

- ### 例题 6 — 参数赋值方向

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q16

  Consider the following class definition.

  ```java
  public class Tester
  {
      private int num1;
      private int num2;

      /* missing constructor */
  }
  ```

  The following statement appears in a method in a class other than Tester. It is intended to create a new Tester object with its attributes set to 10 and 20.

  ```java
  Tester t = new Tester(10, 20);
  ```

  Which of the following can be used to replace `/* missing constructor */` so that the object t is correctly created?

  (A)
  ```java
  public Tester(int first, int second)
  {
      num1 = first;
      num2 = second;
  }
  ```
  (B)
  ```java
  public Tester(int first, int second)
  {
      num1 = 1;
      num2 = 2;
  }
  ```
  (C)
  ```java
  public Tester(int first, int second)
  {
      first = 10;
      second = 20;
  }
  ```
  (D)
  ```java
  public Tester(int first, int second)
  {
      first = num1;
      second = num2;
  }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    构造方法应把形参 `first`、`second` 的值赋给实例变量 `num1`、`num2`，这样 `new Tester(10, 20)` 创建的对象属性为 10 和 20。选项 (A) 正确。选项 (B) 写死为 1、2；(C)(D) 方向错误。正确答案是 **(A)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 构造方法特征       | 与类同名、无返回类型、用 new 调用            | 通常 public                                    |
| 参数 → 实例变量    | `name = n;` 方向不能反                       | `n = name;` 会让实例变量保持默认值             |
| 默认构造方法       | 未定义时自动提供，实例变量取默认值           | int → 0，引用 → null                           |
| 默认值             | int/double/boolean/引用各自的默认值          | 常考 String → null、int → 0                    |
| 实参匹配           | 实参数量与类型必须匹配构造方法签名           | String + int 不能换成 String + String          |
