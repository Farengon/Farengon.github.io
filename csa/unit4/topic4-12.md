---
layout: default
title: 4.12 2D Array Traversals
parent: Unit 4
nav_order: 12
---

# 4.12 2D Array Traversals

## 基础知识

### 遍历 2D 数组
```java
// 行优先遍历
for (int row = 0; row < arr.length; row++) {
    for (int col = 0; col < arr[row].length; col++) {
        System.out.println(arr[row][col]);
    }
}
```

## 代码示例

### 示例 1: 遍历 2D 数组
{% raw %}
```java
public class TwoDTraversal {
    public static void main(String[] args) {
        int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
        
        System.out.println("Row-major:");
        for (int row = 0; row < matrix.length; row++) {
            for (int col = 0; col < matrix[row].length; col++) {
                System.out.print(matrix[row][col] + " ");
            }
            System.out.println();
        }
    }
}
```
{% endraw %}

## 例题

### 例题 1: 编程题
输出 2D 数组的所有元素。

**参考答案:**
{% raw %}
```java
public class Print2D {
    public static void main(String[] args) {
        String[][] names = {{"Alice", "Bob"}, {"Charlie", "David"}};
        
        for (int row = 0; row < names.length; row++) {
            for (int col = 0; col < names[row].length; col++) {
                System.out.println(names[row][col]);
            }
        }
    }
}
```
{% endraw %}
