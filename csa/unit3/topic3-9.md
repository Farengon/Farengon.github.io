---
layout: default
title: 3.9 this Keyword
parent: Unit 3: Class Creation
nav_order: 9
---

# 3.9 this Keyword

## 基础知识

### this 关键字
`this` 引用当前对象：
```java
this.variableName  // 访问当前对象的实例变量
this.methodName()  // 调用当前对象的方法
```

## 代码示例

### 示例 1: 使用 this
```java
public class Person {
    private String name;
    private int age;
    
    public Person(String name, int age) {
        this.name = name;      // this.name 是实例变量，name 是参数
        this.age = age;
    }
    
    public void introduce() {
        System.out.println("I'm " + this.name);
    }
}
```

## 例题

### 例题 1: 选择题
this 关键字引用的是？
A. 类
B. 当前对象
C. 父类
D. 静态变量

**答案: B**
