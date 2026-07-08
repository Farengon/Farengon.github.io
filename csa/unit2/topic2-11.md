---
layout: default
title: 2.11 Nested Iteration
parent: Unit 2: Selection and Iteration
nav_order: 11
---

# 2.11 Nested Iteration

## 基础知识

### 嵌套循环
循环中可以包含另一个循环：
```java
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        System.out.println(i + " " + j);
    }
}
```

## 代码示例

### 示例 1: 乘法表
```java
public class MultiplicationTable {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= 5; j++) {
                System.out.print(i * j + "\t");
            }
            System.out.println();
        }
    }
}
```

## 例题

### 例题 1: 编程题
使用嵌套循环输出以下图案：
```
*
**
***
****
*****
```

**参考答案:**
```java
public class Triangle {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```
