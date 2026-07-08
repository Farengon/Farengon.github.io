---
layout: default
title: 4.11 2D Array Creation and Access
parent: Unit 4: Data Collections
nav_order: 11
---

# 4.11 2D Array Creation and Access

## 基础知识

### 创建 2D 数组
```java
// 方式 1: 初始化
int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};

// 方式 2: 指定大小
int[][] arr = new int[3][4];  // 3 行 4 列
```

### 访问元素
```java
arr[row][col]
```

## 代码示例

### 示例 1: 2D 数组
```java
public class TwoDArray {
    public static void main(String[] args) {
        int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        
        System.out.println(matrix[0][0]);  // 1
        System.out.println(matrix[1][2]);  // 6
        System.out.println(matrix.length);  // 3 (行数)
        System.out.println(matrix[0].length);  // 3 (第一行的列数)
    }
}
```

## 例题

### 例题 1: 选择题
`int[][] arr = new int[5][3];` 有多少行？
A. 5
B. 3
C. 15
D. 8

**答案: A**
