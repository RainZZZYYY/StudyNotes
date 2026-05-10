---
aliases:
  - WSL2
  - Windows Subsystem for Linux
created: 2026-05-10
tags:
  - tools
  - concept
---

# WSL2 原理

WSL2 是 Windows 上的 Linux 子系统，让开发者在 Windows 上直接运行完整的 Linux 内核，无需双系统或传统虚拟机。

## 关键点

- **Windows → WSL2 → Ubuntu 三层关系**：Windows 是宿主机，WSL2 是一个轻量级 Hyper-V 虚拟机（包含完整 Linux 内核），Ubuntu 运行在这个虚拟机里。不是模拟层，性能接近原生 Linux
- **为什么视觉工程常用 Linux**：深度学习框架（PyTorch、TensorFlow）、CUDA 驱动、FFmpeg、图像处理库在 Linux 上原生支持最好，大部分开源视觉项目的默认环境也是 Linux
- **虚拟环境的作用**：`.venv` 或 Conda 环境隔离每个项目的 Python 依赖，避免 A 项目需要 numpy 1.x 而 B 项目需要 numpy 2.x 的冲突
- **项目目录 + 依赖隔离的意义**：每个项目有独立目录和独立 Python 环境，可复现、可迁移。换一台机器，只要有 Python 就能重建环境

## 怎么用

```bash
# 安装 WSL
wsl --install -d Ubuntu-22.04

# 进入 WSL
wsl

# 在 WSL 中检查 Python
python3 --version

# 创建虚拟环境
python3 -m venv .venv
source .venv/bin/activate

# VS Code 连接 WSL
# 安装 Remote - WSL 扩展 → Ctrl+Shift+P → WSL: Connect to WSL
```

## 关联

- [[虚拟环境概念]]
- [[Python虚拟环境]]
- [[Obsidian笔记规范]]
