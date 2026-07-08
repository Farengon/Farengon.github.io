---
layout: default
title: 4.7 Wrapper Classes
parent: Unit 4
nav_order: 7
---

# 4.7 Wrapper Classes

## 基础知识

### 包装类
| 基本类型 | 包装类 |
|----------|--------|
| `int` | `Integer` |
| `double` | `Double` |
| `boolean` | `Boolean` |

### 自动装箱和拆箱
```java
Integer x = 5;        // 自动装箱
int y = x;            // 自动拆箱
```

## 代码示例

### 示例 1: 包装类
```java
public class WrapperDemo {
    public static void main(String[] args) {
        Integer num1 = 10;
        Integer num2 = 20;
        
        System.out.println(num1 + num2);  // 30
        System.out.println(Integer.MAX_VALUE);  // 最大值
    }
}
```

## 例题

### 例题 1: 选择题
int 的包装类是？
A. `Int`
B. `Integer`
C. `Number`
D. `int`

**答案: B**
