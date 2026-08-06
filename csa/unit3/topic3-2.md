---
layout: default
title: 3.2 Impact of Program Design
parent: Unit 3
nav_order: 2
---

# 3.2 — Impact of Program Design

## 3.2.A 程序设计的质量影响

**程序设计的质量**直接影响软件的**可靠性（reliability）**、安全性和用户体验：

- 充分**测试（testing）**可以发现逻辑错误，提高系统可靠性。
- 减少测试虽然能加快开发速度，但可能带来**隐藏错误**，降低可靠性。
- 程序对个人、社会、经济和文化可能产生**预期之外的影响**。

## 3.2.B 开源软件与知识产权

- **开源软件（Open Source）**：源代码公开、允许他人免费使用和修改的软件。其许可证允许程序员复用他人写好的代码，降低**知识产权（intellectual property）**风险。
- 使用开源代码可以减少重复开发工作，但**并不能**免除注释、抽象或前期设计。

{: .note}
> 一个程序即使初衷是解决某个问题，也可能产生**非预期的有害影响**——好的设计应当考虑潜在后果。

- ### 例题 1 — 减少测试的后果

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q4

  A programmer wants to speed up the development of a program by reducing the amount of testing performed on the program. Which of the following is most likely to be a consequence of this approach?

  (A) Decreased intellectual property concerns  
  (B) Decreased system reliability  
  (C) Increased intellectual property concerns  
  (D) Increased system reliability

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    测试可以发现程序中的错误。减少测试可能让错误未被发现，从而**降低系统可靠性（system reliability）**。正确答案是 **(B)**。

  </details>

- ### 例题 2 — 程序的非预期影响

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q5

  A software company created a program to help solve a problem in a community. Which of the following is a true statement about the program?

  (A) The program can be reused by other programmers without obtaining permission.  
  (B) The program could have unintended harmful effects beyond its intended use.  
  (C) The program should be implemented with as few abstractions as possible.  
  (D) The program will improve the system reliability of other programs.

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    程序的效果并不总能被完全预料：一个旨在解决问题的程序，也可能对社会、经济或文化产生**非预期的有害影响**。选项 (B) 正确。正确答案是 **(B)**。

  </details>

- ### 例题 3 — 开源代码的用途

  > **Source:** AP Classroom Unit 3 Progress Check: MCQ Part A, Q6

  Which of the following best explains why programmers often include open source code in their programs?

  (A) To utilize algorithms that eliminate the need to include comments in program code  
  (B) To utilize algorithms that have already been implemented while reducing the risk of raising intellectual property concerns  
  (C) To utilize algorithms that minimize the need for abstraction in a program  
  (D) To utilize algorithms that remove the requirement to design a program before implementing it

  <details markdown="block">
    <summary><b>点击查看解答</b></summary>

    **分析与解答：**  
    开源许可证允许程序员自由使用他人已实现的代码，从而复用成熟算法并**降低知识产权方面的风险**。正确答案是 **(B)**。

  </details>

---

## 考点总结

| 考点             | 关键内容                                     | 考试提示                                     |
| ---------------- | -------------------------------------------- | -------------------------------------------- |
| 测试与可靠性     | 充分测试提高可靠性；减少测试降低可靠性       | 测试是发现错误的关键手段                     |
| 非预期影响       | 程序可能带来预期外的社会/文化影响            | 好设计要考虑潜在后果                         |
| 开源软件         | 许可证允许复用代码，降低知识产权风险         | 开源不等于无需注释/设计                      |
| 知识产权         | 复用他人代码需遵守许可证                     | 开源降低风险                                 |
