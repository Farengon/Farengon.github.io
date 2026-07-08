---
layout: default
title: 1.11 Math Class
parent: Unit 1: Using Objects and Methods
nav_order: 11
---

# 1.11 Math Class

## 基础知识

### 常用 Math 方法
| 方法 | 描述 | 示例 |
|------|------|------|
| `Math.abs(x)` | 绝对值 | `Math.abs(-5)` → 5 |
| `Math.pow(a, b)` | a 的 b 次方 | `Math.pow(2, 3)` → 8.0 |
| `Math.sqrt(x)` | 平方根 | `Math.sqrt(16)` → 4.0 |
| `Math.random()` | 随机数 [0.0, 1.0) | `Math.random()` |
| `Math.round(x)` | 四舍五入 | `Math.round(3.6)` → 4 |

## 代码示例

### 示例 1: Math 方法演示
```java
public class MathDemo {
    public static void main(String[] args) {
        System.out.println("abs(-5): " + Math.abs(-5));
        System.out.println("pow(2, 3): " + Math.pow(2, 3));
        System.out.println("sqrt(16): " + Math.sqrt(16));
        System.out.println("round(3.6): " + Math.round(3.6));
    }
}
```

### 示例 2: 生成随机整数
```java
public class RandomNumbers {
    public static void main(String[] args) {
        // 0 到 9 的随机整数
        int rand1 = (int) (Math.random() * 10);
        System.out.println("0-9: " + rand1);
        
        // 1 到 10 的随机整数
        int rand2 = (int) (Math.random() * 10) + 1;
        System.out.println("1-10: " + rand2);
    }
}
```

## 例题

### 例题 1: 选择题
`Math.abs(-7)` 的结果是？
A. -7
B. 7
C. 0
D. 49

**答案: B**

### 例题 2: 编程题
生成 1 到 100 的随机整数并输出。

**参考答案:**
```java
public class Random100 {
    public static void main(String[] args) {
        int random = (int) (Math.random() * 100) + 1;
        System.out.println("Random (1-100): " + random);
    }
}
```
