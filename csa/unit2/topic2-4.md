---
layout: default
title: 2.4 Nested if Statements
parent: Unit 2: Selection and Iteration
nav_order: 4
---

# 2.4 Nested if Statements

## 基础知识

### 嵌套 if 语句
if 语句中可以包含另一个 if 语句：
```java
if (condition1) {
    if (condition2) {
        // 两个条件都满足时执行
    }
}
```

## 代码示例

### 示例 1: 嵌套 if
```java
public class NestedIf {
    public static void main(String[] args) {
        int age = 18;
        boolean hasLicense = true;
        
        if (age >= 18) {
            if (hasLicense) {
                System.out.println("Can drive");
            } else {
                System.out.println("Need a license");
            }
        } else {
            System.out.println("Too young");
        }
    }
}
```

## 例题

### 例题 1: 编程题
判断一个年份是否是闰年。闰年规则：能被 4 整除但不能被 100 整除，或者能被 400 整除。

**参考答案:**
```java
public class LeapYear {
    public static void main(String[] args) {
        int year = 2024;
        
        if (year % 4 == 0) {
            if (year % 100 == 0) {
                if (year % 400 == 0) {
                    System.out.println("Leap year");
                } else {
                    System.out.println("Not a leap year");
                }
            } else {
                System.out.println("Leap year");
            }
        } else {
            System.out.println("Not a leap year");
        }
    }
}
```
