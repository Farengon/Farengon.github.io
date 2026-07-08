---
layout: default
title: 1.3 Expressions and Output
parent: Unit 1: Using Objects and Methods
nav_order: 3
---

# 1.3 Expressions and Output

## 基础知识

### 算术运算符
| 运算符 | 描述 | 示例 |
|--------|------|------|
| `+` | 加法 | `5 + 3` |
| `-` | 减法 | `5 - 3` |
| `*` | 乘法 | `5 * 3` |
| `/` | 除法 | `5 / 2` (整数除法结果为 2) |
| `%` | 取模 (余数) | `5 % 2` (结果为 1) |

### 运算优先级
1. 括号 `()`
2. 乘除 `* / %`
3. 加减 `+ -`

## 代码示例

### 示例 1: 基本算术运算
```java
public class Arithmetic {
    public static void main(String[] args) {
        int a = 10;
        int b = 3;
        
        System.out.println("a + b = " + (a + b));
        System.out.println("a - b = " + (a - b));
        System.out.println("a * b = " + (a * b));
        System.out.println("a / b = " + (a / b));
        System.out.println("a % b = " + (a % b));
    }
}
```

### 示例 2: 混合类型运算
```java
public class MixedTypes {
    public static void main(String[] args) {
        int x = 5;
        double y = 2.0;
        
        System.out.println(x / y);   // 2.5 (double)
        System.out.println(x / 2);   // 2 (int)
    }
}
```

## 例题

### 例题 1: 选择题
`7 % 3` 的结果是？
A. 2
B. 1
C. 2.333
D. 3

**答案: A**

### 例题 2: 编程题
计算圆的面积和周长，半径为 5。使用公式：
- 面积 = π × r²
- 周长 = 2 × π × r

**参考答案:**
```java
public class Circle {
    public static void main(String[] args) {
        double radius = 5.0;
        double pi = 3.14159;
        
        double area = pi * radius * radius;
        double circumference = 2 * pi * radius;
        
        System.out.println("Area: " + area);
        System.out.println("Circumference: " + circumference);
    }
}
```
