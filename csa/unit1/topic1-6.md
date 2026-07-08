---
layout: default
title: 1.6 Compound Assignment Operators
parent: Unit 1
nav_order: 6
---

# 1.6 Compound Assignment Operators

## 基础知识

### 复合赋值运算符
| 运算符 | 描述 | 等价形式 |
|--------|------|----------|
| `+=` | 加后赋值 | `a += b` → `a = a + b` |
| `-=` | 减后赋值 | `a -= b` → `a = a - b` |
| `*=` | 乘后赋值 | `a *= b` → `a = a * b` |
| `/=` | 除后赋值 | `a /= b` → `a = a / b` |
| `%=` | 取模后赋值 | `a %= b` → `a = a % b` |

### 自增和自减
| 运算符 | 描述 |
|--------|------|
| `++` | 自增 1 |
| `--` | 自减 1 |

**前缀 vs 后缀:**
- `++a`: 先加 1，再使用值
- `a++`: 先使用值，再加 1

## 代码示例

### 示例 1: 复合赋值运算符
```java
public class CompoundAssign {
    public static void main(String[] args) {
        int x = 10;
        
        x += 5;   // x = 10 + 5 = 15
        System.out.println("x += 5: " + x);
        
        x -= 3;   // x = 15 - 3 = 12
        System.out.println("x -= 3: " + x);
        
        x *= 2;   // x = 12 * 2 = 24
        System.out.println("x *= 2: " + x);
    }
}
```

### 示例 2: 自增自减
```java
public class IncrementDecrement {
    public static void main(String[] args) {
        int a = 5;
        int b = 5;
        
        System.out.println("a++: " + a++);  // 输出 5，然后 a 变 6
        System.out.println("a: " + a);      // 输出 6
        
        System.out.println("++b: " + ++b);  // b 先变 6，然后输出 6
        System.out.println("b: " + b);      // 输出 6
    }
}
```

## 例题

### 例题 1: 选择题
执行 `x = 5; x *= 2 + 3;` 后，x 的值是？
A. 10
B. 13
C. 25
D. 7

**答案: C**

### 例题 2: 编程题
初始金额是 1000 元，每年增长 5%。使用复合赋值运算符计算 3 年后的金额。

**参考答案:**
```java
public class Investment {
    public static void main(String[] args) {
        double money = 1000.0;
        
        money *= 1.05;  // 第1年
        money *= 1.05;  // 第2年
        money *= 1.05;  // 第3年
        
        System.out.println("After 3 years: " + money);
    }
}
```
