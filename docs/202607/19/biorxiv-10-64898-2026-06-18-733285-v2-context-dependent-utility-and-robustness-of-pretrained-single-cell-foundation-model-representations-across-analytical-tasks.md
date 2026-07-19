---
title: Context-dependent utility and robustness of pretrained single-cell foundation model representations across analytical tasks
title_zh: 预训练单细胞基础模型表示在不同分析任务中的上下文相关效用与鲁棒性
authors: "Liu, T., Feng, T., Pan, X., Chen, Y., Ren, L., Ye, X., Lin, H., Zhang, Y."
date: 2026-07-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733285v2.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 评估预训练单细胞基础模型表示的零样本性能，这些模型是自监督学习的
tldr: 单细胞基础模型在零样本任务中性能依赖任务类型和数据集结构。研究评估了20种方法、6个任务和1607个数据集，发现高性能不等于鲁棒性，传统方法在某些场景仍有竞争力。模型对细胞/基因数量、类别不平衡等扰动敏感。结果强调需根据具体任务选择表示，并兼顾实用性和结构鲁棒性。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-18-733285-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 1416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-18-733285-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 1902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-18-733285-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 1961, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-18-733285-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 1943, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-18-733285-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1441, \"height\": 2040, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-18-733285-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1429, \"height\": 1737, \"label\": \"Figure\"}]"
motivation: 系统评估单细胞基础模型零样本表示在不同分析任务和数据结构条件下的实用性与鲁棒性。
method: 分析20种表示方法在6个下游任务、1607个数据集上的零样本性能，并考察对结构扰动的鲁棒性。
result: 任务间性能差异大，无统一最优；高实用性不代表高鲁棒性；传统方法仍有竞争力；计算成本与性能不必然正比。
conclusion: 零样本效用和鲁棒性取决于任务和数据结构，选择表示需结合上下文，并重视结构鲁棒性评估。
---

## 摘要
单细胞基础模型已成为单细胞转录组学中强大的表示学习方法。然而，其预训练表示在不同分析任务和数据条件下的效用与鲁棒性仍未被充分表征，尤其是在无需任务特定微调的零样本设置中。本研究系统分析了跨越20种方法、6个下游任务以及包含近2180万个细胞的1607个数据集的单细胞转录组表示的零样本性能。我们从三个互补维度评估模型行为：原始数据集上的效用、对数据集结构受控变化的鲁棒性，以及数据集特征与性能变化之间的探索性关联。结果表明，scFM的性能强烈依赖于任务，没有任何一种方法在细胞级和基因级分析中始终优于其他方法。值得注意的是，原始数据集上的高效用并不一定能转化为结构扰动下的鲁棒性，几种排名靠前的方法对细胞数量、基因数量、类别构成、类别不平衡和批次复杂性的变化敏感。传统的统计方法和任务特定方法在若干设定中仍具有竞争力，而更高的计算成本并不始终对应更好的性能。驱动分析进一步确定了性能与数据集特征之间的任务特定关联，包括细胞类型复杂度、训练-测试类别重叠、批次数量和调控目标集大小。综合这些发现表明，预训练scFM表示的零样本效用和鲁棒性共同取决于分析任务和数据集结构。本研究为上下文感知的表示选择提供了实践基础，并强调了在开发和应用scFM时评估结构鲁棒性与效用并重的重要性。

