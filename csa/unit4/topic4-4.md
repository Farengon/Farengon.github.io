---
layout: default
title: 4.4 Array Traversals
parent: Unit 4: Data Collections
nav_order: 4
---

# 4.4 Array Traversals

## 基础知识

### 遍历数组
```java
// 方式 1: for 循环
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

// 方式 2: 增强 for 循环
for (int num : arr) {
    System.out.println(num);
}
```

## 代码示例

### 示例 1: 遍历数组
```java
public class ArrayTraversal {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        
        // for 循环
        System.out.println("For loop:");
        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }
        
        // 增强 for 循环
        System.out.println("\nEnhanced for loop:");
        for (int num : numbers) {
            System.out.println(num);
        }
    }
}
```

## 例题

### 例题 1: 编程题
遍历数组并输出所有元素。

**参考答案:**
```java
public class PrintArray {
    public static void main(String[] args) {
        String[] fruits = {"Apple", "Banana", "Cherry"};
        
        for (int i = 0; i < fruits.length; i++) {
            System.out.println(fruits[i]);
        }
    }
}
```
