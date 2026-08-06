---
layout: default
title: 1.2 Variables and Data Types
parent: Unit 1
nav_order: 2
---

# 1.2 — Variables and Data Types

## 1.2.A 数据类型

**数据类型（Data Type）** 是一组值以及在这些值上的一组对应操作。数据类型可以分为两大类：**基本类型（Primitive Type）** 和 **引用类型（Reference Type）**。 

AP CSA 课程中使用的三种基本数据类型是 `int`、`double` 和 `boolean`：

- **`int`**：整数，如 `1`、`-5`、`100`。
- **`double`**：实数（浮点数），如 `3.14`、`-0.5`、`99.9`。
- **`boolean`**：布尔值，只有 `true` 和 `false` 两个值。

**引用类型（Reference Type）** 用于定义非基本类型的对象，例如 `String`、`Scanner` 以及自定义的类。

{: .extra}
> **Exclusion Statement**：其他五种基本数据类型（`long`、`short`、`byte`、`float` 和 `char`）不在 AP CSA 课程的考试范围内。 

{: .important}
> 选择数据类型时，需要根据数据本身的特性来决定——整数用 `int`，实数用 `double`，是/否用 `boolean`，对象用引用类型。

- ### 例题 1 — 选择合适的数据类型

    > Source: AP Classroom Unit 1 Progress Check: MCQ Part A, Q6

    A code segment will use variables to represent a student's age, in years, and whether the student has a driver's license. Which of the following variable declarations are most appropriate for the code segment?

    (A) `boolean age;` / `double hasLicense;`  
    (B) `boolean age;` / `boolean hasLicense;`  
    (C) `int age;` / `boolean hasLicense;`  
    (D) `int age;` / `double hasLicense;`

    <details markdown="block>
      <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**  
      年龄通常用整数表示（如 15 岁、17 岁），所以 `int` 是最合适的数据类型。是否有驾照是一个「是/否」的判断，所以 `boolean` 是最合适的数据类型。选项 (C) 正确地使用了 `int` 表示年龄、`boolean` 表示是否有驾照，因此正确答案是 **(C)**。 [pdf_9]

    </details>

- ### 例题 2 — 选择合适的数据类型（类设计）

    > Source: Practice Exam 2 MCQ, Q2

    A student is developing a program that will store information about players of a video game, including each player's score and amount of time remaining, in seconds. Which of the following is the most appropriate design?

    (A) An Information class with Player instance variables for the score and the amount of time remaining.  
    (B) A Player class with int instance variables for the score and the amount of time remaining.  
    (C) A Player class, a Score class, and a Remaining Time class, each with an int instance variable.  
    (D) A Score class and a RemainingTime class, each with a Player instance variable.

    <details markdown="block>
      <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**
      分数和剩余时间（秒）都是整数值，因此用 `int` 类型存储是最合适的。同时，这两个属性都属于同一个 Player（玩家），将它们放在一个 `Player` 类中作为实例变量是最直接、最合理的设计。选项 (A) 使用了不合理的抽象；选项 (C) 和 (D) 引入了不必要的额外类。正确答案是 **(B)**。 [pdf_8]

    </details>

- ### 例题 3 — 区分基本类型与引用类型

    > Source: AP Classroom Unit 1 Progress Check: MCQ Part A, Q11

    Consider the following code segment.

    ```java
    double pi = 3.14;        // line 1
    pi = 3.14159;            // line 2
    double other = null;     // line 3
    double example;          // line 4
    example = pi;            // line 5
    ```

    Which of the following best describes the error in this code segment?

    (A) In line 2, pi is assigned a value after it was already assigned a value in line 1.  
    (B) In line 3, null cannot be assigned to a non-reference type.  
    (C) In line 4, example should be assigned a value.  
    (D) In line 5, a variable cannot be assigned to another variable.

    <details markdown="block>
      <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**  
      `null` 是一个特殊值，表示引用不指向任何对象，它只能赋值给引用类型变量。`double` 是基本类型，不是引用类型，因此不能将 `null` 赋值给 `double` 变量。这个例子清晰地区分了基本类型和引用类型的差异——基本类型存储实际值，而引用类型存储对象的引用（可以为 `null`）。正确答案是 **(B)**。

    </details>

---

## 1.2.B 变量声明

**变量（Variable）** 是一个存储位置，它保存一个值，并且该值在程序运行期间可以改变。每个变量都有一个名称（变量名）和一个关联的数据类型。基本类型的变量保存该类型的一个基本类型值。

