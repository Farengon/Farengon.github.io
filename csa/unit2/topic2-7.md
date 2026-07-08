---
layout: default
title: 2.7 while Loops
parent: Unit 2
nav_order: 7
---

# 2.7 while Loops

## 基础知识

### while 循环
```java
while (condition) {
    // 条件为 true 时重复执行
}
```

## 代码示例

### 示例 1: 计数
```java
public class WhileLoop {
    public static void main(String[] args) {
        int count = 1;
        while (count <= 5) {
            System.out.println(count);
            count++;
        }
    }
}
```

### 示例 2: 求和
```java
public class SumWhile {
    public static void main(String[] args) {
        int sum = 0;
        int i = 1;
        
        while (i <= 10) {
            sum += i;
            i++;
        }
        
        System.out.println("Sum: " + sum);
    }
}
```

## 例题

### 例题 1: 编程题
使用 while 循环计算 1 到 100 的和。

**参考答案:**
```java
public class Sum100 {
    public static void main(String[] args) {
        int sum = 0;
        int i = 1;
        
        while (i <= 100) {
            sum += i;
            i++;
        }
        
        System.out.println("Sum: " + sum);
    }
}
```
