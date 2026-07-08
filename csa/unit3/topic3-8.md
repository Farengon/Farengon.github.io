---
layout: default
title: 3.8 Scope and Access
parent: Unit 3: Class Creation
nav_order: 8
---

# 3.8 Scope and Access

## 基础知识

### 访问修饰符
| 修饰符 | 访问范围 |
|--------|----------|
| `public` | 任何地方 |
| `private` | 同一类内 |

### 变量作用域
- 实例变量：整个类内
- 局部变量：方法内

## 代码示例

### 示例 1: 访问控制
```java
public class Person {
    private String name;      // private - 只能在类内访问
    public int age;           // public - 任何地方都能访问
    
    public Person(String n, int a) {
        name = n;
        age = a;
    }
    
    public String getName() {  // public - 提供访问 private 变量的方法
        return name;
    }
}
```

## 例题

### 例题 1: 选择题
哪个修饰符使成员只能在类内访问？
A. public
B. private
C. static
D. void

**答案: B**
