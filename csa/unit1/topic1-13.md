---
layout: default
title: 1.13 Object Creation and Storage (Instantiation)
parent: Unit 1: Using Objects and Methods
nav_order: 13
---

# 1.13 Object Creation and Storage (Instantiation)

## 基础知识

### 创建对象
使用 `new` 关键字创建对象：
```java
ClassName objectName = new ClassName();
```

### String 的特殊写法
```java
// 方式 1: 使用 new
String s1 = new String("Hello");

// 方式 2: 字符串字面量（推荐）
String s2 = "Hello";
```

### null 引用
```java
String s = null;  // s 不引用任何对象
```

## 代码示例

### 示例 1: 创建对象
```java
public class ObjectCreation {
    public static void main(String[] args) {
        String s1 = new String("Hello");
        String s2 = "Hello";
        
        System.out.println(s1);
        System.out.println(s2);
    }
}
```

## 例题

### 例题 1: 选择题
以下哪行代码正确创建了 String 对象？
A. `String s = "Hello";`
B. `String s = new "Hello";`
C. `String s = String("Hello");`
D. `s = "Hello";`

**答案: A**
