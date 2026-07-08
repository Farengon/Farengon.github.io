---
layout: default
title: 1.14 Calling Instance Methods
parent: Unit 1: Using Objects and Methods
nav_order: 14
---

# 1.14 Calling Instance Methods

## 基础知识

### 调用实例方法
实例方法使用对象名调用：
```java
objectName.methodName(arguments);
```

## 代码示例

### 示例 1: 调用 String 实例方法
```java
public class InstanceMethods {
    public static void main(String[] args) {
        String s = "Hello World";
        
        System.out.println("Length: " + s.length());
        System.out.println("Uppercase: " + s.toUpperCase());
        System.out.println("Lowercase: " + s.toLowerCase());
    }
}
```

## 例题

### 例题 1: 选择题
调用实例方法时使用什么？
A. 对象名
B. 类名
C. 直接调用
D. 不需要任何前缀

**答案: A**
