---
layout: default
title: 3.9 this Keyword
parent: Unit 3
nav_order: 9
---

# 3.9 — this Keyword

## 3.9.A this 的用途

**`this`** 关键字在方法/构造方法内部引用**当前对象**：

- **区分参数与实例变量**：当参数名与实例变量同名时，`this.name` 明确指向实例变量。
- **把当前对象作为参数传递**：`this` 可以传给其他方法。
- **调用当前对象的其他方法**：`this.methodName()`。

{% raw %}
```java
public class Friend
{
    private String name;

    public Friend(String name)
    {
        this.name = name;   // 左边是实例变量，右边是参数
    }
}
```
{% endraw %}

{: .important}
> 当参数名与实例变量同名时，不带 `this` 的 `name = name;` 只是把参数赋给**它自己**，实例变量不会被赋值！必须写 `this.name = name;`。

## 3.9.B this 作为参数传递

`this` 可以表示"当前正在执行方法的那个对象"，常用于跨对象协作：

{% raw %}
```java
public void checkID(Checker c)
{
    c.validate(this);   // 把当前对象传给 Checker 的方法
}
```
{% endraw %}

{: .note}
> **类方法（static 方法）没有 `this` 引用**（EK 3.9.A.3）：static 方法不属于任何特定对象，因此内部**不能使用 `this`**。`this` 只能在**实例方法**和**构造方法**中使用。

- ### 例题 1 — 用 this 比较两个对象

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q13

  Consider the following class definition.

{% raw %}
  ```java
  public class Player
  {
      private int base;
      private int bonus;

      public Player()
      { /* implementation not shown */ }

      public int getTotal()
      {
          return base + bonus;
      }

      public boolean hasHigherScore(Player other)
      {
          /* missing code */
      }
  }
  ```
{% endraw %}

  The Player class contains a getTotal method, which returns the total score for the player.

  The class also contains a hasHigherScore method, which has a Player object as a parameter. The hasHigherScore method, when called on a given Player object, is intended to return true if the total score of the given Player is greater than the total score of the Player specified by the parameter. It is intended to return false otherwise.

  For example, suppose p1 and p2 are valid Player objects. If p1 has a higher total score than p2, `p1.hasHigherScore(p2)` should return true.

  Which of the following can be used to replace `/* missing code */` so that the hasHigherScore method works as intended?

  (A) `return this > other;`  
  (B) `return getTotal(this) > getTotal(other);`  
  (C) `return this.getTotal() > getTotal();`  
  (D) `return this.getTotal() > other.getTotal();`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `this` 指代调用该方法的对象（如 p1），`other` 是参数对象（如 p2）。比较两者的总分：`this.getTotal() > other.getTotal()`。选项 (D) 正确。正确答案是 **(D)**。

  </details>

- ### 例题 2 — this == other 与值比较

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q14

  Consider the following class declaration.

