# Python Jupyter Notebooks 概览

本文件列出所有已转换的Python Jupyter Notebook及其位置。

## 📚 可用的Notebooks

### ✅ Lab 1 - Python和Bash基础
**文件**: `Lab01/lab1.ipynb`  
**内容**:
- Python基础数据类型和结构
- Pandas数据操作（类似R的dplyr）
- 数据可视化（matplotlib和seaborn）
- Bash脚本基础
- 变量、管道和条件语句

**适合**: 初学者，第一次接触Python数据分析

---

### ✅ Lab 3 - PCA和聚类分析
**文件**: `Lab03/Lab3.ipynb`  
**内容**:
- 主成分分析（PCA）
- K-Means聚类
- 层次聚类
- 批次效应识别和去除
- 差异表达分析概念
- GSEA基因富集分析

**适合**: 已了解Python基础，想学习数据分析方法

---

### ✅ Lab 4 - 机器学习
**文件**: `Lab04/Lab4.ipynb`  
**内容**:
- K近邻分类器（KNN）
- 线性回归和正则化（Ridge、LASSO、ElasticNet）
- 逻辑回归
- 支持向量机（SVM）
- 随机森林
- 交叉验证和模型评估

**适合**: 想学习机器学习基础的学生

---

### ✅ Lab 5 - 基因组比对和峰调用
**文件**: `Lab05/Lab5.ipynb`  
**内容**:
- BWA序列比对（命令行）
- SAMtools使用
- MACS2峰调用
- Python数据读取和可视化

**适合**: 学习基因组学数据分析的学生

---

### ✅ Lab 6 - ATAC-seq分析
**文件**: `Lab06/Lab6.ipynb`  
**内容**:
- ATAC-seq数据分析
- BEDTools操作
- LISA转录因子预测
- Python结果可视化

**适合**: 学习表观基因组学的学生

---

### ✅ Lab 8 - 单细胞RNA测序
**文件**: `Lab08/Lab8.ipynb`  
**内容**:
- Scanpy单细胞分析框架
- 质量控制
- 标准化和特征选择
- 降维和聚类
- 细胞类型注释

**R对照**: Seurat → Scanpy  
**适合**: 学习单细胞分析的学生

---

### ✅ Lab 10 - 生存分析
**文件**: `Lab10/Lab10.ipynb`  
**内容**:
- Kaplan-Meier生存曲线
- Cox比例风险模型
- 生存数据的LASSO正则化
- 模型比较

**R对照**: survival包 → lifelines包  
**适合**: 学习临床数据分析的学生

---

### ✅ Lab 11 - CRISPR筛选分析
**文件**: `Lab11/Lab11.ipynb`  
**内容**:
- MAGeCK工具使用
- CRISPR筛选数据分析
- 结果可视化
- Python下游分析

**适合**: 学习功能基因组学的学生

---

## 🚀 快速开始

### 1. 安装依赖
```bash
# 基础包
pip install pandas numpy matplotlib seaborn jupyter

# 机器学习
pip install scikit-learn scipy

# 生物信息学
pip install scanpy lifelines gseapy
```

### 2. 启动Jupyter
```bash
cd Lab_2021
jupyter notebook
```

### 3. 选择并运行notebook
在浏览器中打开相应的 `.ipynb` 文件并运行。

---

## 📖 学习顺序建议

### 路径1: Python入门
1. Lab01 (Python基础) 
2. Lab03 (数据分析)
3. Lab04 (机器学习)

### 路径2: 生物信息学
1. Lab01 (Python基础)
2. Lab05/Lab06 (基因组学)
3. Lab08 (单细胞)

### 路径3: 临床数据分析
1. Lab01 (Python基础)
2. Lab04 (机器学习)
3. Lab10 (生存分析)

---

## 💡 提示

- 所有notebook都包含**中文注释**
- 代码可以直接运行（需要先安装依赖）
- 建议按顺序学习，先掌握基础再进行高级分析
- 遇到问题可查看 `Python_Notebooks_README.md` 获取更多信息

---

## 📊 进度追踪

- [x] Lab01: Python和Bash基础
- [x] Lab03: PCA和聚类
- [x] Lab04: 机器学习
- [x] Lab05: 基因组比对
- [x] Lab06: ATAC-seq
- [x] Lab08: 单细胞分析
- [x] Lab10: 生存分析
- [x] Lab11: CRISPR筛选

**状态**: ✅ 所有主要Lab已完成转换

---

祝学习愉快！🎉
