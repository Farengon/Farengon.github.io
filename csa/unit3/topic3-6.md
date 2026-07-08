---
layout: default
title: 3.6 Methods: Passing and Returning References of an Object
parent: Unit 3: Class Creation
nav_order: 6
---

# 3.6 Methods: Passing and Returning References of an Object

## 基础知识

### 对象引用
对象变量存储的是引用（地址），不是实际对象。

## 代码示例

### 示例 1: 传递对象
```java
public class Person {
    private String name;
    
    public Person(String n) {
        name = n;
    }
    
    public String getName() {
        return name;
    }
}

public class PersonDemo {
    public static void printName(Person p) {
        System.out.println(p.getName());
    }
    
    public static void main(String[] args) {
        Person alice = new Person("Alice");
        printName(alice);
    }
}
```

## 例题

### 例题 1: 选择题
对象变量存储的是？
A. 对象的副本
B. 对象的引用
C. 对象的值
D. 对象的类型

**答案: B**
