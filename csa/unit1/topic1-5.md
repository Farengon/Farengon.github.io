---
layout: default
title: 1.5 Casting and Range of Variables
parent: Unit 1
nav_order: 5
---

# 1.5 Casting and Range of Variables

## 基础知识

### 类型转换
Java 中有两种类型转换：
1. **自动类型转换**（从小到大）
2. **强制类型转换**（从大到小，需要显式声明）

### 自动类型转换
```
byte → short → int → long → float → double
```

### 强制类型转换
```java
double d = 3.14;
int i = (int) d;  // i = 3 (截断小数部分)
```

## 代码示例

### 示例 1: 自动类型转换
```java
public class AutoCasting {
    public static void main(String[] args) {
        int x = 10;
        double y = x;  // int 自动转为 double
        
        System.out.println("x: " + x);    // 10
        System.out.println("y: " + y);    // 10.0
    }
}
```

### 示例 2: 强制类型转换
```java
public class ExplicitCasting {
    public static void main(String[] args) {
        double pi = 3.14159;
        int approxPi = (int) pi;
        
        System.out.println("Pi: " + pi);
        System.out.println("Approx Pi: " + approxPi);
    }
}
```

### 示例 3: 四舍五入技巧
```java
public class Round {
    public static void main(String[] args) {
        double num = 3.6;
        int rounded = (int) (num + 0.5);  // 四舍五入
        
        System.out.println("Original: " + num);
        System.out.println("Rounded: " + rounded);
    }
}
```

## 例题

### 例题 1: 选择题
`(int) 4.99` 的结果是？
A. 4
B. 5
C. 4.0
D. 编译错误

**答案: A**

### 例题 2: 编程题
一个学生的分数是 89.7，使用强制类型转换和 +0.5 的方法将其四舍五入到整数。

**参考答案:**
```java
public class GradeRounding {
    public static void main(String[] args) {
        double score = 89.7;
        int roundedScore = (int) (score + 0.5);
        
        System.out.println("Original: " + score);
        System.out.println("Rounded: " + roundedScore);
    }
}
```
