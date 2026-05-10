---
aliases:
  - Git基础
  - Git和GitHub的区别
created: 2026-05-10
tags:
  - git
  - 工具与环境
---

# Git 核心概念

Git 是本地版本控制工具，GitHub 是云端代码托管平台。可以只用 Git 不碰 GitHub，但 GitHub 必须依赖 Git。

## 关键点

- **Git 和 GitHub 不是同一个东西**：Git 管本地版本历史，断网也能 commit；GitHub 是远程仓库，用于共享和协作
- **四个区域**：工作区（写代码）→ `git add` → 暂存区（挑选要提交的改动）→ `git commit` → 本地仓库（.git/，存快照）→ `git push` → 远程仓库（GitHub）
- **commit 是一张快照**：记录谁改的、改了什么、为什么改。每次 commit 生成唯一 hash，随时可回退
- **commit message 是写给自己和协作者的备忘录**："fix bug" 没用，"修复登录页密码为空时崩溃" 才有用
- **README 是项目入口**：决定了别人（和两周后的自己）3 秒内能否看懂项目是干什么的、怎么跑

## 怎么用

```bash
# 初始化仓库
git init

# 查看四个区域之间的差异
git status

# 工作区 → 暂存区
git add 文件名

# 暂存区 → 本地仓库
git commit -m "描述做了什么"

# 本地仓库 → 远程仓库
git push origin main
```

## 关联

- [[Git文件找回]]
- [[WSL2原理]]
