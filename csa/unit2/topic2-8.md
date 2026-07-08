---
layout: default
title: 2.8 for Loops
parent: Unit 2: Selection and Iteration
nav_order: 8
---

# 2.8 for Loops

## 基础知识

### for 循环
```java
for (初始化; 条件; 更新) {
    // 循环体
}
```

## 代码示例

### 示例 1: 计数
```java
public class ForLoop {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }
    }
}
```

### 示例 2: 求和
```java
public class SumFor {
    public static void main(String[] args) {
        int sum = 0;
        
        for (int i = 1; i <= 10; i++) {
            sum += i;
        }
        
        System.out.println("Sum: " + sum);
    }
}
```

## 例题

### 例题 1: 编程题
使用 for 循环输出 1 到 10 的偶数。

**参考答案:**
```java
public class EvenNumbers {
    public static void main(String[] args) {
        for (int i = 2; i <= 10; i += 2) {
            System.out.println(i);
        }
    }
}
```
