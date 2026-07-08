---
layout: default
title: 1.8 Documentation with Comments
parent: Unit 1
nav_order: 8
---

# 1.8 Documentation with Comments

## 基础知识

### 注释类型
Java 支持三种注释：

1. **单行注释**
```java
// 这是单行注释
```

2. **多行注释**
```java
/* 这是
多行
注释 */
```

3. **Javadoc 注释**
```java
/**
 * 这是 Javadoc 注释
 * 用于生成 API 文档
 */
```

## 代码示例

### 示例 1: 带注释的代码
```java
public class CommentDemo {
    public static void main(String[] args) {
        // 声明并初始化变量
        int age = 16;  // 存储年龄
        
        /* 计算出生年份
           假设当前是 2024 年 */
        int birthYear = 2024 - age;
        
        System.out.println("Birth Year: " + birthYear);
    }
}
```

## 例题

### 例题 1: 选择题
以下哪个是多行注释的正确语法？
A. `// 注释 //`
B. `/* 注释 */`
C. `# 注释 #`
D. `/* 注释`

**答案: B**

### 例题 2: 编程题
写一个计算矩形面积的程序，添加适当的注释解释代码。

**参考答案:**
```java
public class RectangleArea {
    public static void main(String[] args) {
        // 定义矩形的长和宽
        double length = 5.0;
        double width = 3.0;
        
        // 计算面积
        double area = length * width;
        
        // 输出结果
        System.out.println("Area: " + area);
    }
}
```
