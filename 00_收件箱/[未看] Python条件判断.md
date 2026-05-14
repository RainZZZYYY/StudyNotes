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

（更新于 2026-05-15）

- **卫语句**：把异常条件提前 return，消灭深层嵌套。`if not ok: return` 让主逻辑留在第一层缩进（更新于 2026-05-15）
- **分支顺序遮蔽**：`if-elif` 从上到下命中即停，宽泛条件在前会挡住后面的具体条件。从大到小或从小到大排列（更新于 2026-05-15）
- **0 值陷阱**：`if count:` 在 `count == 0` 时走 else。工业场景用 `if count is not None` 区分「没有缺陷」和「没检测到」（更新于 2026-05-15）
- **`in` 替代 or 链**：`if x in {"a", "b", "c"}:` 比 `if x == "a" or x == "b" or x == "c":` 更清晰高效（更新于 2026-05-15）
- **match-case**（Python 3.10+）：替代 C 的 switch，支持模式匹配（更新于 2026-05-15）
- **条件表达式（三元）**：`result = "OK" if score > threshold else "NG"`，等价 C 的 `?:`（更新于 2026-05-15）
- **成本敏感决策**（工业视觉）：漏检（FN）代价 >> 误检（FP），阈值设计偏向宁可误检不放过（更新于 2026-05-15）

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

# 卫语句 — 消灭深层嵌套
def detect(image):
    if image is None:
        return None
    if image.shape[0] < 100:
        return None
    # 主逻辑在顶层
    return model(image)

# in 集合成员 — 替代 or 链
CRITICAL = {"裂纹", "气泡", "异物"}
if defect_type in CRITICAL:
    stop_line()

# match-case
match status:
    case 200: msg = "OK"
    case 404: msg = "未连接"
    case _:   msg = "未知"

# 三元表达式
result = "OK" if confidence > threshold else "NG"
```

## 实际应用（工业视觉）

- 阈值二值化：`if pixel > threshold → 255 else → 0`
- 缺陷面积过滤：`if area > min_threshold → NG`
- 多级规则引擎：面积 + 位置 + 形态组合判定
- 缺陷分级（if-elif-else 链）：严重 > 中等 > 轻微 > 无
- 多条件允收：`if (size_ok and surface_ok) or is_calibration: accept()`

## 关联

- [[Python循环]]
- [[Python变量]]
- [[函数]]
- [[Python异常处理]]

- [ ] 结尾已确认