## Abstract
Single-cell foundation models (scFMs) have emerged as powerful representation learning approaches for single-cell transcriptomics. However, the utility and robustness of their pretrained representations across diverse analytical tasks and data conditions remain insufficiently characterized, particularly in zero-shot settings without task-specific fine-tuning. Here, we systematically analyze zero-shot performance of single-cell transcriptomic representations across 20 methods, 6 downstream tasks and 1,607 datasets comprising nearly 21.8 million cells. We evaluate model behavior along three complementary dimensions: utility on original datasets, robustness to controlled changes in dataset structure, and exploratory associations between dataset characteristics and performance variation. Our results show that scFM performance is strongly task dependent, with no single method consistently outperforming others across cell- and gene-level analyses. Notably, high utility on original datasets did not necessarily translate into robustness under structural perturbations, and several top-ranking methods were sensitive to changes in cell number, gene number, class composition, class imbalance, and batch complexity. Conventional statistical and task-specific methods remained competitive in several settings, while greater computational cost did not consistently correspond to better performance. Driver analyses further identified task-specific associations between performance and dataset characteristics, including cell-type complexity, train-test class overlap, batch number, and regulatory target-set size. Together, these findings show that the zero-shot utility and robustness of pretrained scFM representations depend jointly on analytical task and dataset structure. Our study provides a practical basis for context-aware representation selection and underscores the importance of evaluating structural robustness alongside utility when developing and applying scFMs.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

单细胞转录组学数据持续快速增长，催生了一系列大规模单细胞基础模型（Single-cell Foundation Models, scFMs）。这些模型通过在大规模无标签数据上预训练，旨在学习可泛化的细胞嵌入（cell embeddings）和基因嵌入（gene embeddings），并宣称能够**零样本（zero-shot）** 直接服务于下游分析任务，而无需针对每个任务进行微调。然而，目前领域内对 scFM 在真实分析场景下的实际效用和鲁棒性认知不足：不同任务（如聚类、注释、基因调控推断）对表示的偏好尚不明确；零样本部署下，表示对数据集结构变化（细胞数量、基因数量、类别组成等）的敏感程度缺乏系统评估；传统简单基线（如 PCA、高度可变基因）是否仍具竞争力也鲜有定量比较。因此，本研究的核心问题是：**scFM 的零样本表示在不同分析任务和数据集条件下是否真正提供稳定且可复现的优势，抑或仅在小范围固定基准上表现亮眼？** 这一问题的回答对于引导社区合理选择表示、评估模型声称的泛化能力具有重要意义。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

**核心思想**：构建一个结构化的评估框架，从**效用**、**鲁棒性**和**驱动因素**三个维度量化 scFM 表示的零样本表现。效用指在原始数据集上的基线性能；鲁棒性指在数据集结构受控扰动条件下的性能偏差；驱动因素通过回归模型探索数据集级特征与性能之间的关联。

**关键技术细节**：
- 所有表示均在零样本下提取（冻结预训练权重，无下游任务微调）。
- 对于每个任务，使用统一的下游管道（统一分类器、统一聚类流程）以确保比较公平性。
- 鲁棒性评估：对每个原始数据集生成多组结构扰动版本（如比例基因/细胞采样、移除细胞类型/批次等），计算每对扰动-原始的性能绝对偏差 $\delta_{m,p} = |\text{perf}_{m,p} - \text{perf}_{m,\text{orig}}|$，并在所有扰动实例上对方法进行排名。
- 效用和鲁棒性均采用**基于排名的聚合**：在每个数据集中对方法按指标值排名，再对所有数据集取平均排名，跨指标再平均得到综合排名。这种尺度不变的方式避免了不同数据集指标数值范围差异带来的偏差。
- 驱动分析（Drivers）：对每个方法-指标对，先使用弹性网络回归（Elastic Net, $\alpha=0.5$）从数据集特征中筛选变量，再对选中的特征用标准化后的普通最小二乘回归（OLS）估计标准化系数，仅保留 $R^2 > 0.1$ 的模型进行展示。该分析旨在识别与性能显著关联的数据结构特征（如细胞类型数量、批次数量、类别重叠比例等），而非因果推断。

