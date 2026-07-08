---
layout: default
title: 1.10 Calling Class Methods
parent: Unit 1: Using Objects and Methods
nav_order: 10
---

# 1.10 Calling Class Methods

## 基础知识

### 调用类方法
类方法（静态方法）使用类名调用：
```java
ClassName.methodName(arguments);
```

## 代码示例

### 示例 1: 调用 Math 类方法
```java
public class ClassMethods {
    public static void main(String[] args) {
        System.out.println("Absolute: " + Math.abs(-5));
        System.out.println("Square root: " + Math.sqrt(16));
    }
}
```

## 例题

### 例题 1: 选择题
调用类方法时使用什么？
A. 对象名
B. 类名
C. 直接调用
D. this 关键字

**答案: B**
