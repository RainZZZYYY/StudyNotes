---
aliases:
  - Python异常处理
  - try except
  - exception handling
created: 2026-05-15
tags:
  - python
  - control-flow
---

- [ ] 开头已确认

# Python 异常处理

异常处理让程序从「遇到错误就死」变成「遇到错误能应对」。Python 用 `try-except-finally` 结构替代 C 语言的错误码模式——出错时抛出异常对象，调用栈回退直到被捕获。

## 关键点

- 基本结构：`try` → `except 具体异常` → `else`（无异常才执行）→ `finally`（无论如何都执行）
- 异常类型有层级：`BaseException → Exception → 具体异常`。捕获从具体到宽泛，宽泛在前会遮蔽后面的
- 永远不要裸 `except:`——连 `KeyboardInterrupt`、`SystemExit` 都吞掉，Ctrl+C 杀不掉程序
- 永远不要 `except: pass`——出错悄无声息，数据悄悄变坏，无从调试。至少 `logger.error(exc_info=True)`
- 用 `with` 上下文管理器自动释放资源，比 `try-finally` 更简洁
- 重新抛异常用裸 `raise`，保留原始 traceback；`raise NewError()` 会丢失栈信息
- `assert` 是开发期的「自爆按钮」，生产环境用 `python -O` 会全部跳过。生产校验用 `if + raise`

## 怎么用

```python
# 基本结构
def safe_read(path):
    try:
        with open(path) as f:
            return f.read()
    except FileNotFoundError:
        print(f"文件不存在: {path}")
        return None
    except PermissionError:
        print(f"无权限: {path}")
        return None
    except Exception as e:
        print(f"未知错误: {path} — {e}")
        return None

# 记录但不处理，交给上层
def load_config(path):
    try:
        with open(path) as f:
            return json.load(f)
    except FileNotFoundError:
        print(f"[WARN] {path} 不存在")
        raise   # 裸 raise，保留原始 traceback

# 工业场景：批处理容错
def batch_process(paths):
    ok, fail = [], []
    for path in paths:
        try:
            ok.append(process(path))
        except FileNotFoundError:
            fail.append((path, "不存在"))
        except Exception as e:
            print(f"未知: {path} — {e}")
            fail.append((path, "未知"))
    return ok, fail
```

## 实际应用（工业视觉）

- 相机 I/O 容错：None 帧跳过、超时重试、断连重连（几乎所有相机 SDK 都需要防御性包裹）
- 图像批处理：1000 张图片中第 523 张损坏，skip 继续而非整体崩溃
- 模型推理异常：`CUDA OutOfMemoryError`、输入 shape 不匹配，每种异常不同处理策略
- Pipeline 优雅降级：YOLO 失败切 Faster R-CNN，GPU 不可用切 CPU

## 关联

- [[Python条件判断]]
- [[函数]]

- [ ] 结尾已确认
