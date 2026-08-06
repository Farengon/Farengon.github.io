---
layout: default
title: 3.3 Anatomy of a Class
parent: Unit 3
nav_order: 3
---

# 3.3 — Anatomy of a Class

## 3.3.A 类的组成部分

一个 Java 类的**组成部分（Anatomy）**包括：

```java
public class Item          // 类声明（class header）
{
    private double price;  // 实例变量（instance variables / attributes）
    public String name;

    public Item(double p)  // 构造方法（constructor）
    {
        price = p;
    }

    public double getPrice()  // 方法（methods / behaviors）
    {
        return price;
    }
}
```

**访问修饰符（Access Modifiers）：**

| 修饰符    | 可见性                     | 用途                       |
| --------- | -------------------------- | -------------------------- |
| `public`  | 所有类都可以访问           | 类、构造方法、公开方法     |
| `private` | 仅本类内部可以访问         | 实例变量（数据封装）       |

{: .important}
> **数据封装（Encapsulation）**：实例变量通常声明为 `private`，防止外部类直接访问和修改；外部通过**公开方法（public methods）**访问。

## 3.3.B 类声明的正确设计

- 类本身通常声明为 `public`（外部才能创建对象）。
- 构造方法**总是**声明为 `public`。
- 实例变量声明为 `private`（保持数据内部化）。
- 需要在类外访问的方法声明为 `public`。
- **实例变量属于对象**——每个对象都有自己的一份实例变量副本（EK 3.3.A.4）。

- ### 例题 1 — 私有与公有访问

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q7

  Consider the following partial class declaration.

  ```java
  public class Item
  {
      private double price;    // The price of the item
      public String name;      // The name of the item

      /* There may be instance variables, constructors, and methods that are not shown. */
  }
  ```

  The following code segments each appear in a class other than Item. Assume that myItem and myItem2 are Item objects that have been properly instantiated.

  **Code Segment I**

  ```java
  int x = myItem.price;
  System.out.println(x);
  ```

  **Code Segment II**

  ```java
  String y = myItem2.name;
  System.out.println(y);
  ```

  What, if anything, is printed as a result of executing each of the code segments?

  (A) Code segment I prints the price of myItem, and code segment II prints the name of myItem2.  
  (B) Code segment I prints the price of myItem, but code segment II does not compile.  
  (C) Code segment II prints the name of myItem2, but code segment I does not compile.  
  (D) Nothing is printed because neither code segment compiles.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `price` 声明为 `private`，在 Item 类**外部**无法直接访问，代码段 I 编译失败。`name` 声明为 `public`，外部可以访问，代码段 II 可以正常打印 name。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 约束外部修改

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q8

  The following Candy class is used to represent pieces of candy.

  ```java
  public class Candy        // line 1
  {
      public String name;   // line 3
      public double weight; // line 4

      /* There may be instance variables, constructors, and methods that are not shown. */
  }
  ```

  The class is intended to allow external classes to create Candy objects, but external classes should not be able to modify the attributes of Candy objects. Access to the class is not constrained as intended.

  Which of the following changes can be made so that access to the class is constrained as intended?

  (A) Changing the public designation to private in line 1  
  (B) Changing the class header in line 1 to `public class Candy()`  
  (C) Changing the public designation to private in lines 3 and 4  
  (D) Changing the data type in line 4 from double to String

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    要防止外部类直接访问和修改实例变量，应把实例变量声明为 `private`。类本身要保持 `public`（外部才能创建对象）。把第 3、4 行的 `public` 改为 `private` 即可。正确答案是 **(C)**。

  </details>

- ### 例题 3 — Profile 类的正确声明

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q9

  The Profile class will be used to represent users of a social media website. Each instance of the class will maintain the user's name, username, and number of followers. This information is unique to each user and should not be directly accessible outside the Profile class.

  Which of the following declarations is the most appropriate for the Profile class?

  (A)
  ```java
  private class Profile
  {
      private String name;
      private String username;
      private int followers;
  }
  ```
  (B)
  ```java
  public class Profile
  {
      public String name;
      public String username;
      public int followers;
  }
  ```
  (C)
  ```java
  public class Profile
  {
      private String name;
      private String username;
      private int followers;
  }
  ```
  (D)
  ```java
  private class Profile
  {
      private String name;
      private String username;
      private int followers;
  }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    类声明为 `public`（其他类可以创建 Profile 对象），三个实例变量声明为 `private`（外部不能直接访问用户信息）。选项 (C) 正确。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 完整类实现（Player）

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q1

  Consider the design of a Player class that will contain two int attributes and a constructor. The class will also contain a method getScore that can be accessed from outside the class. A partial definition of the Player class is shown.

  ```java
  public class Player
  {
      /* missing code */
  }
  ```

  Which of the following replacements for `/* missing code */` is the most appropriate implementation of the class?

  (A)
  ```java
  private int score;
  private int id;
  public Player(int playerScore, int playerID)
  { /* implementation not shown */ }
  private int getScore()
  { /* implementation not shown */ }
  ```
  (B)
  ```java
  private int score;
  private int id;
  public Player(int playerScore, int playerID)
  { /* implementation not shown */ }
  public int getScore()
  { /* implementation not shown */ }
  ```
  (C)
  ```java
  public int score;
  public int id;
  public Player(int playerScore, int playerID)
  { /* implementation not shown */ }
  private int getScore()
  { /* implementation not shown */ }
  ```
  (D)
  ```java
  public int score;
  public int id;
  public Player(int playerScore, int playerID)
  { /* implementation not shown */ }
  public int getScore()
  { /* implementation not shown */ }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    score 和 id 是内部数据，应声明为 `private`；构造方法需要在类外创建对象，声明为 `public`；getScore 需要被外部访问，声明为 `public`。选项 (B) 完全正确。正确答案是 **(B)**。

  </details>

- ### 例题 5 — 编译错误定位（Bugs）

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q3

  Consider the following Bugs class, which is intended to simulate variations in a population of bugs. The population is stored in the method's int attribute. The getPopulation method is intended to allow methods in other classes to access a Bugs object's population value. However, the class does not compile.

  ```java
  public class Bugs
  {
      private int population;

      public Bugs(int p)
      {
          population = p;
      }

      public int getPopulation()
      {
          return p;
      }
  }
  ```

  Which of the following best explains why the Bugs class does not compile?

  (A) The return type of the getPopulation method should be void.  
  (B) The getPopulation method should have at least one parameter.  
  (C) The variable population is not declared inside the getPopulation method.  
  (D) In the getPopulation method, the variable population should be returned instead of p.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    getPopulation 方法中 `return p;` 的变量 `p` 只在构造方法中作为参数存在，在该方法中未定义，导致编译错误。应返回实例变量 `population`。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| 类组成部分         | 类声明、实例变量、构造方法、方法             | 各部分的语法和位置                             |
| 访问修饰符         | `private` 仅类内、`public` 全类可访问        | 实例变量通常 private                           |
| 数据封装           | 私有数据 + 公有方法访问                      | 防止外部直接修改                               |
| 类声明             | 类本身 public，实例变量 private              | 外部要创建对象 → 类必须 public                 |
| 编译错误定位       | 未定义变量、错误返回类型                     | 检查方法内使用的变量是否已定义                 |
