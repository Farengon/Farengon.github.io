---
layout: default
title: 2.9 Implementing Selection and Iteration Algorithms
parent: Unit 2: Selection and Iteration
nav_order: 9
---

# 2.9 Implementing Selection and Iteration Algorithms

## 基础知识

### 常见算法
- 求最大值/最小值
- 计数
- 求和

## 代码示例

### 示例 1: 求最大值
```java
public class FindMax {
    public static void main(String[] args) {
        int[] numbers = {5, 2, 8, 1, 9};
        int max = numbers[0];
        
        for (int i = 1; i < numbers.length; i++) {
            if (numbers[i] > max) {
                max = numbers[i];
            }
        }
        
        System.out.println("Max: " + max);
    }
}
```

## 例题

### 例题 1: 编程题
找出数组中的最小值。

**参考答案:**
```java
public class FindMin {
    public static void main(String[] args) {
        int[] numbers = {5, 2, 8, 1, 9};
        int min = numbers[0];
        
        for (int i = 1; i < numbers.length; i++) {
            if (numbers[i] < min) {
                min = numbers[i];
            }
        }
        
        System.out.println("Min: " + min);
    }
}
```
