---
layout: default
title: 4.13 Implementing 2D Array Algorithms
parent: Unit 4
nav_order: 13
---

# 4.13 Implementing 2D Array Algorithms

## 基础知识

### 常见 2D 数组算法
- 求所有元素和
- 求每行/每列的和
- 查找元素

## 代码示例

### 示例 1: 求和
{% raw %}
```java
public class TwoDSum {
    public static void main(String[] args) {
        int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        int sum = 0;
        
        for (int row = 0; row < matrix.length; row++) {
            for (int col = 0; col < matrix[row].length; col++) {
                sum += matrix[row][col];
            }
        }
        
        System.out.println("Sum: " + sum);
    }
}
```
{% endraw %}

### 示例 2: 求每行的和
{% raw %}
```java
public class RowSums {
    public static void main(String[] args) {
        int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        
        for (int row = 0; row < matrix.length; row++) {
            int rowSum = 0;
            for (int col = 0; col < matrix[row].length; col++) {
                rowSum += matrix[row][col];
            }
            System.out.println("Row " + row + " sum: " + rowSum);
        }
    }
}
```
{% endraw %}

## 例题

### 例题 1: 编程题
求 2D 数组中所有元素的最大值。

**参考答案:**
{% raw %}
```java
public class TwoDMax {
    public static void main(String[] args) {
        int[][] matrix = {{1, 5, 3}, {4, 2, 6}, {9, 8, 7}};
        int max = matrix[0][0];
        
        for (int row = 0; row < matrix.length; row++) {
            for (int col = 0; col < matrix[row].length; col++) {
                if (matrix[row][col] > max) {
                    max = matrix[row][col];
                }
            }
        }
        
        System.out.println("Max: " + max);
    }
}
```
{% endraw %}
