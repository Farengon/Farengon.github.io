---
layout: default
title: 3.7 Class Variables and Methods
parent: Unit 3
nav_order: 7
---

# 3.7 — Class Variables and Methods

## 3.7.A 类变量（Class Variables / static Variables）

**类变量（Class Variable）** 用关键字 `static` 声明，它属于**类**而不是某个对象：

- 所有该类的对象**共享**同一个类变量。
- 类变量在类被加载时初始化（只初始化一次）。
- 通过**类名.变量名**访问，也可以在方法中直接使用。

```java
public class TestObject
{
    private double var1;         // 实例变量：每个对象各有一份
    private static int var2 = 0; // 类变量：所有对象共享一份

    public TestObject(double p)
    {
        var1 = p;
        var2++;                  // 每创建一个对象，var2 + 1
    }
}
```

## 3.7.B 类方法（Class Methods / static Methods）

**类方法（Class Method）** 也用 `static` 声明，通过**类名.方法名()** 调用：

- 类方法**只能访问类变量**（static 变量），不能访问实例变量。
- 实例方法可以访问类变量（因为类变量对所有对象都可见）。

{: .important}
> - `static` 变量/方法属于**类**，所有对象共享。
> - 类方法内部不能直接使用实例变量（它不属于任何特定对象）。
> - 用类名调用 → 该方法必须是 static。

