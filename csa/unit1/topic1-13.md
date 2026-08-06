---
layout: default
title: 1.13 Object Creation and Storage (Instantiation)
parent: Unit 1
nav_order: 13
---

# 1.13 — Object Creation and Storage (Instantiation)

## 1.13.A 实例化（Instantiation）

**实例化（Instantiation）** 是创建类的对象的过程。使用关键字 **`new`** 加上对**构造方法（constructor）** 的调用来创建对象：

```java
Dog dog1 = new Dog("Rex", 4);   // 调用 Dog 类的构造方法创建对象
```

- 等号右边先执行 `new Dog("Rex", 4)`：在内存中创建一个新的 Dog 对象。
- `dog1` 是一个**引用变量（reference variable）**，它存储的是对象在内存中的**地址（引用）**，而不是对象本身。

{: .important}
> 对象变量（引用变量）中保存的是**内存地址**。把引用变量赋值给另一个引用变量，会让两个变量指向**同一个对象**。

## 1.13.B 构造方法的重载与参数匹配

一个类可以有**多个构造方法**（称为**重载 overload**），它们的**参数数量或类型不同**。创建对象时，实参必须与某个构造方法的签名匹配：

```java
Vbox b1 = new Vbox(4);        // 匹配 Vbox(int len)
Vbox b2 = new Vbox(2, 8, 4);  // 匹配 Vbox(int w, int h, int d)
```

- ### 例题 1 — 引用变量的指向

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q9

  The Dog class has a constructor that takes two parameters. The first parameter is a String representing a dog's name and the second parameter is an int representing the dog's age, in months.

  The following code segment appears in a class other than Dog.

  ```java
  Dog dog1 = new Dog("Rex", 4);
  Dog dog2 = dog1;
  dog1 = new Dog("Fido", 60);
  ```

  Which of the following best describes the contents of dog1 and dog2 as a result of executing this code segment?

  (A) dog1 and dog2 are Dog variables that each contain the same Dog object, which represents a dog named "Fido" that is 60 months old.  
  (B) dog1 is a Dog variable that contains a Dog object representing a dog named "Fido" that is 60 months old, and dog2 is a Dog variable that contains a Dog object representing a dog named "Rex" that is 4 months old.  
  (C) dog1 and dog2 are Dog reference variables that each contain a reference to the same memory address that contains the Dog object representing a dog named "Fido" that is 60 months old.  
  (D) dog1 is a Dog reference variable, which contains a reference to the memory address for the Dog object representing a dog named "Fido" that is 60 months old. dog2 is a Dog reference variable, which contains a reference to the memory address for the Dog object representing a dog named "Rex" that is 4 months old.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    第 1 行创建 "Rex"（4 个月）对象，dog1 指向它。第 2 行 `dog2 = dog1` 让 dog2 也指向 "Rex" 对象。第 3 行重新给 dog1 赋值，指向新建的 "Fido"（60 个月）对象——dog1 现在指向新对象，而 dog2 仍指向原来的 "Rex" 对象。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 构造方法参数匹配（Vbox）

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q10

  The Vbox class includes the following two constructors.

  | Constructor Signature               | Explanation                                                       |
  | ----------------------------------- | ----------------------------------------------------------------- |
  | `public Vbox(int w, int h, int d)`  | Constructs a Vbox object that represents a box with width w, height h, and depth d. |
  | `public Vbox(int len)`              | Constructs a Vbox object that represents a box with width len, height len, and depth len. |

  Which of the following declarations, appearing in a class other than Vbox, will correctly instantiate a Vbox object?

  (A) `Vbox b1 = new Vbox(4.0);`  
  (B) `Vbox b2 = new Vbox(4, 2);`  
  (C) `Vbox b3 = new Vbox(2, 8, 4);`  
  (D) `Vbox b4 = new Vbox(4.0, 4.0, 4.0);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `Vbox(2, 8, 4)` 使用三个 int 实参，匹配构造方法 `Vbox(int w, int h, int d)`。(A)(D) 使用 double 实参不匹配任何构造方法；(B) 两个参数也不匹配。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 参数顺序必须正确（Person）

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q11

  The Person class has exactly two constructors. Partial declarations of the constructors are shown.

  ```java
  public Person(int idNumber, boolean isActive)
  { /* implementation not shown */ }

  public Person(int idNumber, int age, boolean isActive)
  { /* implementation not shown */ }
  ```

  Which of the following statements does not correctly create an object of type Person?

  (A) `Person p1 = new Person(1138, true);`  
  (B) `Person p2 = new Person(3136, 17, false);`  
  (C) `Person p3 = new Person(3544, false, 18);`  
  (D) `Person p4 = new Person(0, false);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (C) 试图使用第二个构造方法 `Person(int, int, boolean)`，但实参顺序是 `(int, boolean, int)`，第二个实参应为 int 而给的是 boolean，第三个应为 boolean 而给的是 int，类型不匹配导致编译错误。正确答案是 **(C)**。

  </details>

