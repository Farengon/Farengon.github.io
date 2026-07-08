---
layout: default
title: 1.4 Assignment Statements and Input
parent: Unit 1: Using Objects and Methods
nav_order: 4
---

# 1.4 Assignment Statements and Input

## 基础知识

### 赋值语句
赋值语句将值存储到变量中：
```java
variable = expression;
```

## 代码示例

### 示例 1: 多次赋值
```java
public class Assignment {
    public static void main(String[] args) {
        int x = 5;
        System.out.println("x = " + x);  // 5
        
        x = 10;
        System.out.println("x = " + x);  // 10
        
        x = x + 5;
        System.out.println("x = " + x);  // 15
    }
}
```

### 示例 2: 交换两个变量
```java
public class Swap {
    public static void main(String[] args) {
        int a = 5;
        int b = 10;
        
        System.out.println("Before: a = " + a + ", b = " + b);
        
        int temp = a;
        a = b;
        b = temp;
        
        System.out.println("After: a = " + a + ", b = " + b);
    }
}
```

## 例题

### 例题 1: 选择题
执行以下代码后，`y` 的值是？
```java
int x = 3;
int y = x * 2;
x = 5;
```
A. 3
B. 6
C. 10
D. 5

**答案: B**

### 例题 2: 编程题
声明三个变量 a, b, c，分别赋值 1, 2, 3。然后交换它们的值，使 a=2, b=3, c=1。

**参考答案:**
```java
public class Rotate {
    public static void main(String[] args) {
        int a = 1;
        int b = 2;
        int c = 3;
        
        int temp = a;
        a = b;
        b = c;
        c = temp;
        
        System.out.println("a = " + a);
        System.out.println("b = " + b);
        System.out.println("c = " + c);
    }
}
```