- ### 例题 1 — 类变量在多个对象间共享

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q7

  Consider the following StringFinder class.

  ```java
  public class StringFinder
  {
      private String fullString;
      private static String target = "x";

      public StringFinder(String fs)
      {
          fullString = fs;
      }

      public static void updateTarget(String newTarget)
      {
          target = newTarget;
      }

      public int targetLocation()
      {
          int temp = fullString.indexOf(target);
          target = "z";
          return temp;
      }
  }
  ```

  The following code segment appears in a class other than StringFinder.

  ```java
  StringFinder music = new StringFinder("jazz");
  StringFinder fire = new StringFinder("blaze");
  StringFinder animal = new StringFinder("zebra");
  int musicLoc = music.targetLocation();
  StringFinder.updateTarget("a");
  int fireLoc = fire.targetLocation();
  int animalLoc = animal.targetLocation();
  System.out.println(musicLoc + " " + fireLoc + " " + animalLoc);
  ```

  What is printed as a result of executing this code segment?

  (A) `-1 -1 -1`  
  (B) `-1 2 0`  
  (C) `-1 2 4`  
  (D) `0 2 4`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    ① `music.targetLocation()`：target 初始为 "x"，"jazz" 中没有 "x"，返回 -1；然后 target 被改为 "z"。② `StringFinder.updateTarget("a")`：类方法把共享的 target 改为 "a"。③ `fire.targetLocation()`："blaze" 中 "a" 在索引 2，返回 2；target 被改为 "z"。④ `animal.targetLocation()`："zebra" 中 "z" 在索引 0，返回 0。输出 "-1 2 0"。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 类方法调用要求 static

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q8

  Consider the following class definition.

  ```java
  public class Widget
  {
      private int number;
      private static String word = "start";

      public Widget()
      { /* implementation not shown */ }
  }
  ```

  The following code segment appears in a class other than Widget.

  ```java
  int result = Widget.doSomething();
  ```

  Which of the following implementations of doSomething will allow this code segment to run without error when added to the Widget class?

  (A)
  ```java
  public int doSomething()
  {
      return number;
  }
  ```
  (B)
  ```java
  public int doSomething()
  {
      return word.length();
  }
  ```
  (C)
  ```java
  public static int doSomething()
  {
      return number;
  }
  ```
  (D)
  ```java
  public static int doSomething()
  {
      return word.length();
  }
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    调用语句使用类名 `Widget.doSomething()`，所以 doSomething 必须是 **static 方法**（排除 A、B）。类方法只能访问**类变量**，`number` 是实例变量不能访问，`word` 是 static 类变量可以访问。选项 (D) 正确。正确答案是 **(D)**。

  </details>

- ### 例题 3 — 类变量计数

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q9

  Consider the following class declaration.

  ```java
  public class TestObject
  {
      private double var1;
      private static int var2 = 0;

      public TestObject(double p)
      {
          var1 = p;
          var2++;
      }

      public void printTestObject()
      {
          System.out.println(var1 + "," + var2);
      }
  }
  ```

  The following code segment appears in a class other than TestObject. Assume that no other TestObject objects have been created.

  ```java
  TestObject obj1 = new TestObject(2.5);
  TestObject obj2 = new TestObject(10.2);
  obj1.printTestObject();
  ```

  What is printed as a result of executing this code segment?

  (A) `2.5,0`  
  (B) `2.5,1`  
  (C) `2.5,2`  
  (D) `10.2,2`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    obj1 的实例变量 var1 = 2.5。类变量 var2 在创建 obj1 时 +1 变为 1，创建 obj2 时再 +1 变为 2。`obj1.printTestObject()` 打印 obj1 的 var1（2.5）和**共享的** var2（2）。输出 "2.5,2"。正确答案是 **(C)**。

  </details>

- ### 例题 4 — 类变量的共享行为

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q2

  Consider the following class definition.

  ```java
  public class WordClass
  {
      private final String word;
      private static String maxWord = "";

      public WordClass(String s)
      {
          word = s;
          if (word.length() > maxWord.length())
          {
              maxWord = word;
          }
      }
  }
  ```

  Which of the following is a true statement about the behavior of WordClass objects?

  (A) Every time a WordClass object is created, the maxWord variable is referenced.  
  (B) Every time a WordClass object is created, the value of the maxWord variable changes.  
  (C) No two WordClass objects can have their word length equal to the length of maxWord.  
  (D) The value of the maxWord variable cannot be changed once it has been initialized.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `maxWord` 是 static 类变量，所有 WordClass 对象共享。每次创建对象（调用构造方法）时，都会比较 `word.length()` 与 `maxWord.length()`，即 maxWord **被引用**。但只有当新单词更长时它才会**改变**（选项 B 过于绝对）。正确答案是 **(A)**。

  </details>

- ### 例题 5 — static 方法与类变量

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q15

  Consider the following class definition.

  ```java
  public class Something
  {
      private static int count = 0;

      public Something()
      {
          count += 5;
      }

      public static void increment()
      {
          count++;
      }
  }
  ```

  The following code segment appears in a method in a class other than Something.

  ```java
  Something s = new Something();
  Something.increment();
  ```

  Which of the following best describes the behavior of the code segment?

  (A) The code segment does not compile because the increment method should be called on an object of the class Something, not on the class itself.  
  (B) The code segment creates a Something object s. The Something class's static variable count is initially 0, then is increased by 1.  
  (C) The code segment creates a Something object s. The Something class's static variable count is initially 0, then is increased by 5, then is increased by 1.  
  (D) The code segment creates a Something object s. The Something class's static variable count does not change after it is initially set to 0.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    count 初始为 0。创建对象 s 时构造方法执行 `count += 5`，count = 5；`Something.increment()` 是合法调用（static 方法用类名调用），count 再 +1 变为 6。选项 (C) 正确描述了过程。正确答案是 **(C)**。

  </details>

- ### 例题 6 — static 变量的更新次数

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q17

  Consider the following class definition.

  ```java
  public class Element
  {
      private static int maxValue = 0;

      public Element(int value)
      {
          if (value > maxValue)
          {
              maxValue = value;
          }
      }

      public static int getMaxValue()
      {
          return maxValue;
      }
  }
  ```

  The following code segment appears in a class other than Element. Assume that no other Element objects have been created.

  ```java
  Element a = new Element(1);
  Element b = new Element(Element.getMaxValue());
  Element c = new Element(2);
  if (Element.getMaxValue() == 3)
  {
      Element d = new Element(4);
  }
  ```

  Which of the following best describes the number of times that the code segment updates maxValue after it is initialized to 0?

  (A) It is never updated because it is declared static.  
  (B) It is updated 2 times, first when a is created and again when c is created.  
  (C) It is updated 3 times because the code segment creates exactly 3 Element objects.  
  (D) It is updated 4 times because the code segment creates exactly 4 Element objects.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    ① 创建 a(1)：1 > 0，maxValue = 1（第 1 次更新）。② 创建 b(1)：1 > 1 为 false，不更新。③ 创建 c(2)：2 > 1，maxValue = 2（第 2 次更新）。④ `getMaxValue() == 3` 为 false，d 从未创建。共更新 2 次。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点           | 关键内容                                     | 考试提示                                       |
| -------------- | -------------------------------------------- | ---------------------------------------------- |
| 类变量 static  | 属于类，所有对象共享                         | 每创建对象时构造方法对 static 变量的修改累计   |
| 类方法 static  | 用类名调用，只能访问类变量                   | static 方法内不能访问实例变量                  |
| 调用方式       | 类名.方法() → 必须是 static                  | 实例方法必须用对象调用                         |
| 更新次数       | 只有条件满足时才更新                         | 逐一追踪每次构造调用                           |
