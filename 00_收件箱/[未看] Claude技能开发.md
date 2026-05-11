---
aliases:
  - Claude Code Skills
  - 自定义技能
created: 2026-05-11
tags:
  - tools
  - concept
---

- [ ] 开头已确认
# Claude 技能开发

Claude Code 技能是放在 `~/.claude/skills/<技能名>/SKILL.md` 下的自然语言指令文件，Claude Code 启动时自动发现并注册。

## 关键点

- **自动发现，无需注册**：只要在 `~/.claude/skills/` 下创建 `<技能名>/SKILL.md`，Claude Code 就会自动识别，不需要修改任何配置文件
- **YAML frontmatter** 声明 `name` 和 `description`；`description` 末尾写明触发方式决定了技能的调用机制
- **两种触发方式**：description 中写"当用户说...时触发"→ 对话关键词匹配自动触发；写"仅通过 /xxx 主动调用"→ 用户手动 slash 命令
- **Markdown 正文即指令**：用编号步骤描述工作流，LLM 逐条理解执行。技能的行为完全由文字控制，不需要编程
- **技能间可以协作**：一个技能可以在某一步调用另一个技能（如 session 结束时自动触发 obsidian-note），也可以并行使用不冲突
- **references/ 子目录**可放辅助参考文档，主 SKILL.md 引用其格式和规则

## 怎么用

```yaml
# SKILL.md 最小骨架
---
name: my-skill
description: 一句话描述功能，以及触发方式。
---

# 技能标题

简短说明。

## 第 1 步：xxx

具体操作指令。

## 第 2 步：xxx

...

## 原则

- 设计原则 1
- 设计原则 2
```

## 设计经验

- **步骤用数字编号**，给 LLM 明确的执行顺序
- **展示模板用代码块**，统一输出格式（如进度总览、确认菜单）
- **数据文件路径硬编码**，技能直接读写具体文件，不依赖参数传递
- **临时标记文件做状态恢复**（如 `当前会话.md`），轻量不复杂
- **用户确认是关键环节**，不替用户做决定（标记完成、删除文件等都需确认）

## 关联

- [[Claude技能清单]]
- [[2026-05-11_技能开发]]
- [[session技能]]
- [[learn技能]]
- [[push-skills技能]]

- [ ] 结尾已确认
