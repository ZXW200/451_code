# 451_code 项目运行说明

本项目包含两个独立的数据分析任务。

## 项目结构

```
451_code/
├── 451_code/
│   ├── task1/    # 气候数据分析
│   └── task2/    # 图像分析
└── README.md
```

## ⚠️ 重要提示

**必须在项目根目录下运行命令！**

确保你的当前目录是包含 `451_code` 文件夹和 `README.md` 的目录。如果你在 Windows 上看到路径类似 `C:\Users\...\桌面\451_code`，那么这就是正确的目录。

## Task 1 - 气候数据分析

### 功能
- 气候数据预处理
- 聚类分析

### 运行方法

**从项目根目录运行**（包含 451_code 文件夹的目录）：

```bash
python -m 451_code.task1.main --data <数据文件路径>
```

### 参数说明
- `--data`: 必需参数，指定气候数据 CSV 文件的路径

### 示例

```bash
python -m 451_code.task1.main --data data/climate.csv
```

---

## Task 2 - 图像分析

### 功能
- 特征提取
- 降维
- 聚类
- 分类

### 运行方法

**从项目根目录运行**（包含 451_code 文件夹的目录）：

```bash
python -m 451_code.task2.main --dataset <数据集目录> [--models 模型名称]
```

### 参数说明
- `--dataset`: 必需参数，指定数据集目录路径
- `--models`: 可选参数，指定使用的模型，可选值：
  - `resnet50` (默认)
  - `densenet121`
  - `dinov2`
  - 可以指定多个模型

### 示例

```bash
# 使用默认模型 (ResNet50)
python -m 451_code.task2.main --dataset data/images

# 使用多个模型
python -m 451_code.task2.main --dataset data/images --models resnet50 densenet121 dinov2

# 使用单个指定模型
python -m 451_code.task2.main --dataset data/images --models dinov2
```

---

## 依赖安装

在运行之前，请确保安装必要的 Python 依赖：

```bash
pip install numpy pandas scikit-learn matplotlib torch torchvision
```

Task2 可能还需要额外的深度学习库。

## 输出

- Task 1: 结果保存在 `pipeline/history` 目录下，包括预处理和聚类结果
- Task 2: 结果保存在 `pipeline/history` 目录下，包括特征提取、降维、聚类和分类的结果及可视化图表

## 注意事项

1. 确保提供的数据路径正确且文件存在
2. Task2 需要 GPU 支持以获得更好的性能（可自动检测并使用 CUDA）
3. 输出目录会自动创建