**算法流程**（文字说明）：
1. 输入单细胞表达矩阵。
2. 通过预训练 scFM 提取零样本表示（细胞嵌入、基因嵌入或注意力分数）。
3. 对每个下游任务，在原始数据集上运行统一管道，记录效用指标（如 ARI、F1、AUROC 等）。
4. 对每个原始数据集，生成多种结构扰动（基因/细胞/类别/批次扰动），对每个扰动版本重复步骤 3，记录偏差 $\delta$。
5. 统计排名：对每个指标，按原始性能排名得效用排名，按偏差大小反向排名得鲁棒性排名；跨指标汇总得到综合效用与综合鲁棒性。
6. 将各方法映射到二维效用-鲁棒性图，使用不对称阈值（效用前 25%，鲁棒性中位数以上）或对称阈值识别偏好区域。
7. 对每个方法-指标对，运行驱动分析：弹性网络特征选择 → OLS 回归 → 报告标准化系数。

### 3. 实验设计：使用了哪些数据集 / 场景，benchmark 是什么，对比了哪些方法

**数据集与场景**：
- **细胞聚类**（无监督）：Tabula Sapiens 2.0 组织子集（26 个数据集，共 541,276 细胞）。
- **细胞类型注释**（有监督）：同上，按细胞类型分层 5 折交叉验证。
- **药物敏感性预测**（表型预测）：14 个单细胞药物响应数据集（来自 DRMref，93,481 细胞），二分类任务（耐药 vs 非耐药）。
- **批次整合**（无监督整合）：7 个代表性多技术平台单细胞数据集（105,750 细胞），评估生物保存（ARI, NMI, ASW）和批次混合（iLISI, kBET, batch ASW）。
- **基因功能预测**（有监督）：HPA 数据库中 1,797 个组织特异性基因，15 类单标签多分类任务；仅测试显式提供基因嵌入的 12 个模型+1 个 one-hot 基线。
- **基因调控网络推断（GRN）**：17 个扰动 scRNA-seq 数据集（9,096 细胞），通过表达响应 + 基序支持双重证据定义高置信度 TF-靶标关系；提取注意力矩阵或基因嵌入余弦相似度作为关联矩阵。

**Benchmark 方法**：总计 20 种，包括多个 scFM 变体：
- **scFM 类**：scFoundation, UCE (4L/33L), SCimilarity, CellPLM, CellFM (min/base), scGPT, Geneformer (6L/12L), GeneCompass, GenePT (min/large), tGPT, scBERT (CLS/Mean)。
- **传统统计基线**：PCA (top 50 PCs), highVariable (top 2000 HVG), Harmony（批次整合基线）, Cosine 相似度（GRN 基线）。
- **其他深度学习基线**：scGNN（自监督图表示）, one-hot（基因功能基线）。

**总共实验规模**：6 个任务，1,607 个数据集（含扰动），近 2,180 万细胞。其中原始数据集用于效用评估，扰动数据集用于鲁棒性评估（如聚类有 26 原始 + 339 扰动，批次整合有 7 原始 + 325 扰动等）。

### 4. 资源与算力

论文在“Computational resources”节中明确说明：
- 硬件：Linux 服务器，Ubuntu 22.04.5 LTS，AMD 32 核 CPU，503 GB 系统内存，单块 NVIDIA A100 PCIe GPU (40 GB)，CUDA 12.2。
- 仅统计了零样本表示提取阶段的耗时（细胞嵌入和基因关联矩阵），未报告训练硬件或总 GPU 小时数。各方法的运行时间从 1-2 分钟到超过 30 分钟不等，内存占用差异大（详见补充表 S2）。
- 计算成本**不直接对应于预测效用**——高计算开销的方法未必性能更好。

### 5. 实验数量与充分性

- **实验规模**：6 个任务，每个任务包含数十到数百个数据集（原始+扰动）。总数据集 1,607 个，覆盖多种常见单细胞分析场景。
- **扰动设计**：对每个任务定制了合理的扰动类型（基因/细胞/类别/批次/不平衡等），确保鲁棒性评估的全面性。
- **统计检验**：在效用和鲁棒性对比中都采用了配对 Wilcoxon 符号秩检验，并控制 FDR（BH 校正），报告中位数效应量，增强了结果统计严谨性。
- **消融/变体**：对多个模型（UCE、Geneformer、GenePT、CellFM、scBERT）测试了不同检查点或表示聚合策略，视作独立方法。
- **局限性**：所有下游分类器统一且未调优，不代表每类表示的最佳微调性能；扰动仅覆盖部分结构性属性（如未包含测序技术差异、批次效应异质性等）；驱动分析是关联而非因果。总体而言，实验设计公平、充分，但未覆盖所有潜在变异性，属于有边界但扎实的系统基准。

