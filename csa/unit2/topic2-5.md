---
layout: default
title: 2.5 Compound Boolean Expressions
parent: Unit 2: Selection and Iteration
nav_order: 5
---

# 2.5 Compound Boolean Expressions

## 基础知识

### && (AND)
两个条件都为 true 时，结果为 true

### || (OR)
至少一个条件为 true 时，结果为 true

### ! (NOT)
取反

## 代码示例

### 示例 1: 复合布尔表达式
```java
public class CompoundBoolean {
    public static void main(String[] args) {
        int age = 25;
        double money = 100.0;
        
        // AND
        if (age >= 18 && money >= 50) {
            System.out.println("Can buy ticket");
        }
        
        // OR
        if (age < 12 || age >= 65) {
            System.out.println("Discount applies");
        }
    }
}
```

## 例题

### 例题 1: 选择题
`(3 < 5) && (2 > 4)` 的结果是？
A. true
B. false
C. 3
D. 5

**答案: B**
