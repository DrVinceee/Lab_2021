# Python Jupyter Notebooks - R Markdown转换说明

## 概述

本仓库原本使用R语言和R Markdown（.Rmd）文件。为了方便使用Python的用户，我们将所有实验内容转换为Jupyter Notebook（.ipynb）格式，并使用Python代码实现。

## 文件对应关系

| 原R Markdown文件 | Python Notebook | 主要内容 |
|-----------------|-----------------|---------|
| `Lab01/lab1.rmd` | `Lab01/lab1.ipynb` | Python基础、Pandas数据操作、可视化、Bash脚本 |
| `Lab03/Lab3.Rmd` | `Lab03/Lab3.ipynb` | PCA、K-Means、层次聚类、批次效应、差异表达分析、GSEA |
| `Lab04/Lab4.Rmd` | `Lab04/Lab4.ipynb` | 机器学习算法（KNN、线性回归、逻辑回归、SVM、随机森林） |
| `Lab05/2021_Lab5.Rmd` | `Lab05/Lab5.ipynb` | BWA比对、MACS2峰调用（主要为命令行工具） |
| `Lab06/Lab6.Rmd` | `Lab06/Lab6.ipynb` | ATAC-seq分析、LISA转录因子预测 |
| `Lab08/pbmc3k_tutorial.Rmd` | `Lab08/Lab8.ipynb` | 单细胞RNA-seq分析（Scanpy替代Seurat） |
| `Lab10/HW6_lab10_sample_code.Rmd` | `Lab10/Lab10.ipynb` | 生存分析（lifelines库） |
| `Lab11/HW6_lab12_sample_code.Rmd` | `Lab11/Lab11.ipynb` | CRISPR筛选分析（MAGeCK） |

## R包到Python包的映射

### 数据处理
- **dplyr** (R) → **pandas** (Python)
  - `filter()` → `df[df['col'] > value]` 或 `df.query()`
  - `select()` → `df[['col1', 'col2']]`
  - `mutate()` → `df['new_col'] = ...`
  - `group_by() %>% summarize()` → `df.groupby().agg()`
  - `%>%` (管道) → 方法链 `.method1().method2()`

### 可视化
- **ggplot2** (R) → **matplotlib + seaborn** (Python)
  - `ggplot() + geom_*()` → `plt.plot()` 或 `sns.scatterplot()`
  - `facet_wrap()` → `plt.subplot()` 或 `sns.FacetGrid()`

### 机器学习
- **caret** (R) → **scikit-learn** (Python)
  - `train()` → 各种模型的`.fit()`方法
  - `trainControl()` → `cross_val_score()`, `GridSearchCV()`
  - `confusionMatrix()` → `confusion_matrix()`, `classification_report()`

### 统计和生物信息学
- **survival** (R) → **lifelines** (Python)
  - `Surv()` → `lifelines.utils.Surv()`
  - `survfit()` → `KaplanMeierFitter()`
  - `coxph()` → `CoxPHFitter()`

- **DESeq2** (R) → **pyDESeq2** (Python) 或使用 **rpy2** 调用R
  - `DESeqDataSetFromMatrix()` → `DeseqDataSet()`
  - `DESeq()` → `deseq2()`
  - `results()` → `.results_df`

- **Seurat** (R) → **scanpy** (Python)
  - `CreateSeuratObject()` → `sc.AnnData()`
  - `NormalizeData()` → `sc.pp.normalize_total()` + `sc.pp.log1p()`
  - `FindVariableFeatures()` → `sc.pp.highly_variable_genes()`
  - `RunPCA()` → `sc.tl.pca()`
  - `FindClusters()` → `sc.tl.leiden()` 或 `sc.tl.louvain()`
  - `RunUMAP()` → `sc.tl.umap()`

### 生物信息学命令行工具
以下工具主要通过命令行使用，Python可用于结果分析：
- **BWA** - 序列比对
- **MACS2** - ChIP-seq峰调用
- **BEDTools** - 基因组区间操作（可使用 **pybedtools** Python包装）
- **MAGeCK** - CRISPR筛选分析
- **LISA** - 转录因子预测

## 安装所需Python包

### 核心包
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 机器学习
```bash
pip install scikit-learn scipy statsmodels
```

### 生物信息学
```bash
# 单细胞分析
pip install scanpy

# 生存分析
pip install lifelines

# 差异表达分析
pip install pydeseq2

# 基因富集分析
pip install gseapy

# BEDTools Python接口
pip install pybedtools

# R包调用（可选）
pip install rpy2
```

## 使用说明

### 1. 启动Jupyter Notebook
```bash
cd /path/to/Lab_2021
jupyter notebook
```

### 2. 打开相应的实验notebook
在Jupyter界面中，导航到对应的Lab文件夹，打开`.ipynb`文件。

### 3. 运行代码单元格
- 按 `Shift + Enter` 运行当前单元格
- 按 `Cell → Run All` 运行所有单元格

### 4. 修改和实验
所有代码都可以修改和调整。鼓励您：
- 更改参数观察结果变化
- 尝试不同的数据集
- 添加您自己的分析

## 注意事项

### 1. 数据文件
- 部分notebook需要数据文件，这些文件可能在原Lab文件夹中
- 某些数据集可以从Python包中加载（如sklearn、seaborn的内置数据集）
- 大型数据集可能需要从外部下载

### 2. 计算资源
- 某些分析（如单细胞分析、大规模机器学习）可能需要较多内存
- 建议在开始前检查数据大小和可用资源

### 3. R包的使用
对于某些没有直接Python替代品的R包，可以使用`rpy2`：

```python
import rpy2.robjects as ro
from rpy2.robjects.packages import importr

# 导入R包
deseq2 = importr('DESeq2')

# 使用R函数
# ...
```

### 4. 中文支持
notebook中的注释和文档使用中文。如果显示出现问题，请确保：
- Jupyter支持UTF-8编码
- 系统安装了中文字体
- matplotlib配置了中文字体（已在代码中设置）

## 学习路径建议

### 初学者
1. **Lab01**: Python基础和数据操作
2. **Lab03**: 数据分析和可视化基础
3. **Lab04**: 机器学习入门

### 生物信息学分析
1. **Lab05/Lab06**: 基因组学数据分析
2. **Lab08**: 单细胞RNA-seq分析
3. **Lab10**: 生存分析

### 高级分析
1. **Lab03**: 批次效应和差异表达
2. **Lab04**: 高级机器学习模型
3. **Lab11**: CRISPR筛选分析

## 资源链接

### Python学习资源
- [Python官方教程](https://docs.python.org/3/tutorial/)
- [Pandas文档](https://pandas.pydata.org/docs/)
- [Scikit-learn教程](https://scikit-learn.org/stable/tutorial/)

### 生物信息学资源
- [Scanpy教程](https://scanpy-tutorials.readthedocs.io/)
- [Lifelines文档](https://lifelines.readthedocs.io/)
- [GSEApy文档](https://gseapy.readthedocs.io/)

### Jupyter使用
- [Jupyter Notebook文档](https://jupyter-notebook.readthedocs.io/)
- [JupyterLab](https://jupyterlab.readthedocs.io/)

## 反馈和贡献

如果您发现错误或有改进建议，欢迎：
- 提交Issue
- 创建Pull Request
- 与课程助教联系

## 许可证

本转换保持原仓库的许可证。所有代码仅用于教育目的。

---

**更新日期**: 2024  
**维护者**: Lab_2021 Python转换项目组

祝学习愉快！🎓
