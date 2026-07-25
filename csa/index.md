---
layout: default
title: AP CSA
nav_order: 2
has_children: true
permalink: /csa/
---

# AP Computer Science A 

## 课程结构

| 单元 | 名称 | 考试权重 | 课时 |
|------|------|----------|------|
| **Unit 1** | Using Objects and Methods | 15-25% | 32-34 |
| **Unit 2** | Selection and Iteration | 25-35% | 29-31 |
| **Unit 3** | Class Creation | 10-18% | 20-22 |
| **Unit 4** | Data Collections | 30-40% | 50-52 |

## 准备

- [下载JDK](https://www.oracle.com/java/technologies/downloads/)

- 下载IDE

  我个人喜欢[VSCode](https://code.visualstudio.com/)

{: .note}
> **JDK & IDE**
>
> JDK 是Java开发工具和运行环境，而 IDE 是代码编辑器（主流的Java IDE包括IDEA、Eclipse、NetBeans等）。
>
> 也就是说只需要JDK就可以运行Java程序了，IDE只是让写代码的过程更方便（自动补全/自动纠错/运行代码...）

现在你可以新建一个文件夹，在 IDE 中打开这个文件夹，并在里面新建一个叫做“Helloworld.java”的文件。复制粘贴下面这段代码：

```java
public class Helloworld {
	public static void main(String[] args) {
		System.out.println("Hello world!")
	}
}
```

点击“运行”，你就会看到计算机输出“Hello world！”