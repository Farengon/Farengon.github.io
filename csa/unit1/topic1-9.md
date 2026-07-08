---
layout: default
title: 1.9 Method Signatures
parent: Unit 1: Using Objects and Methods
nav_order: 9
---

# 1.9 Method Signatures

## 基础知识

### 方法签名
方法签名包括方法名和参数列表：
```java
returnType methodName(parameterType1 param1, parameterType2 param2, ...)
```

### 组成部分
- **返回类型**: 方法返回的数据类型（`void` 表示不返回）
- **方法名**: 方法的名称
- **参数列表**: 参数类型和名称

## 代码示例

### 示例 1: 方法签名示例
```java
public class MethodSignatures {
    public static void main(String[] args) {
        // void 方法，无参数
        System.out.println("Hello");
        
        // void 方法，有参数
        System.out.println(5);
    }
}
```

## 例题

### 例题 1: 选择题
方法签名包含哪些部分？
A. 方法名和返回类型
B. 方法名和参数列表
C. 返回类型和参数列表
D. 方法名、返回类型和参数列表

**答案: B**
