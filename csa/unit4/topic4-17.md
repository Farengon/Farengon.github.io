---
layout: default
title: 4.17 Recursive Searching and Sorting
parent: Unit 4: Data Collections
nav_order: 17
---

# 4.17 Recursive Searching and Sorting

## 基础知识

### 递归二分搜索
```java
public static int binarySearch(int[] arr, int target, int low, int high) {
    if (low > high) {
        return -1;
    }
    int mid = (low + high) / 2;
    if (arr[mid] == target) {
        return mid;
    } else if (arr[mid] < target) {
        return binarySearch(arr, target, mid + 1, high);
    } else {
        return binarySearch(arr, target, low, mid - 1);
    }
}
```

### 归并排序 (概念)
归并排序是分治算法，但 AP CSA 不要求实现。

## 代码示例

### 示例 1: 递归二分搜索
```java
public class RecursiveBinarySearch {
    public static int search(int[] arr, int target, int low, int high) {
        if (low > high) {
            return -1;
        }
        int mid = (low + high) / 2;
        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            return search(arr, target, mid + 1, high);
        } else {
            return search(arr, target, low, mid - 1);
        }
    }
    
    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11};
        int index = search(arr, 7, 0, arr.length - 1);
        System.out.println("Found at index: " + index);  // 3
    }
}
```

## 例题

### 例题 1: 选择题
二分搜索的时间复杂度是？
A. O(1)
B. O(n)
C. O(n²)
D. O(log n)

**答案: D**
