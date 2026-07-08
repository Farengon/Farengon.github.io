---
layout: default
title: 3.1 Abstraction and Program Design
parent: Unit 3
nav_order: 1
---

# 3.1 Abstraction and Program Design

## 基础知识

### 抽象 (Abstraction)
抽象是隐藏复杂细节，只展示必要信息的过程。

### 程序设计原则
- 模块化
- 封装
- 可重用性

## 代码示例

### 示例 1: 简单的类设计
```java
public class Student {
    private String name;
    private int age;
    
    public Student(String n, int a) {
        name = n;
        age = a;
    }
    
    public void introduce() {
        System.out.println("I'm " + name + ", " + age + " years old.");
    }
}
```

## 例题

### 例题 1: 选择题
隐藏复杂细节，只展示必要信息的概念称为？
A. 继承
B. 抽象
C. 多态
D. 封装

**答案: B**
