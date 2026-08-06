---
layout: default
title: 3.1 Abstraction and Program Design
parent: Unit 3
nav_order: 1
---

# 3.1 — Abstraction and Program Design

## 3.1.A 抽象（Abstraction）

**抽象（Abstraction）** 是在程序中隐藏不必要的细节、只保留关键信息的过程。通过抽象，程序员可以：

- 把复杂问题分解成更小、更易管理的部分；
- 只关注"做什么"，而暂时忽略"怎么做"；
- 复用已有的类和库。

在面向对象编程中，**类（Class）** 就是一种抽象工具：它把相关的**属性（attributes）**和**行为（behaviors）**封装在一起。

**数据抽象（Data Abstraction）** 把数据类型的**抽象性质**与**具体表示细节**分离开来——给数据起一个名字（如实例变量 `score`），而不必关心它的内部表示。**属性（Attribute）** 就是一种数据抽象：定义在类中的**实例变量**（每个对象各有一份）或**类变量**。

**过程抽象（Procedural Abstraction）** 给一个过程起名字（方法名），使用该方法时只需知道它**做什么**，不必知道**怎么做**。**方法分解（method decomposition）** 把较大的行为拆分成多个较小的方法。

{: .note}
> 设计类时，先确定这个类需要哪些**属性**（用什么类型的变量存储）和**行为**（提供哪些方法），这是**程序设计（Program Design）**的第一步。

## 3.1.B 类设计：属性与行为

- **属性（Attribute）**：类的状态信息，用实例变量存储。如 Player 类的 score（分数）。
- **行为（Behavior）**：类能执行的操作，用方法实现。如 Player 类的 getScore、setScore。

{: .important}
> 选择属性的数据类型要贴合其含义：名字用 `String`、年龄/数量用 `int`、小数用 `double`。

- ### 例题 1 — 选择属性类型

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q1

  A student is developing a class that will store information about pets, including each pet's name and age. Which of the following sets of attributes is most appropriate for this class?

  (A) One String attribute that includes the pet's name and age  
  (B) One String attribute for the pet's name and one String attribute for the pet's age  
  (C) One String attribute for the pet's name and one int attribute for the pet's age  
  (D) One int attribute for the pet's name and one int attribute for the pet's age

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    名字最好用 `String` 表示；年龄是整数，最好用 `int` 表示。选项 (C) 正确地为每个属性选择了合适的类型。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 类图设计（Fruit）

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q2

  The Fruit class contains attributes for a fruit's type, color, and quantity. The class also contains methods to allow the attributes to be accessed outside the class.

  A class design diagram for the *Fruit* class contains three sections. The first section contains the class name, the second section contains three instance variables and their data types, and the third section contains three methods and their return types. The + symbol indicates a public designation, and the - symbol indicates a private designation.

  | Fruit |
  | ----- |
  | - type : String |
  | - color : String |
  | (missing instance variable) |
  | + getType() : String |
  | + getColor() : String |
  | (missing method) |

  Which of the following are the most appropriate replacements for `(missing instance variable)` and `(missing method)`?

  (A) Replacing (missing instance variable) with `- quantity : String` and replacing (missing method) with `+ getQuantity() : String`  
  (B) Replacing (missing instance variable) with `- quantity : int` and replacing (missing method) with `+ getQuantity() : int`  
  (C) Replacing (missing instance variable) with `- quantity : int` and replacing (missing method) with `+ getQuantity() : String`  
  (D) Replacing (missing instance variable) with `- quantity : String` and replacing (missing method) with `+ getQuantity() : int`

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    水果数量是非负整数，因此 quantity 实例变量和 getQuantity 方法的返回类型都应使用 `int`。选项 (B) 正确。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 属性与行为的区分（Player）

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q3

  A student is developing a Player class to represent a player in a game. The class should allow other classes to access and modify the player's score.

  Which of the following sets of attributes and behaviors is most appropriate for the Player class design?

  (A) Attributes: none / Behaviors: setScore and getScore  
  (B) Attributes: setScore and getScore / Behaviors: none  
  (C) Attributes: getScore and setScore / Behavior: score  
  (D) Attribute: score / Behaviors: getScore and setScore

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    分数是玩家的状态信息，应作为**属性（score）**存储；允许其他类查看和修改分数，通过**行为（getScore 和 setScore 方法）**实现。选项 (D) 正确区分了属性与行为。正确答案是 **(D)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                     |
| ---------------- | -------------------------------------------- | -------------------------------------------- |
| 抽象             | 隐藏细节、聚焦关键信息                       | 类是对属性和行为的封装                       |
| 程序设计         | 先确定属性与行为再实现                       | 属性用变量、行为用方法                       |
| 属性类型选择     | 名字→String，整数→int，小数→double          | 类型与含义匹配                               |
| 访问方式         | 外部类通过 getter/setter 访问私有属性        | `+` 公开、`-` 私有                           |
