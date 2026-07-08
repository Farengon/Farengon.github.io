---
layout: default
title: 4.10 Implementing ArrayList Algorithms
parent: Unit 4
nav_order: 10
---

# 4.10 Implementing ArrayList Algorithms

## 基础知识

### ArrayList 算法
与数组类似，但使用方法而不是索引直接访问。

## 代码示例

### 示例 1: 求和
```java
import java.util.ArrayList;

public class ArrayListSum {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<Integer>();
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);
        numbers.add(4);
        numbers.add(5);
        
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        
        System.out.println("Sum: " + sum);
    }
}
```

### 示例 2: 删除元素（注意：反向遍历）
```java
import java.util.ArrayList;

public class RemoveElements {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<Integer>();
        numbers.add(1);
        numbers.add(2);
        numbers.add(3);
        numbers.add(4);
        
        // 删除偶数 - 反向遍历避免问题
        for (int i = numbers.size() - 1; i >= 0; i--) {
            if (numbers.get(i) % 2 == 0) {
                numbers.remove(i);
            }
        }
        
        System.out.println(numbers);  // [1, 3]
    }
}
```

## 例题

### 例题 1: 编程题
找出 ArrayList 中的最大值。

**参考答案:**
```java
import java.util.ArrayList;

public class ArrayListMax {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<Integer>();
        numbers.add(5);
        numbers.add(2);
        numbers.add(8);
        numbers.add(1);
        numbers.add(9);
        
        int max = numbers.get(0);
        for (int num : numbers) {
            if (num > max) {
                max = num;
            }
        }
        
        System.out.println("Max: " + max);
    }
}
```
