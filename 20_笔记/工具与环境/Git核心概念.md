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

## SSH 认证（更新于 2026-05-10）

GitHub 支持两种认证方式：

| | HTTPS | SSH |
|------|-------|------|
| 地址格式 | `https://github.com/user/repo.git` | `git@github.com:user/repo.git` |
| 认证方式 | 每次输密码或 token | 密钥对自动验证 |
| 稳定性 | WSL2 中可能间歇超时 | 更稳定 |

SSH 密钥配置流程：
1. `ssh-keygen -t ed25519 -C "邮箱"` 生成密钥对
2. 公钥（`.pub`）添加到 GitHub Settings → SSH Keys
3. `git remote set-url origin git@github.com:user/repo.git` 切换地址

## 远程仓库（remote）管理（更新于 2026-05-10）

| 命令 | 作用 |
|------|------|
| `git remote -v` | 查看当前关联了哪些远程仓库 |
| `git remote add 别名 地址` | 关联一个新远程 |
| `git remote set-url 别名 新地址` | 修改远程地址（如 HTTPS → SSH） |

一个本地仓库可以关联多个远程。

## 上游分支（upstream）（更新于 2026-05-10）

上游分支是本地分支和远程分支的对应关系。设置后 `git push`/`git pull` 不需要每次指定远程名和分支名：

```bash
git push --set-upstream origin main   # 只需设一次
```

之后 `git push` 自动推到 origin/main，`git pull` 自动从 origin/main 拉取，`git status` 会显示本地与远程的差异。

## 关联

- [[Git文件找回]]
- [[WSL2原理]]
