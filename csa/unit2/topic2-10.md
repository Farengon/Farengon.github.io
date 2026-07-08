---
layout: default
title: 2.10 Implementing String Algorithms
parent: Unit 2: Selection and Iteration
nav_order: 10
---

# 2.10 Implementing String Algorithms

## 基础知识

### 遍历字符串
```java
String s = "Hello";
for (int i = 0; i < s.length(); i++) {
    char c = s.charAt(i);
    System.out.println(c);
}
```

## 代码示例

### 示例 1: 统计字符
```java
public class CountChars {
    public static void main(String[] args) {
        String s = "Hello World";
        int count = 0;
        
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == 'l') {
                count++;
            }
        }
        
        System.out.println("Number of 'l's: " + count);
    }
}
```

## 例题

### 例题 1: 编程题
统计字符串中有多少个大写字母。

**参考答案:**
```java
public class CountUppercase {
    public static void main(String[] args) {
        String s = "Hello World!";
        int count = 0;
        
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c >= 'A' && c <= 'Z') {
                count++;
            }
        }
        
        System.out.println("Uppercase count: " + count);
    }
}
```
