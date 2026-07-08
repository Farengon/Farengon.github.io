---
layout: default
title: 4.14 Searching Algorithms
parent: Unit 4
nav_order: 14
---

# 4.14 Searching Algorithms

## 基础知识

### 线性搜索
逐个检查元素，适用于任何数组：
```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;  // 没找到
}
```

### 二分搜索
要求数组已排序，效率更高：
```java
public static int binarySearch(int[] arr, int target) {
    int low = 0;
    int high = arr.length - 1;
    
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return -1;
}
```

## 代码示例

### 示例 1: 线性搜索
```java
public class LinearSearch {
    public static int search(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        return -1;
    }
    
    public static void main(String[] args) {
        int[] numbers = {5, 2, 8, 1, 9};
        int index = search(numbers, 8);
        System.out.println("Found at index: " + index);  // 2
    }
}
```

## 例题

### 例题 1: 选择题
线性搜索的时间复杂度是？
A. O(1)
B. O(n)
C. O(n²)
D. O(log n)

**答案: B**

### 例题 2: 选择题
二分搜索要求数组？
A. 为空
B. 已排序
C. 全是正数
D. 大小固定

**答案: B**
