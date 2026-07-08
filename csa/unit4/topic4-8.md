---
layout: default
title: 4.8 ArrayList Methods
parent: Unit 4: Data Collections
nav_order: 8
---

# 4.8 ArrayList Methods

## 基础知识

### ArrayList 特点
- 大小可以动态改变
- 只能存储对象（使用包装类）

### 常用方法
| 方法 | 描述 |
|------|------|
| `add(obj)` | 添加元素 |
| `add(index, obj)` | 在指定位置添加 |
| `get(index)` | 获取元素 |
| `set(index, obj)` | 替换元素 |
| `remove(index)` | 删除元素 |
| `size()` | 返回大小 |

## 代码示例

### 示例 1: ArrayList 方法
```java
import java.util.ArrayList;

public class ArrayListDemo {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<String>();
        
        list.add("Apple");
        list.add("Banana");
        list.add(1, "Cherry");  // 在索引 1 插入
        
        System.out.println(list.get(0));  // Apple
        System.out.println(list.size());   // 3
        
        list.set(1, "Blueberry");  // 替换
        list.remove(0);  // 删除第一个元素
        
        System.out.println(list);  // [Blueberry, Banana]
    }
}
```

## 例题

### 例题 1: 选择题
获取 ArrayList 大小的方法是？
A. `length`
B. `size()`
C. `count()`
D. `getLength()`

**答案: B**
