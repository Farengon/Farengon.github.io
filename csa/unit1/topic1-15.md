---
layout: default
title: 1.15 String Manipulation
parent: Unit 1: Using Objects and Methods
nav_order: 15
---

# 1.15 String Manipulation

## 基础知识

### 常用 String 方法
| 方法 | 描述 | 示例 |
|------|------|------|
| `length()` | 返回长度 | `"Hello".length()` → 5 |
| `substring(int)` | 从索引开始截取 | `"Hello".substring(1)` → "ello" |
| `substring(int, int)` | 截取一段 | `"Hello".substring(0, 2)` → "He" |
| `indexOf(String)` | 查找子串位置 | `"Hello".indexOf("e")` → 1 |
| `equals(String)` | 比较内容 | `s.equals("Hello")` |
| `toUpperCase()` | 转大写 | `"Hello".toUpperCase()` → "HELLO" |
| `toLowerCase()` | 转小写 | `"Hello".toLowerCase()` → "hello" |

### 字符串拼接
```java
String s = "Hello" + " " + "World";  // "Hello World"
```

## 代码示例

### 示例 1: 截取子串
```java
public class SubstringDemo {
    public static void main(String[] args) {
        String s = "Hello World";
        
        System.out.println(s.substring(0, 5));   // "Hello"
        System.out.println(s.substring(6));      // "World"
    }
}
```

### 示例 2: 查找子串
```java
public class IndexOfDemo {
    public static void main(String[] args) {
        String s = "Hello World";
        
        System.out.println(s.indexOf("W"));      // 6
        System.out.println(s.indexOf("World"));  // 6
        System.out.println(s.indexOf("Java"));   // -1 (没找到)
    }
}
```

### 示例 3: 字符串比较
```java
public class StringComparison {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = "Hello";
        String s3 = new String("Hello");
        
        System.out.println(s1.equals(s2));  // true
        System.out.println(s1.equals(s3));  // true (比较内容)
    }
}
```

## 例题

### 例题 1: 选择题
`"Programming".substring(3, 7)` 的结果是？
A. "gram"
B. "ogra"
C. "gramm"
D. "prog"

**答案: A**

### 例题 2: 编程题
从字符串 "Computer Science" 中提取 "Science" 并输出。

**参考答案:**
```java
public class ExtractWord {
    public static void main(String[] args) {
        String text = "Computer Science";
        String word = text.substring(9);
        
        System.out.println("Extracted: " + word);
    }
}
```