**变量声明语法：**

```java
dataType variableName;           // 仅声明
dataType variableName = value;   // 声明并初始化
```

**变量初始化：** 变量在使用前**必须**被赋值。第一次赋值称为初始化，赋值必须来自**兼容**的数据类型。

**变量命名规范：**

- 变量名通常使用 **驼峰命名法（camelCase）**，首字母小写，如 `studentAge`、`hasLicense`
- 变量名必须以字母、下划线（`_`）或美元符号（`$`）开头，后续可以是字母、数字、下划线或美元符号
- 变量名不能是 Java 关键字（如 `int`、`double`、`boolean`、`class` 等）
- 变量名区分大小写（`age` 和 `Age` 是不同的变量）

**声明并初始化示例：**

```java
int score = 100;               // 声明 int 变量并初始化为 100
double price = 19.99;          // 声明 double 变量并初始化为 19.99
boolean isPassing = true;      // 声明 boolean 变量并初始化为 true
```

- ### 例题 4 — int 变量可存储的值

    > Source: AP Classroom Unit 1 Progress Check: MCQ Part A, Q4

    Consider the following variable declaration.

    ```java
    int x;
    ```

    Which of the following values can be stored in the variable x?

    (A) 0.5  
    (B) 1  
    (C) true  
    (D) false

    <details markdown="block>
      <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**
      `int` 变量只能存储整数（integer）值。`0.5` 是小数（需要 `double` 类型），`true` 和 `false` 是布尔值（需要 `boolean` 类型）。只有 `1` 是一个整数，可以存储在 `int` 变量中。正确答案是 **(B)**。 

    </details>

- ### 例题 5 — boolean 变量可存储的值

    > Source: AP Classroom Unit 1 Progress Check: MCQ Part A, Q5

    Consider the following variable declaration.

    ```java
    boolean b;
    ```

    Which of the following values can be stored in the variable b?

    (A) -1  
    (B) 0  
    (C) 1.0  
    (D) false

    <details markdown="block>
      <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**
      `boolean` 变量只能存储 `true` 或 `false` 两个值。`-1` 和 `0` 是整数，`1.0` 是浮点数，只有 `false` 是合法的布尔值。正确答案是 **(D)**。 

    </details>

- ### 例题 6 — 变量必须先声明再使用

    > Source: AP Classroom New Unit 1 TopicQuestion MCQ, Q9

    Consider the following code segment.

    ```java
    int x = 5;
    int y = 6;
    /* missing code */
    ```

    Which of the following can be used to replace `/* missing code */` so that the code segment compiles?

    (A) `boolean z = true;`  
    (B) `int z = 0.0;`  
    (C) `int z = 0;`  
    (D) `z = 0;`

    <details markdown="block>
      <summary><b>点击查看解答</b></summary>
    
      **分析与解答：**
      在 Java 中，变量必须先声明才能使用。选项 (A) 声明了一个 `boolean` 类型的变量 `z`，语法正确，可以编译。选项 (B) 试图将 `double` 值 `0.0` 赋值给 `int` 变量，类型不兼容，无法编译。选项 (C) 声明了 `int` 类型的变量 `z` 并初始化为 `0`，语法正确，可以编译。选项 (D) 中 `z` 未声明就直接使用，无法编译。该题中选项 (A) 和 (C) 都能使代码段编译通过，但题目要求选出**可以使用**的代码，注意变量声明时必须确保类型与值匹配。 

    </details>

---

## 考点总结

| 考点               | 关键内容                                                  | 考试提示                                 |
| ------------------ | --------------------------------------------------------- | ---------------------------------------- |
| 数据类型分类       | 基本类型（`int`、`double`、`boolean`）vs 引用类型         | 牢记三种基本类型，其他五种不在考试范围内 |
| 选择合适的数据类型 | 整数→`int`，实数→`double`，是/否→`boolean`，对象→引用类型 | 根据数据的实际含义选择类型               |
| 变量声明           | `type name;` 或 `type name = value;`                      | 变量必须先声明再使用，声明不能重复       |
| 变量初始化         | 变量使用前必须被赋值                                      | 未初始化的变量不能参与表达式运算         |
| `null` 的使用      | `null` 只能赋值给引用类型，不能给基本类型                 | 这是基本类型和引用类型的核心区别之一     |