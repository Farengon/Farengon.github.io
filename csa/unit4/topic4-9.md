---
layout: default
title: 4.9 ArrayList Traversals
parent: Unit 4
nav_order: 9
---

# 4.9 ArrayList Traversals

## 基础知识

### 遍历 ArrayList
```java
// 方式 1: for 循环
for (int i = 0; i < list.size(); i++) {
    System.out.println(list.get(i));
}

// 方式 2: 增强 for 循环
for (String s : list) {
    System.out.println(s);
}
```

## 代码示例

### 示例 1: 遍历 ArrayList
```java
import java.util.ArrayList;

public class ArrayListTraversal {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<Integer>();
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);
        
        System.out.println("For loop:");
        for (int i = 0; i < numbers.size(); i++) {
            System.out.println(numbers.get(i));
        }
        
        System.out.println("\nEnhanced for loop:");
        for (int num : numbers) {
            System.out.println(num);
        }
    }
}
```

## 例题

### 例题 1: 编程题
创建一个 ArrayList，添加几个元素，然后遍历输出。

**参考答案:**
```java
import java.util.ArrayList;

public class PrintList {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<String>();
        colors.add("Red");
        colors.add("Green");
        colors.add("Blue");
        
        for (String color : colors) {
            System.out.println(color);
        }
    }
}
```
