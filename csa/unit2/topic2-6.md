---
layout: default
title: 2.6 Comparing Boolean Expressions
parent: Unit 2: Selection and Iteration
nav_order: 6
---

# 2.6 Comparing Boolean Expressions

## 基础知识

### 比较对象
使用 `.equals()` 比较对象内容：
```java
String s1 = "Hello";
String s2 = "Hello";
System.out.println(s1.equals(s2));  // true
```

### 比较基本类型
使用 `==` 比较基本类型：
```java
int x = 5;
int y = 5;
System.out.println(x == y);  // true
```

## 代码示例

### 示例 1: 字符串比较
```java
public class StringCompare {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = "Hello";
        String s3 = new String("Hello");
        
        System.out.println(s1.equals(s2));  // true
        System.out.println(s1.equals(s3));  // true
    }
}
```

## 例题

### 例题 1: 选择题
比较两个 String 对象的内容应该使用？
A. `==`
B. `.equals()`
C. `=`
D. `!=`

**答案: B**
