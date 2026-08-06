---
layout: default
title: "1.12 Objects: Instances of Classes"
parent: Unit 1
nav_order: 12
---

# 1.12 — Objects: Instances of Classes

## 1.12.A 对象与类

**类（Class）** 是一种定义对象类型的数据类型，它决定了对象的**属性（attributes/实例变量）**和**行为（behaviors/方法）**。

**对象（Object）** 是类的一个**实例（instance）**。当用 `类型名 变量名 = new 类名(...)` 声明变量时，就创建了该类的一个对象，例如：

```java
Student greg;          // greg 是 Student 类型的变量
greg = new Student();  // greg 现在引用一个 Student 对象
```

{: .important}
> - 对象是**类**的实例：`greg` 是 `Student` 类的一个实例。
> - 类**不是**对象的实例；对象拥有的**属性**（实例变量）才是对象的状态信息。

## 1.12.B 对象的属性（Attributes）

对象的**属性**是存储在该对象实例变量中的信息。不同类的对象有不同的属性。例如：

- `Student` 对象可能有属性：`grade`（年级）、`name`（姓名）、`average`（平均分）。
- `Parent` 对象可能有属性：`parentName`、`email`。

- ### 例题 1 — 对象是类的实例

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q7

  A teacher has created a Student class. The class contains the following.

  - An int variable named grade to represent the student's grade level.
  - A String variable named name to represent the student's name.
  - A double variable named average to represent the student's grade point average.
  - A method named updateAverage that updates the value of average.

  The object greg will be declared as type Student.

  Which of the following descriptions is accurate?

  (A) greg is an instance of the Student class.  
  (B) greg is an instance of three attributes.  
  (C) Student is an instance of the greg object.  
  (D) updateAverage is an instance of the Student class.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    greg 被声明为 Student 类型，因此 greg 是 **Student 类的一个实例（instance）**。类不是对象的实例，方法也不是类的实例。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 不同对象的属性

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part C, Q8

  A school administrator has created a Student class. The class contains variables to represent the following.

  - An int variable named studentID to represent the student's ID number.
  - A String variable named studentName to represent the student's name.

  The school administrator has also created a Parent class. The class contains variables to represent the following.

  - A String variable named parentName to represent the parent's name.
  - A String variable named email to represent the parent's e-mail address.

  The object penelope will be declared as type Student. The object mrsPatel will be declared as type Parent.

  Which of the following descriptions is accurate?

  (A) An attribute of the penelope object is email.  
  (B) An attribute of the penelope object is Parent.  
  (C) An attribute of the penelope object is Student.  
  (D) An attribute of the mrsPatel object is email.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    mrsPatel 是 Parent 类的实例，Parent 类的属性是 `parentName` 和 `email`，因此 email 是 mrsPatel 对象的一个属性。penelope 是 Student 类的实例，其属性是 studentID 和 studentName，不含 email。正确答案是 **(D)**。

  </details>

- ### 例题 3 — 对象与属性的关系（Car）

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q11

  A student has created a Car class. The class contains the following attributes.

  - A String variable named color to represent the color of the car.
  - An int variable named year to represent the year the car was made.
  - A String variable named make to represent the manufacturer of the car.
  - A String variable named model to represent the model of the car.

  Assume that vehicle is a variable of type Car that has been properly declared and initialized.

  Which of the following best describes a valid relationship?

  (A) An instance of the vehicle class is Car.  
  (B) An instance of the Car object is vehicle.  
  (C) An attribute of the year object is int.  
  (D) An attribute of the vehicle object is color.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    vehicle 是 Car 类的一个实例，它有四个属性：color、year、make、model。因此"color 是 vehicle 对象的属性"是正确的。选项 (A)(B) 混淆了类与实例的关系；(C) 把 year（属性名）当作对象。正确答案是 **(D)**。

  </details>

- ### 例题 4 — 实例与类（Song）

  > **Source:** AP Classroom New Unit 1 TopicQuestion MCQ, Q28

  A student has created a Song class. The class contains the following three variables.

  - A String variable named artist to represent the artist name.
  - A String variable named title to represent the song title.
  - A String variable named album to represent the album title.

  The object happyBirthday will be declared as type Song.

  Which of the following statements is true?

  (A) artist, title, and album are instances of the Song class.  
  (B) happyBirthday is an instance of three String objects.  
  (C) happyBirthday is an instance of the Song class.  
  (D) Song is an instance of the happyBirthday object.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    happyBirthday 被声明为 Song 类型，因此 happyBirthday 是 **Song 类的一个实例**。artist、title、album 是 Song 类的属性，不是实例；Song 不是 happyBirthday 的实例。正确答案是 **(C)**。

  </details>

---

## 考点总结

| 考点           | 关键内容                                     | 考试提示                                           |
| -------------- | -------------------------------------------- | -------------------------------------------------- |
| 对象是类的实例 | `类型名 变量 = new 类名()` 创建对象          | 对象是类的实例，类不是对象的实例                   |
| 属性           | 存储在实例变量中的信息                       | 属性属于对象，如 color 是 vehicle 的属性           |
| 常见错误说法   | "类 is an instance of 对象"、"方法 is an instance of 类" | 这类说法都是错误的                       |
