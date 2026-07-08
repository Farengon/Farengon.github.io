---
layout: default
title: 4.5 Implementing Array Algorithms
parent: Unit 4: Data Collections
nav_order: 5
---

# 4.5 Implementing Array Algorithms

## 基础知识

### 常见数组算法
- 求和
- 求平均值
- 找最大/最小值
- 查找元素

## 代码示例

### 示例 1: 求和
```java
public class ArraySum {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        int sum = 0;
        
        for (int num : numbers) {
            sum += num;
        }
        
        System.out.println("Sum: " + sum);
    }
}
```

### 示例 2: 找最大值
```java
public class ArrayMax {
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
计算数组中所有元素的平均值。

**参考答案:**
```java
public class ArrayAverage {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        int sum = 0;
        
        for (int num : numbers) {
            sum += num;
        }
        
        double average = (double) sum / numbers.length;
        System.out.println("Average: " + average);
    }
}
```
