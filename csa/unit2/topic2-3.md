---
layout: default
title: 2.3 if Statements
parent: Unit 2
nav_order: 3
---

# 2.3 if Statements

## 基础知识

### if 语句
```java
if (condition) {
    // 条件为 true 时执行
}
```

### if-else 语句
```java
if (condition) {
    // 条件为 true 时执行
} else {
    // 条件为 false 时执行
}
```

### if-else if 语句
```java
if (condition1) {
    // 条件 1 为 true 时执行
} else if (condition2) {
    // 条件 2 为 true 时执行
} else {
    // 以上都不满足时执行
}
```

## 代码示例

### 示例 1: if-else
```java
public class IfElseDemo {
    public static void main(String[] args) {
        int score = 85;
        
        if (score >= 90) {
            System.out.println("A");
        } else if (score >= 80) {
            System.out.println("B");
        } else if (score >= 70) {
            System.out.println("C");
        } else if (score >= 60) {
            System.out.println("D");
        } else {
            System.out.println("F");
        }
    }
}
```

## 例题

### 例题 1: 编程题
编写一个程序，判断一个数是正数、负数还是零。

**参考答案:**
```java
public class NumberCheck {
    public static void main(String[] args) {
        int num = 42;
        
        if (num > 0) {
            System.out.println("Positive");
        } else if (num < 0) {
            System.out.println("Negative");
        } else {
            System.out.println("Zero");
        }
    }
}
```
