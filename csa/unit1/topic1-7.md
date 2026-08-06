---
layout: default
title: 1.7 Application Program Interface (API) and Libraries
parent: Unit 1
nav_order: 7
---

# 1.7 — Application Program Interface (API) and Libraries

## 1.7.A 应用编程接口（API）与库

**应用编程接口（Application Program Interface, API）** 是一个类的**公开方法清单**，它描述了外部代码可以对该类的对象调用哪些方法，以及每个方法的参数和返回类型。API 只说明方法**做什么**，不透露方法**如何实现**。

**库（Library）** 是一组相关的类和 API 的集合，程序员可以直接使用库中已经写好的类，而不必从零开始实现。Java 标准库（Java Standard Library）就包含了 `Math`、`String`、`Scanner` 等常用类。

{: .note}
> 使用库中的类时，我们只需要查看该类的 API（即公开的方法签名和说明），而不需要关心其内部实现细节——这正是**抽象（abstraction）**的体现。

## 1.7.B 属性（Attributes）与行为（Behaviors）

类规格说明（class specification）通常会描述两类信息：

- **属性（Attributes）**：存储在**变量**中的信息，用于描述对象的状态，如车辆的 make、model、year。
- **行为（Behaviors）**：由**方法**定义的、对象可以执行的操作，如 `move()`、`rotate()`。

{: .important}
> 判断一个描述是属性还是行为：**变量 → 属性，方法 → 行为**。对象是类的实例，而属性/行为是对象拥有的特征/操作。

- ### 例题 1 — 属性 vs 行为（Vehicle）

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q7

  The following is an excerpt of a class specification that appears in an API library.

  ```
  public class Vehicle
  ```

  The Vehicle class is used to create objects that represent vehicles.

  The Vehicle class has make, model, and year variables that hold information about the vehicle's characteristics.

  The Vehicle constructor initializes a Vehicle object with the given make, model, and year.

  The getMake(), getModel(), and getYear() methods return information about the vehicle.

  Based on the class specification, which of the following descriptions is accurate?

  (A) Vehicle objects are attributes of the variables make, model, and year.  
  (B) Vehicle objects are behaviors of the variables make, model, and year.  
  (C) The variables make, model, and year are attributes of Vehicle objects.  
  (D) The variables make, model, and year are behaviors of Vehicle objects.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    make、model 和 year 是**变量**，它们存储了车辆的信息，因此它们是 Vehicle 对象的**属性（attributes）**。属性由变量（实例变量）承载，而不是方法。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 行为 vs 属性（Robot）

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q8

  The following is an excerpt of a class specification that appears in an API library.

  ```
  public class Robot
  ```

  A Robot specifies a robot that moves around a two-dimensional coordinate grid.

  The Robot class has xCoordinate and yCoordinate variables that hold information about the robot's location on the grid.

  The Robot constructor initializes a Robot object with the given coordinates.

  The move() and rotate() methods are used to modify the robot's location on the grid.

  Based on the class specification, which of the following descriptions is accurate?

  (A) Robot objects are attributes of the methods move and rotate.  
  (B) Robot objects are behaviors of the methods move and rotate.  
  (C) The methods move and rotate represent attributes of Robot objects.  
  (D) The methods move and rotate represent behaviors of Robot objects.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    move() 和 rotate() 是**方法**，方法定义的是类的实例"能做什么"，即**行为（behaviors）**。属性由变量承载，行为由方法承载。正确答案是 **(D)**。

  </details>

- ### 例题 3 — 属性与行为的组合判断（Parcel）

  > **Source:** AP Classroom Unit 1 Progress Check: MCQ Part B, Q9

  The following is an excerpt of a class specification that appears in an API library.

  ```
  public class Parcel
  ```

  A Parcel class is used to create objects that represent the status of packages that are delivered to customers.

  The Parcel class has status and location variables that hold information about a package's shipping status and location.

  The Parcel constructor initializes a Parcel object with its initial status and location.

  The updateStatus() and updateLocation() methods are used to update the status and location of a package.

  Based on the class specification, which of the following is a true statement about Parcel objects?

  (A) status and location are attributes; updateStatus and updateLocation are behaviors.  
  (B) status and location are behaviors; updateStatus and updateLocation are attributes.  
  (C) status and updateStatus are attributes; location and updateLocation are behaviors.  
  (D) status and updateStatus are behaviors; location and updateLocation are attributes.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    status 和 location 是**变量**，用于存储包裹的状态信息，属于**属性**；updateStatus() 和 updateLocation() 是**方法**，用于更新状态，属于**行为**。选项 (A) 正确区分了两者。正确答案是 **(A)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                             | 考试提示                                     |
| ------------------ | ---------------------------------------------------- | -------------------------------------------- |
| API 与库           | API 是公开方法清单；库是类的集合                     | 使用库中类只需看 API，无需关心实现           |
| 属性（Attributes） | 由**变量**承载，描述对象的状态信息                   | 变量 → 属性                                  |
| 行为（Behaviors）  | 由**方法**承载，描述对象能执行的操作                 | 方法 → 行为                                  |
| 类规格说明阅读     | 根据 API 描述区分变量/方法、属性/行为                | 注意题中"variables hold information"与"methods modify"的措辞 |
