---
aliases:
  - Python列表
  - list
created: 2026-05-11
tags:
  - python
  - data-structure
---

- [ ] 开头已确认
# Python 列表

列表是一组按顺序存放的数据，用 `[]`，索引从 0 开始。一个变量管理一堆数据。

## 关键点

- 创建：`nums = [1, 3, 5]`，空列表 `[]`
- 索引：`nums[0]` 取第一个，`nums[-1]` 取最后一个
- 切片：`nums[1:3]` 含开头不含结尾
- 增删改：`append()`、`del` / `pop()`、直接赋值
- 与 C 的差异：列表可混合类型、动态扩容、内建 `sort()` / `reverse()`
- 嵌套列表：`matrix[0][1]` 取第一行第二列，图像本质就是二维列表

## 怎么用

```python
nums = [1, 3, 5, 7, 9]
nums.append(6)          # [1,3,5,7,9,6]
del nums[1]             # 按索引删
nums[0] = 10            # 按索引改
nums[2:5]               # 切片 → [5,7,9]
nums.sort(reverse=True) # 降序排列
nums.reverse()          # 翻转

pixels = [[128,255,0], [64,128,255], [0,64,128]]
pixels[1][1]            # 128 — 中心像素
```

## 关联

- [[Python变量]]
- [[Python字典]] — 字典按名取值，列表按索引取值
- [[Python循环]] — 遍历列表常用 for

- [ ] 结尾已确认
