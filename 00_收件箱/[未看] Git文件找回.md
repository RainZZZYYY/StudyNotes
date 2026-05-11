---
aliases:
  - Git恢复删除文件
  - git restore
created: 2026-05-10
tags:
  - git
  - 工具与环境
---

# Git 文件找回

只要 commit 过，文件就永久存在于 Git 历史中。删文件只删了当前版本，历史版本里还在。

## 关键点

- **只删了工作区文件（未 add）**：`git restore 文件名` 从最近 commit 恢复
- **已 add 到暂存区**：先 `git restore --staged 文件名` 取消暂存，再恢复文件
- **已 commit**：`git revert <那个commit>` 生成新 commit 撤销删除；或 `git reset --hard HEAD~1` 回退一个版本
- **已 push**：同上 revert/reset，再 push（reset 后需 force push，慎用）
- **删了很久找不到了**：`git log -- 文件名` 找到最后一次存在的 commit，`git checkout <commit> -- 文件名` 拿回来

## 怎么用

```bash
# 找文件最后一次存在的位置
git log -- 文件名

# 从历史中恢复文件
git checkout <commit-hash> -- 文件名
```

## 关联

- [[Git核心概念]]
