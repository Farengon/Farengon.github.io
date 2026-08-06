---
layout: default
title: 4.1 Ethical and Social Issues Around Data Collection
parent: Unit 4
nav_order: 1
---

# 4.1 — Ethical and Social Issues Around Data Collection

## 4.1.A 数据收集的伦理问题

收集和使用数据时，需要考虑**隐私（privacy）**、**偏见（bias）**和**知情同意（informed consent）**等伦理问题：

- **隐私**：个人数据不应被未经授权地访问或泄露。
- **数据封装**：把数据声明为 `private`、通过受控方法访问，是保护数据的重要手段。
- **自愿参与的偏差**：仅限有网络且有兴趣的人参与调查，样本可能**不具有代表性**。

{: .note}
> 即使某个类有 `private` 字段，若其他 `public` 字段/方法可以被外部利用来拼出个人信息，仍然存在隐私风险。

## 4.1.B 隐私风险分析

- `public` 实例变量可以被**任何外部类直接访问**——这是最大的隐私风险来源。
- 访问方法（getter）如果有密码等防护，能在一定程度上保护数据，但**数据本身的可见性**才是关键。
- **算法偏见（Algorithmic Bias）**：程序中**系统性的、反复出现的错误**会对特定用户群体产生不公平的结果。程序员在使用数据集前应了解数据的**收集方式**及其**潜在的偏差**。
- **不完整/不准确的数据**：某些数据集可能**不完整或包含错误数据**，使用这类数据会使程序工作不正确或低效。
- **数据集的适用性（EK 4.1.C.1）**：数据集的内容可能与**特定问题或主题**相关，用它回答**不同的问题**或推断其他信息可能给出错误答案——选择数据集时要确认它与要回答的问题匹配。

- ### 例题 1 — 公开字段导致的隐私风险

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q1

  The following SocialMediaAccount class is used to represent a user of a social media site. It includes attributes for the user's username, real name, email address, and ID number.

  ```java
  public class SocialMediaAccount
  {
      public String username;    // The user's username
      private String realName;   // The user's real name
      private String email;      // The user's email address
      private int idNumber;      // The user's ID number

      public String getInfo(String str)
      {
          if (str.equals(username))
          {
              return realName + " " + email + " " + idNumber;
          }
          else
          {
              return "username does not match";
          }
      }
  }
  ```

  What is the greatest personal privacy risk posed to users by this class design?

  (A) The class contains no mutator methods.  
  (B) The class utilizes data encapsulation.  
  (C) Personal information can be determined from outside the class using information that has public visibility.  
  (D) If the ID numbers are assigned consecutively, the total number of users can be determined.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    `username` 是 `public` 实例变量，外部类可以直接访问。知道 username 后，就可以调用 `getInfo` 方法获取用户的真实姓名和邮箱等个人信息——这是最大的隐私风险。正确答案是 **(C)**。

  </details>

- ### 例题 2 — 公开实例变量的隐私问题

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q2

  The following class is used to store information about a customer.

  ```java
  public class Customer
  {
      public String cName;           // The customer's name
      public String cPaymentInfo;    // The customer's payment information

      public String getName()
      { /* implementation not shown */ }

      public String getPaymentInfo(String password)
      { /* implementation not shown */ }
  }
  ```

  Which of the following statements best describes the privacy of the customer's payment information?

  (A) It is considered private because retrieving it requires a password.  
  (B) It is considered private because the value of the instance variable cName is not easy to guess.  
  (C) It is not considered private because the instance variables are declared public.  
  (D) It is not considered private because the `getName` method has no password parameter.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    虽然 getPaymentInfo 需要密码，但 `cPaymentInfo` 本身声明为 **public**，任何外部类都可以**直接访问**这个实例变量，绕过密码检查。因此支付信息并不私密。正确答案是 **(C)**。

  </details>

- ### 例题 3 — 调查数据的偏差

  > **Source:** AP Classroom Unit 4 Progress Check: MCQ Part A, Q3

  A research team is analyzing survey data to determine the average number of hours high school students spend on homework each night. The survey was conducted online, and students volunteered to participate.

  Which of the following factors is most important for the team to consider before drawing conclusions from the data?

  (A) The survey data are considered reliable because the survey used self-reported responses from students.  
  (B) The survey results may not represent all high school students because only those with Internet access and interest in the topic participated.  
  (C) The survey ensures accuracy because students were able to choose whether or not to participate.  
  (D) The method of survey collection does not matter as long as there are a large number of responses in the data set.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    在线、自愿参与的调查方式引入了**潜在偏差**：只有能上网且对话题感兴趣的学生才会参与，样本可能无法代表所有高中生。这是得出结论前最重要的考虑因素。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                       |
| ---------------- | -------------------------------------------- | ---------------------------------------------- |
| 隐私风险         | public 数据可被外部直接访问                  | 公开字段 + 可拼凑信息 = 隐私风险               |
| 数据封装         | private 数据 + 受控方法访问                  | getter 有密码 ≠ 数据私密                       |
| 调查偏差         | 自愿参与、仅网络用户 → 样本不具代表性        | 数据量大也不能消除偏差                         |
| 伦理意识         | 收集数据要考虑隐私、同意、偏见               | 分析结论前先评估样本                          |
