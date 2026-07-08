---
layout: default
title: 4.3 Array Creation and Access
parent: Unit 4
nav_order: 3
---

# 4.3 Array Creation and Access

## 基础知识

### 创建数组
```java
// 方式 1: 声明并初始化
int[] arr1 = {1, 2, 3, 4, 5};

// 方式 2: 声明大小，后赋值
int[] arr2 = new int[5];
arr2[0] = 1;
arr2[1] = 2;
```

### 访问元素
```java
arr[index]  // 索引从 0 开始
```

## 代码示例

### 示例 1: 数组创建和访问
```java
public class ArrayDemo {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        
        System.out.println(numbers[0]);  // 10
        System.out.println(numbers[2]);  // 30
        System.out.println(numbers.length);  // 5
    }
}
```

## 例题

### 例题 1: 选择题
数组的第一个元素索引是？
A. 1
B. 0
C. -1
D. length

**答案: B**

### 例题 2: 编程题
创建一个包含 5 个学生成绩的数组，输出第一个和最后一个元素。

**参考答案:**
```java
public class Scores {
    public static void main(String[] args) {
        int[] scores = {85, 92, 78, 90, 88};
        
        System.out.println("First: " + scores[0]);
        System.out.println("Last: " + scores[scores.length - 1]);
    }
}
```
