---
layout: default
title: 3.4 Constructors
parent: Unit 3
nav_order: 4
---

# 3.4 Constructors

## 基础知识

### 构造函数
构造函数用于初始化对象，与类名同名，没有返回类型：
```java
public ClassName() { }
```

### 构造函数重载
可以有多个构造函数，参数不同：
```java
public ClassName() { }
public ClassName(int x) { }
```

## 代码示例

### 示例 1: 构造函数
```java
public class Rectangle {
    private double length;
    private double width;
    
    // 无参构造函数
    public Rectangle() {
        length = 1.0;
        width = 1.0;
    }
    
    // 有参构造函数
    public Rectangle(double l, double w) {
        length = l;
        width = w;
    }
    
    public double getArea() {
        return length * width;
    }
}
```

### 示例 2: 使用构造函数
```java
public class RectangleTest {
    public static void main(String[] args) {
        Rectangle r1 = new Rectangle();
        Rectangle r2 = new Rectangle(5.0, 3.0);
        
        System.out.println("Area 1: " + r1.getArea());
        System.out.println("Area 2: " + r2.getArea());
    }
}
```

## 例题

### 例题 1: 选择题
构造函数的特点是？
A. 与类名同名
B. 有返回类型
C. 只能有一个
D. 必须是 private

**答案: A**

### 例题 2: 编程题
创建一个 Circle 类，包含 radius 属性和构造函数。

**参考答案:**
```java
public class Circle {
    private double radius;
    
    public Circle() {
        radius = 1.0;
    }
    
    public Circle(double r) {
        radius = r;
    }
    
    public double getArea() {
        return Math.PI * radius * radius;
    }
}
```
