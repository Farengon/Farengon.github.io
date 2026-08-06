---
layout: default
title: 4.2 Introduction to Using Data Sets
parent: Unit 4
nav_order: 2
---

# 4.2 — Introduction to Using Data Sets

## 4.2.A 从数据集中提取信息

**数据集（Data Set）** 是一组特定信息/数据的集合。从数据集中提取信息时：

- 只能回答**数据中确实包含**的问题。
- 数据集可以被**操作和分析**来解决问题——分析时**逐个（一次一个）**访问和处理集合中的值。
- 注意哪些信息可以直接计算、哪些信息数据集中**没有**。
- 多个数据集可以通过**共同的关键字段**（如项目名称、开发者 ID）合并分析。

{: .note}
> 判断"能否从数据集中得出某结论"：检查该结论所需的所有数据点是否都在数据集中。缺少任何必需数据（如总人数），就无法计算相应的比例或百分比。

**数据的可视化表示：** 数据可以用**图表（chart）**或**表格（table）**来表示，这些可视化形式有助于**规划**处理数据的算法（EK 4.2.A.3）。

## 4.2.B 数据集的合并分析

当需要结合多个数据源的信息时，找两个数据集中**共同的关键字**，通过它把数据集关联起来。

- ### 例题 1 — 零售交易数据分析

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q4

  A retail store has a data set that contains the following information for each sales transaction.

  - Store location
  - Transaction date
  - Time of purchase
  - Sales amount, in dollars
  - Product category (electronics, clothing, home goods, grocery, etc.)

  Which of the following is most easily determined from the data in the data set?

  (A) Customer purchasing preferences by category for each store location  
  (B) Customer satisfaction levels by category for each date  
  (C) The name of the most popular product at each location  
  (D) The quantity available for each product at each store location

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    数据集中有门店位置和产品类别，可以按门店统计各类别的销售情况（即每个门店各类别的购买偏好）。数据集中**没有**满意度、具体产品名称或库存数量信息。正确答案是 **(A)**。

  </details>

- ### 例题 2 — 无法确定的信息

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q5

  A data set contains information for all high schools in a school district. The following information from the previous year is available for each school in the district.

  - The name of the high school
  - The number of students who arrived at school late 1 or more times during the year
  - The number of students who arrived at school late 10 or more times during the year
  - The number of students who submitted medical excuse documentation for 1 or more of their late arrivals
  - The percentage of students who voted to delay the school start time by one hour

  The following shows a portion of the data set for a district with 13 high schools.

  | High School Name | Number of Students Late at Least 1 Time | Number of Students Late at Least 10 Times | Number of Students Who Submitted Medical Excuse Documentation | Percent of Student Population Who Voted for Later Start Time |
  | ---------------- | --------------------------------------- | ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | School A         | 402                                     | 59                                        | 179                                                          | 62%                                                          |
  | School B         | 63                                      | 2                                         | 48                                                           | 29%                                                          |
  | ...              | ...                                     | ...                                       | ...                                                          | ...                                                          |
  | School M         | 163                                     | 37                                        | 44                                                           | 84%                                                          |

  Which of the following information cannot be determined using only the information in the data set?

  (A) The district-wide total number of students who were late to school at least 10 times  
  (B) The district-wide total number of students who were late to school between 1 and 9 times, inclusive  
  (C) The district-wide percentage of students who voted for a later school start time  
  (D) The district-wide percentage of the students who were late at least 1 time who submitted medical excuse documentation for at least 1 late arrival

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    表中只有"投票推迟上课时间的学生的**百分比**"，没有各校的**总学生人数**，因此无法算出全学区投票学生的**总人数**和百分比。(A) 可以把各校"迟到至少 10 次"人数相加；(B) 用"至少 1 次"减去"至少 10 次"再求和；(D) 用文档人数除以迟到人数。只有 (C) 缺少必需的总人数数据。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 数据集合并

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q6

  A software developer wants to determine which programming language is most commonly used in different types of software projects. They have access to the following data sets.

  - Data set 1 contains entries for each registered developer, including their unique developer ID and their favorite programming language.
  - Data set 2 contains entries for each software project, including project name, type of project, and the developer ID of the project creator.
  - Data set 3 contains entries for each completed project, including project name and user ratings.
  - Data set 4 contains entries for each software project, including project name and all programming languages used in the project.

  Which two data sets can be combined and analyzed to determine the desired information?

  (A) Data sets 1 and 2  
  (B) Data sets 2 and 4  
  (C) Data sets 3 and 4  
  (D) Data sets 1 and 3

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    需要知道每个项目**类型**（数据集 2 有）和每个项目使用的**编程语言**（数据集 4 有）。两个数据集都有"项目名称"字段，可以合并，从而分析不同类型项目中语言的使用情况。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点               | 关键内容                                     | 考试提示                                     |
| ------------------ | -------------------------------------------- | -------------------------------------------- |
| 数据可得性         | 只能回答数据中确实包含的问题                 | 检查所需数据点是否都在数据集中               |
| 缺失数据           | 缺少总人数等数据 → 无法计算比例              | 百分比 ≠ 人数                                |
| 数据集合并         | 通过共同关键字（如项目名）关联               | 选择包含所需字段的两个数据集                 |
| 信息提取           | 明确每个字段能支撑什么样的结论               | 区分"可确定"与"不可确定"                     |
