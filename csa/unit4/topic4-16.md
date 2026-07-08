---
layout: default
title: 4.16 Recursion
parent: Unit 4: Data Collections
nav_order: 16
---

# 4.16 Recursion

## 基础知识

### 递归
方法调用自己，需要：
- 基准情形 (base case): 停止递归
- 递归情形: 向基准情形推进

## 代码示例

### 示例 1: 阶乘
```java
public class Factorial {
    public static int factorial(int n) {
        if (n <= 1) {  // 基准情形
            return 1;
        }
        return n * factorial(n - 1);  // 递归情形
    }
    
    public static void main(String[] args) {
        System.out.println(factorial(5));  // 120
    }
}
```

### 示例 2: 斐波那契
```java
public class Fibonacci {
    public static int fib(int n) {
        if (n <= 1) {  // 基准情形
            return n;
        }
        return fib(n - 1) + fib(n - 2);  // 递归情形
    }
    
    public static void main(String[] args) {
        System.out.println(fib(7));  // 13
    }
}
```

## 例题

### 例题 1: 选择题
递归方法必须有？
A. 循环
B. 基准情形
C. 返回值
D. 参数

**答案: B**

### 例题 2: 编程题
写一个递归方法计算 1 到 n 的和。

**参考答案:**
```java
public class SumRecursive {
    public static int sum(int n) {
        if (n <= 1) {
            return n;
        }
        return n + sum(n - 1);
    }
    
    public static void main(String[] args) {
        System.out.println(sum(5));  // 15
    }
}
```
