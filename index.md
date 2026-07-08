---
layout: default
title: 首页
nav_order: 1
permalink: /
---

# 欢迎来到 AP 教程网 👋

在这里选择你想学习的 AP 课程，开始备考吧！

## 📚 课程列表

<style>
.course-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

.course-card {
  border: 1px solid var(--border-color, #e0e0e0);
  border-radius: 8px;
  background: var(--bg-color, #ffffff);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
}

.course-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.12);
}

.course-card a {
  display: block;
  padding: 1.5rem;
  text-decoration: none;
  color: inherit;
}

.course-card h3 {
  margin: 0 0 0.5rem 0;
  font-size: 1.25rem;
}

.course-card p {
  margin: 0.5rem 0 1rem 0;
  color: var(--text-muted, #666);
  font-size: 0.95rem;
}

.course-tag {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 500;
}

.tag-math {
  background: #e3f2fd;
  color: #1565c0;
}

.tag-physics {
  background: #fff3e0;
  color: #ef6c00;
}

.tag-cs {
  background: #e8f5e9;
  color: #2e7d32;
}
</style>

<div class="course-cards">
  <div class="course-card">
    <a href="./csa/">
      <h3>💻 AP 计算机科学 A</h3>
      <span class="course-tag tag-cs">计算机科学</span>
      <p>Java 编程基础、面向对象设计、数据结构与算法，完全基于 College Board 考纲。</p>
    </a>
  </div>

  <div class="course-card">
    <a href="./ap-calculus/">
      <h3>📐 AP 微积分 BC</h3>
      <span class="course-tag tag-math">数学</span>
      <p>极限、微分、积分、级数，深入掌握微积分核心概念与解题技巧。</p>
    </a>
  </div>

  <div class="course-card">
    <a href="./ap-physics/">
      <h3>⚡ AP 物理 C</h3>
      <span class="course-tag tag-physics">物理</span>
      <p>力学与电磁学，微积分基础上的物理原理，适合理工科学生。</p>
    </a>
  </div>
</div>

## 📝 说明

- 每门课程都按照 College Board 官方大纲顺序组织
- 使用左侧导航栏或课程卡片进入各单元的学习
- 支持全文搜索功能，快速定位知识点