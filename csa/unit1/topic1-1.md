---
layout: default
title: 1.1 Introduction to Algorithms, Programming, and Compilers
parent: Unit 1
nav_order: 1
---

# 1.1 Introduction to Algorithms, Programming, and Compilers

## 基础知识

### 什么是算法？
算法是一组按顺序执行的指令，用于解决问题或完成任务。

### 什么是编程？
编程是使用编程语言创建计算机程序的过程。

### 编译过程
Java 程序需要先被编译成字节码，然后由 Java 虚拟机 (JVM) 执行。

```
源代码 (.java) → 编译器 → 字节码 (.class) → JVM → 运行
```

### 第一个程序
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

## 代码示例

### 示例 1: 输出多条信息
```java
public class Greetings {
    public static void main(String[] args) {
        System.out.println("Welcome to AP CSA!");
        System.out.println("Let's learn Java together.");
        System.out.println("Computers are fun!");
    }
}
```

## 例题

### 例题 1: 选择题
Java 程序的入口点是以下哪个方法？
A. `public static void main()`
B. `public void main(String[] args)`
C. `public static void main(String[] args)`
D. `static void main(String[] args)`

**答案: C**

### 例题 2: 编程题
编写一个程序，输出你的名字和最喜欢的科目。

**参考答案:**
```java
public class AboutMe {
    public static void main(String[] args) {
        System.out.println("Name: Alice");
        System.out.println("Favorite Subject: Computer Science");
    }
}
```
