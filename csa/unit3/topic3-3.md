---
layout: default
title: 3.3 Anatomy of a Class
parent: Unit 3
nav_order: 3
---

# 3.3 Anatomy of a Class

## 基础知识

### 类的组成
```java
public class ClassName {
    // 实例变量（属性）
    private type variableName;
    
    // 构造函数
    public ClassName() { }
    
    // 方法
    public returnType methodName() { }
}
```

## 代码示例

### 示例 1: 完整的类
```java
public class Person {
    // 实例变量
    private String name;
    private int age;
    
    // 构造函数
    public Person(String n, int a) {
        name = n;
        age = a;
    }
    
    // 方法
    public String getName() { return name; }
    public int getAge() { return age; }
    public void birthday() { age++; }
}
```

## 例题

### 例题 1: 选择题
类的属性通常存储在？
A. 构造函数
B. 实例变量
C. 方法
D. 主函数

**答案: B**
