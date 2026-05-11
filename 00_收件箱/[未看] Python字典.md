---
aliases:
  - Python字典
  - dict
created: 2026-05-11
tags:
  - python
  - data-structure
---

# Python 字典

字典是无序的键值对集合，用 `{}`，通过键快速查找值。底层是哈希表，O(1) 查找。

## 关键点

- 键必须是不可变类型（字符串、数字、元组），列表不能做键
- 安全访问用 `d.get("key", 默认值)` 而非 `d["key"]`，防止 KeyError 崩溃
- 遍历用 `for k, v in d.items()`（推荐，比 `for k in d` 快 15-20%）
- 合并用 `{**d1, **d2}`，后者覆盖前者同名键
- 浅拷贝 `d.copy()` 嵌套字典会共享内层，需 `copy.deepcopy()`
- JSON ↔ Python 字典：`json.dumps()` / `json.loads()`，工业视觉 API 都用 JSON

## 怎么用

```python
config = {"width": 640, "height": 480, "format": "jpg"}
config.get("fps", 30)         # 安全访问
config["exposure"] = 500      # 新增
merged = {**defaults, **user}  # 合并

for k, v in config.items():
    print(f"{k}: {v}")

label_map = {0: "正常", 1: "划伤", 2: "凹陷"}
label_map[1]  # "划伤"
```

## 实际应用（工业视觉）

- 相机参数配置、检测阈值存储
- 模型推理结果（JSON 格式，对接 MES 系统）
- 分类标签映射

## 关联

- [[Python列表]]
- [[Python变量]]
