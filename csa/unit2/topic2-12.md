---
layout: default
title: 2.12 Informal Run-Time Analysis
parent: Unit 2
nav_order: 12
---

# 2.12 Informal Run-Time Analysis

## 基础知识

### 时间复杂度
- O(1): 常数时间
- O(n): 线性时间
- O(n²): 平方时间

## 代码示例

### 示例 1: 分析循环
```java
// O(n) - 执行 n 次
for (int i = 0; i < n; i++) {
    System.out.println(i);
}

// O(n²) - 执行 n*n 次
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        System.out.println(i + j);
    }
}
```

## 例题

### 例题 1: 选择题
一个循环执行 n 次的时间复杂度是？
A. O(1)
B. O(n)
C. O(n²)
D. O(log n)

**答案: B**