### 6. 论文的主要结论与发现

1. **强任务依赖性**：无单一 scFM 在所有任务上始终最优；不同任务偏好不同的表示（例如聚类中 UCE4L、CellPLM 较好；注释中 scFoundation 最优；基因功能 GeneCompass 最优）。
2. **效用与鲁棒性可解耦**：高效用的方法在结构扰动下可能脆弱（如 SCimilarity 在聚类中效用高但鲁棒性不足；Harmony 在批次整合中效用最高但鲁棒性偏弱）。联合效用-鲁棒性图揭示了更全面的方法选择空间。
3. **传统基线仍有竞争力**：highVariable 在注释和药物预测中表现突出；Harmony 在批次整合中排名第一；Cosine 相似性在 GRN 推断中匹敌甚至优于部分深度模型。大规模预训练并非在零样本下总是优于简单统计方法。
4. **计算成本不决定性能**：计算资源消耗大的模型未必获得更好结果，实际选型需考虑资源-性能权衡。
5. **关键驱动特征**：监督任务中，训练-测试类别重叠比例、批次整合中批次数量、GRN 中目标集大小是与性能关联最强的数据集级特征。这些特征可作为未来模型压力测试的参考轴。
6. **对社区的建议**：在报告新 scFM 时应提供效用、鲁棒性和资源三方面比较；在应用中选择表示时应结合具体任务和数据结构特点，而非单一排名。

### 7. 优点

- **系统性与规模**：覆盖 20 种方法、6 个任务、1607 个数据集，是目前最全面的零样本 scFM 基准之一。
- **结构扰动方法论**：引入受控扰动体系评估鲁棒性，超越了传统的单一固定基准评估，揭示了表示在真实变异下的稳定性。
- **统一下游管道**：所有方法使用相同分类器/聚类流程，避免因下游设计不同导致的偏差；零样本提取严格隔离。
- **基于排名的聚合**：采用跨数据集排名再平均的方式，鲁棒于不同指标量纲和分布。
- **统计严谨**：配对检验 + FDR 控制，报告效应量；驱动分析结合弹性网络选择 + OLS，控制多重共线性。
- **实用导向**：提供了“效用-鲁棒性”二维决策图，有助于研究人员根据自身数据条件（是否稳定、是否有资源）进行表示选择。

### 8. 不足与局限

- **缺乏微调**：刻意避免微调，只能反映冻结预训练表示的天花板，无法评估通过微调可达到的最佳性能。对于实际中愿意微调的用户，结果未必适用。
- **扰动覆盖有限**：仅针对细胞/基因/类别/批次数量等结构属性进行了系统扰动，未涵盖如测序深度差异、批次效应异质性、多种数据源混合等现实噪声。
- **驱动分析为关联性**：弹性网络 + OLS 回归发现的关联不代表因果关系，可能存在混杂变量（如细胞类型数量与批次数量之间的相关性）。
- **基因级任务排除模型**：无法提供显式基因嵌入或基因-基因关系的模型（如 CellPLM、SCimilarity）被排除在基因功能与 GRN 任务之外，导致这些任务的比较范围受限。
- **单细胞类型层次**：所有评估基于预定义的细胞类型标签，未测试细粒度亚群或连续状态。
- **药物预测任务二值化处理**：将药物响应简单二值化为耐药/非耐药，可能丢失部分信息，影响模型区分类别的能力。
- **可重复性资源有限**：所有计算在一张 A100 上完成，但数据/代码仍有公开；对于大规模零样本提取的运行时内存需求，文中未给出所有模型的具体峰值。

（完）
