---
layout: default
title: 2.2 Boolean Expressions
parent: Unit 2
nav_order: 2
---

# 2.2 Boolean Expressions

## 基础知识

### 关系运算符
| 运算符 | 描述 | 示例 |
|--------|------|------|
| `==` | 等于 | `5 == 5` → true |
| `!=` | 不等于 | `5 != 3` → true |
| `<` | 小于 | `3 < 5` → true |
| `>` | 大于 | `5 > 3` → true |
| `<=` | 小于等于 | `3 <= 5` → true |
| `>=` | 大于等于 | `5 >= 5` → true |

### 逻辑运算符
| 运算符 | 描述 |
|--------|------|
| `&&` | AND (与) |
| `||` | OR (或) |
| `!` | NOT (非) |

## 代码示例

### 示例 1: 布尔表达式
```java
public class BooleanExpressions {
    public static void main(String[] args) {
        int x = 5;
        int y = 10;
        
        System.out.println(x < y);        // true
        System.out.println(x == y);       // false
        System.out.println(x != y);       // true
        System.out.println(x < y && x > 0);  // true
        System.out.println(!(x < y));     // false
    }
}
```

## 例题

### 例题 1: 选择题
`5 > 3 && 2 < 4` 的结果是？
A. true
B. false
C. 5
D. 2

**答案: A**
