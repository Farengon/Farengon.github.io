---
layout: default
title: "3.5 Methods: How to Write Them"
parent: Unit 3
nav_order: 5
---

# 3.5 Methods: How to Write Them

## 基础知识

### 方法结构
```java
public returnType methodName(parameterType param) {
    // 方法体
    return value;  // 如果返回类型不是 void
}
```

## 代码示例

### 示例 1: 各种方法
```java
public class BankAccount {
    private double balance;
    
    public BankAccount(double initial) {
        balance = initial;
    }
    
    // void 方法
    public void deposit(double amount) {
        balance += amount;
    }
    
    // 返回值的方法
    public double getBalance() {
        return balance;
    }
    
    // 带参数的方法
    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        }
    }
}
```

## 例题

### 例题 1: 编程题
创建一个类，包含一个计算两个数之和的方法。

**参考答案:**
```java
public class Adder {
    public int add(int a, int b) {
        return a + b;
    }
}
```
