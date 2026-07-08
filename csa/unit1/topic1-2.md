---
layout: default
title: 1.2 Variables and Data Types
parent: Unit 1: Using Objects and Methods
nav_order: 2
---

# 1.2 Variables and Data Types

## 基础知识

### 变量声明
在 Java 中，使用变量前必须先声明类型和名称：
```java
type variableName;
variableName = value;
```

或者同时声明和初始化：
```java
type variableName = value;
```

### 基本数据类型
| 类型 | 描述 | 范围 |
|------|------|------|
| `int` | 整数 | -2,147,483,648 到 2,147,483,647 |
| `double` | 双精度浮点数 | ±4.9e-324 到 ±1.7e+308 |
| `boolean` | 布尔值 | `true` 或 `false` |

## 代码示例

### 示例 1: 变量声明和使用
```java
public class Variables {
    public static void main(String[] args) {
        int age = 16;
        double gpa = 3.8;
        boolean isStudent = true;
        
        System.out.println("Age: " + age);
        System.out.println("GPA: " + gpa);
        System.out.println("Is Student: " + isStudent);
    }
}
```

### 示例 2: 变量命名规则
```java
// 正确的命名
int myAge;
double _price;
boolean $isValid;
String studentName;

// 错误的命名
// int 123abc;    // 不能以数字开头
// int class;     // class 是关键字
```

## 例题

### 例题 1: 选择题
以下哪个变量声明是正确的？
A. `int 123number;`
B. `double price$;`
C. `boolean True;`
D. `String class;`

**答案: B**

### 例题 2: 编程题
声明三个变量表示考试分数（整数），计算总分和平均分，输出结果。

**参考答案:**
```java
public class Scores {
    public static void main(String[] args) {
        int score1 = 85;
        int score2 = 90;
        int score3 = 88;
        
        int total = score1 + score2 + score3;
        double average = total / 3.0;
        
        System.out.println("Total: " + total);
        System.out.println("Average: " + average);
    }
}
```