- ### 例题 4 — new 关键字必不可少（Player）

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q12

  The Player class has only one constructor. A partial declaration of the constructor is shown.

  ```java
  public Player(boolean isOnline, int numLives)
  { /* implementation not shown */ }
  ```

  Which of the following statements correctly creates a Player object?

  (A) `Player p = new Player(true, 5);`  
  (B) `Player p = new Player(5, true);`  
  (C) `Player p = Player(true, 5);`  
  (D) `Player p = Player(5, true);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    创建对象必须使用关键字 `new`，且实参数量、类型、顺序都要匹配构造方法。选项 (A) 使用 `new Player(true, 5)`，参数顺序正确（boolean 在前、int 在后）。选项 (C)(D) 缺少 `new`；选项 (B) 参数顺序错误。正确答案是 **(A)**。

  </details>

- ### 例题 5 — 选择正确的构造调用（WindTurbine）

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q8

  The WindTurbine class has two constructors. The constructor headers are shown.

  ```java
  public WindTurbine(int efficiency)
  public WindTurbine(int efficiency, String location)
  ```

  Which of the following statements, when placed in a method in a class other than WindTurbine, will construct a WindTurbine object wt?

  (A) `WindTurbine wt = new WindTurbine(3);`  
  (B) `WindTurbine wt = new WindTurbine(3.25);`  
  (C) `WindTurbine wt = WindTurbine(3, "Atlantic Ocean");`  
  (D) `WindTurbine wt = WindTurbine(3.25, "Atlantic Ocean");`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    选项 (A) 用 `new` 关键字调用 `WindTurbine(int)`，参数类型匹配。选项 (B) 中 3.25 是 double，不匹配任何构造方法；选项 (C)(D) 缺少 `new` 关键字且 (D) 参数类型错误。正确答案是 **(A)**。

  </details>

- ### 例题 6 — new 与构造方法调用的语法

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q18

  Consider the following Point2D class constructor header.

  ```java
  public Point2D(double x, double y)
  { /* implementation not shown */ }
  ```

  Which of the following code segments will correctly create an instance of a Point2D object?

  (A) `Point2D p = Point2D(3.0, 4.0);`  
  (B) `new p = Point2D(3.0, 4.0);`  
  (C) `new Point2D = p(3.0, 4.0);`  
  (D) `Point2D p = new Point2D(3.0, 4.0);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    正确语法是：声明变量 `p`（类型 Point2D），用 `new Point2D(3.0, 4.0)` 创建对象并赋值。选项 (D) 完全正确，其他选项语法错误。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                           | 考试提示                                           |
| ------------------ | -------------------------------------------------- | -------------------------------------------------- |
| 实例化             | `new 类名(实参)` 创建对象                          | `new` 关键字必不可少                               |
| 引用变量           | 存内存地址，赋值使两个变量指向同一对象             | 追踪 dog2 = dog1 后各变量的指向                    |
| 构造方法重载       | 参数数量/类型不同                                  | 实参必须匹配某个构造方法的签名                     |
| 参数顺序           | 参数顺序错误 → 编译错误                            | 注意 `(int, boolean)` 与 `(boolean, int)` 的区别   |