{% raw %}
  ```java
  public class Thing
  {
      private int val;

      public Thing(int v)
      {
          val = v;
      }

      public int getVal()
      {
          return val;
      }

      public String mystery(Thing other)
      {
          if (this == other)
          {
              return "yes";
          }
          else if (this.val == other.getVal())
          {
              return "maybe";
          }
          else
              return "no";
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than Thing.

  ```java
  Thing apple = new Thing(5);
  Thing banana = new Thing(5);
  System.out.println(apple.mystery(banana));
  System.out.println(banana.mystery(banana));
  ```

  What, if anything, is printed as a result of executing this code segment?

  (A) `yes` / `yes`  
  (B) `maybe` / `yes`  
  (C) `maybe` / `maybe`  
  (D) Nothing is printed because the Thing class does not compile.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `apple.mystery(banana)`：`this` 是 apple，`other` 是 banana。`this == other` 比较引用——apple 和 banana 是两个不同对象，为 false；`this.val == other.getVal()`（5 == 5）为 true，返回 "maybe"。`banana.mystery(banana)`：`this` 和 `other` 都是 banana，`this == other` 为 true，返回 "yes"。输出 "maybe" 和 "yes"。正确答案是 **(B)**。

  </details>

- ### 例题 3 — this.name = name

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part B, Q15

  Consider the following class definition.

{% raw %}
  ```java
  public class Friend
  {
      private String name;   // Line 3

      public Friend(String name)
      {
          name = name;       // Line 7
      }

      public String getName()
      {
          return name;       // Line 12
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than Friend. It is intended to print the string "Jessie" but does not work as intended because of an error in the Friend class.

  ```java
  Friend bestie = new Friend("Jessie");
  System.out.println(bestie.getName());
  ```

  Which of the following changes can be made to the Friend class so that this code segment works as intended?

  (A) Changing line 3 to `private String this.name;`  
  (B) Changing line 7 to `this.name = name;`  
  (C) Changing line 7 to `name = this.name;`  
  (D) Changing line 12 to `return this.name;`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    第 7 行 `name = name;` 中参数 name 与实例变量同名，这条语句只是把参数赋给它自己，实例变量 name 没有被赋值（保持 null）。应改为 `this.name = name;`——`this.name` 指实例变量，`name` 指参数。正确答案是 **(B)**。

  </details>

- ### 例题 4 — this 作为参数传递（Item/Checker）

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q11

  Consider the following class definitions.

{% raw %}
  ```java
  public class Item
  {
      private int IdNum;

      public Item(int id)
      {
          IdNum = id;
      }

      public int getIdNum()
      {
          return IdNum;
      }

      public void checkID(Checker c)
      {
          c.validate(this);     // 把当前 Item 对象传给 validate
      }
  }

  public class Checker
  {
      private int lastID = 0;

      public void validate(Item i)
      {
          int id = i.getIdNum();
          if (id == lastID)
          {
              System.out.println("ID " + id + ": invalid");
          }
          else
          {
              lastID = id;
              System.out.println("ID " + id + ": valid");
          }
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than Item or Checker.

  ```java
  Item i = new Item(23);
  Item j = new Item(55);
  Checker c = new Checker();
  i.checkID(c);
  j.checkID(c);
  j.checkID(c);
  i.checkID(c);
  ```

  What is printed as a result of executing the code segment?

  (A)
  ```
  ID 23: valid
  ID 55: valid
  ID 55: invalid
  ID 23: valid
  ```
  (B)
  ```
  ID 23: valid
  ID 55: valid
  ID 55: invalid
  ID 23: invalid
  ```
  (C)
  ```
  ID 23: valid
  ID 55: invalid
  ID 55: valid
  ID 23: valid
  ```
  (D)
  ```
  ID 23: invalid
  ID 55: valid
  ID 55: valid
  ID 23: invalid
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    ① `i.checkID(c)`：validate(i)，id = 23 ≠ lastID(0)，lastID = 23，输出 "ID 23: valid"。② `j.checkID(c)`：id = 55 ≠ 23，lastID = 55，输出 "ID 55: valid"。③ `j.checkID(c)`：id = 55 == 55，输出 "ID 55: invalid"（lastID 不变）。④ `i.checkID(c)`：id = 23 ≠ 55，lastID = 23，输出 "ID 23: valid"。正确答案是 **(A)**。

  </details>

- ### 例题 5 — this 传递当前对象（Class1/Class2）

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q12

  Consider the following class definitions.

{% raw %}
  ```java
  public class Class1
  {
      private int val1;

      public Class1()
      {
          val1 = 1;
      }

      public void init()
      {
          Class2 c2 = new Class2();
          c2.init(this, val1);   // this 指当前 Class1 对象
      }

      public void update(int x)
      {
          val1 -= x;
      }

      public int getVal()
      {
          return val1;
      }
  }

  public class Class2
  {
      private int val2;

      public Class2()
      {
          val2 = 2;
      }

      public void init(Class1 c, int y)
      {
          c.update(val2 + y);
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than Class1 or Class2.

  ```java
  Class1 c = new Class1();
  c.init();
  System.out.println(c.getVal());
  ```

  What, if anything, is printed as a result of executing the code segment?

  (A) 2  
  (B) 1  
  (C) -2  
  (D) Nothing is printed because the code segment does not compile.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    c 创建时 val1 = 1。`c.init()` 中 `this` 是 c，`c2.init(this, 1)` 把 c 和 val1(=1) 传给 Class2 的 init。init 调用 `c.update(val2 + y)` = `c.update(2 + 1)` = `c.update(3)`。update 执行 `val1 -= 3`，val1 = 1 − 3 = −2。打印 −2。正确答案是 **(C)**。

  </details>

- ### 例题 6 — this 传递与返回值

  > **Source:** AP Classroom New Unit 3 TopicQuestion MCQ, Q13

  Consider the following class definitions.

{% raw %}
  ```java
  public class MenuItem
  {
      private double price;

      public MenuItem(double p)
      {
          price = p;
      }

      public double getPrice()
      {
          return price;
      }

      public void makeItAMeal()
      {
          Combo meal = new Combo(this);   // 把当前 MenuItem 传给 Combo
          price = meal.getComboPrice();
      }
  }

  public class Combo
  {
      private double comboPrice;

      public Combo(MenuItem item)
      {
          comboPrice = item.getPrice() + 1.5;
      }

      public double getComboPrice()
      {
          return comboPrice;
      }
  }
  ```
{% endraw %}

  The following code segment appears in a class other than MenuItem or Combo.

  ```java
  MenuItem one = new MenuItem(5.0);
  one.makeItAMeal();
  System.out.println(one.getPrice());
  ```

  What, if anything, is printed as a result of executing the code segment?

  (A) 5.0  
  (B) 6.5  
  (C) 8.0  
  (D) Nothing is printed because the code does not compile.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    one 的 price = 5.0。`makeItAMeal()` 中 `new Combo(this)` 把 one 传给 Combo 构造方法，comboPrice = 5.0 + 1.5 = 6.5。然后 `price = meal.getComboPrice()`，one 的 price 变为 6.5。打印 6.5。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                       |
| ------------------ | -------------------------------------------- | ---------------------------------------------- |
| this 区分同名变量  | `this.name` 指实例变量，`name` 指参数        | `name = name;` 不会赋值实例变量                |
| this 指当前对象    | 在方法中代表调用该方法的对象                 | `this.getTotal()` 调用当前对象的方法           |
| this == other      | 判断两个引用是否指向同一个对象               | 不同对象即使值相同 `==` 也为 false             |
| this 作为参数      | `other.method(this)` 把当前对象传出去        | 追踪跨对象调用链                               |
