---
layout: default
title: 1.14 Calling Instance Methods
parent: Unit 1
nav_order: 14
---

# 1.14 — Calling Instance Methods

## 1.14.A 实例方法（Instance Methods）

**实例方法（Instance Method）** 是**非 static** 的方法，必须通过**对象**调用，使用**点运算符（.）**：

```java
AnimalPrinter myPrinter = new AnimalPrinter();
myPrinter.printDog();        // 在对象 myPrinter 上调用实例方法
myPrinter.printCat();
```

{: .important}
> - 实例方法通过 `对象名.方法名(实参)` 调用。
> - 不能用**类名**调用实例方法（`AnimalPrinter.printDog()` 是错的）——只有 static 方法才能用类名调用。
> - 在**同一个类内部**可以直接用方法名调用，无需对象前缀。
> - 在 **null 引用**上调用实例方法会抛出 **NullPointerException**。例如：`String s = null; s.length();` 会崩溃，因为 null 不指向任何对象。

## 1.14.B 实例方法与类方法（static）的区别

| 调用方式                       | 方法类型      | 示例                          |
| ------------------------------ | ------------- | ----------------------------- |
| `对象.方法()`                  | 实例方法      | `p.getAge()`                  |
| `类名.方法()`                  | 类方法 static | `Person.getAge()`（错误用法见下） |

- ### 例题 1 — 在对象上调用实例方法

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q13

  The AnimalPrinter class includes the following two methods.

  | Method Signature        | Explanation                                            |
  | ----------------------- | ------------------------------------------------------ |
  | `public void printDog()` | Prints the word "dog" and then moves the cursor to a new line. |
  | `public void printCat()` | Prints the word "cat" and then moves the cursor to a new line. |

  The method myMethod appears in a class other than AnimalPrinter. The method is intended to produce the following output.

  ```
  dog
  cat
  ```

  Assume that an AnimalPrinter object myPrinter has been properly declared and initialized inside myMethod. Which of the following code segments, if located in myMethod, will produce the intended output?

  (A)
  ```java
  printDog();
  printCat();
  ```
  (B)
  ```java
  printDog(AnimalPrinter);
  printCat(AnimalPrinter);
  ```
  (C)
  ```java
  AnimalPrinter.printDog();
  AnimalPrinter.printCat();
  ```
  (D)
  ```java
  myPrinter.printDog();
  myPrinter.printCat();
  ```

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    实例方法必须通过对象调用。myMethod 在 AnimalPrinter 类之外，不能直接调用方法名（选项 A），也不能用类名调用（选项 C，那是 static 方法的调用方式）。选项 (D) 用对象 `myPrinter` 调用两个实例方法，正确。正确答案是 **(D)**。

  </details>

- ### 例题 2 — 实例方法不能用类名调用

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q14

  Consider the following information about the Person class.

  - The class has an int attribute age that represents a person's age.
  - The class has a non-static getAge method that has no parameters and returns the value of age. This method can be called from another class.

  The following code segments each appear in a class other than Person. Assume that `p` is a Person object whose age attribute is equal to 16.

  **Code Segment 1**

  ```java
  int val1 = p.getAge();
  System.out.println(val1);
  ```

  **Code Segment 2**

  ```java
  int val2 = Person.getAge();
  System.out.println(val2);
  ```

  What, if anything, is printed as a result of executing each of the code segments?

  (A) Both code segments print 16.  
  (B) Code segment 1 prints 16, but code segment 2 prints nothing because it will not compile.  
  (C) Code segment 2 prints 16, but code segment 1 prints nothing because it will not compile.  
  (D) Neither code segment will print anything because they will not compile.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    getAge 是非 static 方法（实例方法），必须用对象调用：`p.getAge()` 返回 16 并打印。代码段 2 用类名 `Person.getAge()` 调用实例方法，编译失败。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 实例方法带参数

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q15

  The Dog class contains a non-static method named calculateWalkLength which can be called from a class other than Dog. The method takes an integer parameter for the number of minutes a dog is taken for a walk and returns a double representing the number of miles walked during that time.

  The following code segment appears in a class other than Dog. The statement in line 2 causes a compile-time error.

  ```java
  Dog fido = new Dog();                  // line 1
  double miles = calculateWalkLength(fido, 90);  // line 2
  ```

  Which of the following can be used to replace line 2 so that this code segment will compile without error?

  (A) `double miles = calculateWalkLength(90);`  
  (B) `double miles = Dog.calculateWalkLength(fido, 90);`  
  (C) `double miles = Dog.calculateWalkLength(90);`  
  (D) `double miles = fido.calculateWalkLength(90);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    calculateWalkLength 是非 static 方法且只有一个 int 参数。正确调用方式是用 Dog 对象 `fido` 调用并传入一个 int 实参：`fido.calculateWalkLength(90)`。选项 (A) 缺少对象；(B)(C) 用类名调用实例方法是错误的。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 实例方法的调用语法（Book）

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q3

  The Book class includes the following method.

  | Method Signature                       | Explanation                              |
  | -------------------------------------- | ---------------------------------------- |
  | `public int getNumPages(int ch)`       | Returns the number of pages in chapter number ch |

  Assume that Book object book1 and int variable c have been properly declared and initialized in a class other than Book. Which of the following statements will compile without error?

  (A) `int pages = getNumPages(Book book1, int c);`  
  (B) `int pages = getNumPages(book1, c);`  
  (C) `int pages = book1.getNumPages(int c);`  
  (D) `int pages = book1.getNumPages(c);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    正确语法是 `book1.getNumPages(c)`：用对象 book1 调用方法，传入实参 c（声明中不带类型）。选项 (A)(B) 直接使用方法名而缺少对象，且 (A) 在实参中写类型也是错的；(C) 在实参中写 `int c` 也是错的。正确答案是 **(D)**。

  </details>

- ### 例题 5 — 实例方法与实参传递（Game）

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q10

  The Game class includes the following method.

  | Method Signature              | Explanation                          |
  | ----------------------------- | ------------------------------------ |
  | `public void addPoints(int pts)` | Increases the number of points by pts |

  Assume that the Game object myGame and the int variable points have been properly declared and initialized in a class other than Game. Which of the following code segments is a valid method call?

  (A) `myGame.addPoints(int points);`  
  (B) `myGame.addPoints(points);`  
  (C) `addPoints(Game myGame, int points);`  
  (D) `addPoints(myGame, points);`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    正确的调用是 `myGame.addPoints(points)`：对象 + 点运算符 + 方法名 + 实参（不带类型声明）。选项 (A) 在实参里写类型；(C)(D) 缺少对象且方法名直接调用。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 实例方法调用     | `对象.方法名(实参)`                          | 必须通过对象调用                               |
| 类名调用限制     | 实例方法不能用类名调用（static 才可以）      | `Dog.calculateWalkLength()` → 编译错误         |
| 实参写法         | 实参只写值/变量，不写类型                    | `book1.getNumPages(c)` 而非 `(int c)`          |
| 同类内部调用     | 同类中可直接调用方法名（无前缀）             | 跨类必须用对象                                 |
| NullPointerException | null 引用上调用方法会抛异常              | `String s = null; s.length();` → 崩溃          |
