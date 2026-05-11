---
aliases:
  - Python循环
  - for while
created: 2026-05-11
tags:
  - python
  - control-flow
---

# Python 循环

Python 的 `for` 本质是 for-each 遍历迭代器，与 C 的 `for(;;)` 有根本差异。`while` 两者基本一致。

## 关键点

- `for item in collection` 直接取元素，不用 `range(len())`
- 需要索引时用 `enumerate()`：`for i, v in enumerate(seq)`
- Python `for` 中修改循环变量无效（被迭代器下个值覆盖）
- C 风格需手动控制循环变量 → 用 `while`
- `range(起点, 终点, 步长)`，含起点不含终点
- Python 独有 `for...else`：循环正常结束（无 break）执行 else
- Python 无 `do...while`

## 怎么用

```python
for i in range(5):            # 0 1 2 3 4
for i in range(2, 7, 2):     # 2 4 6
for i in range(9, -1, -1):   # 倒序 9 8 7 ... 0

for i, name in enumerate(names):
    print(f"{i}: {name}")

# 嵌套遍历像素
for row in pixels:
    for pixel in row:
        print(pixel)
```

## 关联

- [[Python列表]]
- [[Python条件判断]]
