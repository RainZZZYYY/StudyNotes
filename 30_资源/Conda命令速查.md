---
aliases:
  - Conda 用法
  - conda cheatsheet
created: 2026-04-09
tags:
  - tools
  - reference
  - python
---

# Conda 命令速查

概念理解见 [[虚拟环境概念]]。

## 基本信息

```bash
conda --version          # 查看版本
conda info               # 查看配置信息
conda config --show channels  # 查看镜像源
```

## 环境管理

```bash
conda env list           # 查看所有环境
conda create -n myenv python=3.11           # 创建环境
conda create -n data_env python=3.11 numpy pandas matplotlib  # 创建并装包
conda activate myenv     # 激活环境
conda deactivate         # 退出环境
conda remove -n myenv --all  # 删除环境

# 重命名（克隆后删旧）
conda create -n new_env --clone old_env
conda remove -n old_env --all
```

## 包管理

```bash
conda install numpy              # 安装包
conda install numpy=1.26         # 安装指定版本
conda remove numpy               # 卸载包
conda update numpy               # 更新包
conda list                       # 查看当前环境已安装的包
conda install -n myenv pandas    # 在指定环境中安装
```

## 搜索与渠道

```bash
conda search pytorch             # 搜索包
conda install -c conda-forge requests    # 指定渠道安装
conda config --add channels conda-forge  # 添加渠道
conda config --set channel_priority strict  # 严格优先级
```

## 环境导出与恢复

```bash
conda env export > environment.yml              # 导出完整环境
conda env create -f environment.yml             # 从文件创建
conda env export --from-history > environment.yml  # 精简导出
conda env update -f environment.yml --prune     # 更新并清理
conda list --export > requirements-conda.txt    # 导出包列表
```

## Conda 中使用 pip

```bash
conda activate myenv
pip install package_name

# 检查 pip 属于哪个环境
which pip        # Linux / macOS
where pip        # Windows
```

## 查看环境路径

```bash
echo $CONDA_PREFIX      # Linux / macOS
echo %CONDA_PREFIX%     # Windows CMD
$env:CONDA_PREFIX       # PowerShell
```

## 清理

```bash
conda clean --all       # 清理缓存、索引、无用包
```

## 常见问题

**`conda activate` 无效**：运行 `conda init powershell` 后重启终端。

**下载速度慢**：配置镜像源，优先使用稳定渠道。

**环境冲突**：新建干净环境重新安装，减少 channel 混用。

**包安装成功但导入失败**：检查是否激活了正确环境，`python` 和 `pip` 是否指向同一环境，IDE 解释器是否选对。

## 关联

- [[虚拟环境概念]]
- [[Python虚拟环境]]
