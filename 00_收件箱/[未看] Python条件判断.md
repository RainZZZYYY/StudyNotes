---
aliases:
  - Python条件判断
  - if elif else
created: 2026-05-11
tags:
  - python
  - control-flow
---

- [ ] 开头已确认
# Python 条件判断

Python 条件判断语法比 C 简洁：去括号和花括号，用 `elif` 代替 `else if`，`and/or/not` 代替 `&&/||/!`。

## 关键点

- 基本语法：`if 条件:` → `elif 条件:` → `else:`
- 逻辑运算符：`and` / `or` / `not`（不是 C 的 `&&` / `||` / `!`）
- 代码块靠冒号 `:` + 缩进，缩进必须一致（通常 4 空格）
- Python 中 `if x = 5:` 直接报错（C 这是大坑）
- `is` 比较内存地址，`==` 比较值 — 不要混用
- `if...if...else` 不等同 `if...elif...else`，多个 `if` 各自独立判断
- 支持链式比较：`if 0 <= score <= 100:`
- 真值测试：空字符串、0、None、空列表/字典 → `False`

## 怎么用

```python
if score >= 90:
    print("A")
elif score >= 60:
    print("B")
else:
    print("C")

# 链式比较（Python 独有）
if 0 <= score <= 100:
    print("合法")

# 利用真值测试
if items:      # 代替 if len(items) > 0:
    process(items)
```

## 实际应用（工业视觉）

- 阈值二值化：`if pixel > threshold → 255 else → 0`
- 缺陷面积过滤：`if area > min_threshold → NG`
- 多级规则引擎：面积 + 位置 + 形态组合判定

## 关联

- [[Python循环]]
- [[Python变量]]

- [ ] 结尾已确认
