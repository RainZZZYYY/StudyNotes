---
aliases:
  - Python变量
  - variable
created: 2026-05-11
tags:
  - python
  - basic
---

- [ ] 开头已确认
# Python 变量

变量是带名字的容器，用来存放数据。Python 不需要声明类型，赋值即确定类型，且同一变量可重新赋值为不同类型（动态类型）。

## 关键点

- 基本类型：`str`（字符串）、`int`（整数）、`float`（浮点数）、`bool`（布尔值）
- 命名规则：不能数字开头、不能含连字符 `-`、不能和关键字重名，推荐 `snake_case`
- 与 C 的差异：无需声明类型、支持 `a, b, c = 1, 2, 3` 多变量同时赋值
- 类型可用 `type()` 查看

## 怎么用

```python
name = "rainz"
age = 25
pi = 3.14159
is_member = True

x = 100          # int
x = "hello"      # 同一变量可以换类型

a, b, c = 1, 2, 3   # 多变量同时赋值
```

## 关联

- [[Python列表]] — 列表是多个变量的有序集合
- [[Python字典]] — 字典是键值对的集合

- [ ] 结尾已确认
