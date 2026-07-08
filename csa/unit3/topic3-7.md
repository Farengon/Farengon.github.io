---
layout: default
title: 3.7 Class Variables and Methods
parent: Unit 3: Class Creation
nav_order: 7
---

# 3.7 Class Variables and Methods

## 基础知识

### 静态变量 (Class Variables)
使用 `static` 关键字，所有实例共享：
```java
private static int count = 0;
```

### 静态方法 (Class Methods)
使用 `static` 关键字，属于类而不是实例：
```java
public static void method() { }
```

## 代码示例

### 示例 1: 静态变量和方法
```java
public class Counter {
    private static int count = 0;
    
    public Counter() {
        count++;
    }
    
    public static int getCount() {
        return count;
    }
}

public class CounterDemo {
    public static void main(String[] args) {
        Counter c1 = new Counter();
        Counter c2 = new Counter();
        Counter c3 = new Counter();
        
        System.out.println("Count: " + Counter.getCount());  // 3
    }
}
```

## 例题

### 例题 1: 选择题
静态变量属于？
A. 每个实例
B. 类
C. 方法
D. 构造函数

**答案: B**
