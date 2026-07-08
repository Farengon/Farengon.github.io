---
layout: default
title: 4.15 Sorting Algorithms
parent: Unit 4: Data Collections
nav_order: 15
---

# 4.15 Sorting Algorithms

## 基础知识

### 选择排序
每次找最小值，放到正确位置：
```java
public static void selectionSort(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
}
```

### 插入排序
将元素插入到已排序部分：
```java
public static void insertionSort(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

## 代码示例

### 示例 1: 选择排序
```java
public class SelectionSort {
    public static void sort(int[] arr) {
        for (int i = 0; i < arr.length - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                }
            }
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
    
    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        sort(arr);
        
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

## 例题

### 例题 1: 选择题
选择排序和插入排序的时间复杂度是？
A. O(1)
B. O(n)
C. O(n²)
D. O(log n)

**答案: C**
