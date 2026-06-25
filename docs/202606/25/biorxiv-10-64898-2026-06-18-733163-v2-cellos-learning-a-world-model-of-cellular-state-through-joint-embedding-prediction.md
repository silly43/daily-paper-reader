---
title: "CellOS: Learning a World Model of Cellular State through Joint Embedding Prediction"
title_zh: "CellOS: 通过联合嵌入预测学习细胞状态的世界模型"
authors: "Zhou, Q., Le, Y., Qi, X., Chang, S., Lu, H., Wu, Y., Wang, H., Ran, R., li, x."
date: 2026-06-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733163v2.full.pdf"
tags: ["query:world-models"]
score: 9.0
evidence: 明确学习细胞状态的世界模型
tldr: 当前单细胞基础模型仅从单一基因表达视图学习，难以整合互补的细胞状态信息。CellOS提出多视图框架，通过因果细胞句子语言建模、密集到混合专家扩展和LLM-JEPA潜在空间对齐的三阶段策略，联合学习表达与感知视图。在3.905亿单细胞转录组上训练的12B参数模型，在细胞注释、批次整合和扰动响应预测等基准中均超越现有模型。结果表明，互补视图的预测对齐为构建可迁移的AI虚拟细胞提供了可扩展路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞基础模型仅利用单一基因表达视图，无法整合互补的细胞状态信息，限制了对细胞的全面理解。
method: 提出CellOS，包含因果细胞句子建模、密集到混合专家扩展和LLM-JEPA潜在空间对齐的三阶段多视图训练。
result: 在3.905亿单细胞转录组上训练12B参数模型，在细胞状态注释、批次整合和扰动响应预测等任务上超越当前最先进模型。
conclusion: 互补细胞视图的预测对齐为实现表示中心的细胞世界模型和可迁移AI虚拟细胞提供了可扩展方案。
---

## 摘要
从单细胞转录组学习的基础模型对于能够表示、查询和预测细胞状态的AI虚拟细胞的前景至关重要。然而，当前大多数单细胞基础模型从基因表达的单一视图学习，主要通过重建或下一个token预测进行优化。因此，它们捕捉表达丰度，但无法显式协调细胞状态的互补视图。这里我们提出CellOS，一个多视图基础模型，从配对表达和感知视图学习细胞表示。CellOS通过可扩展的三阶段训练策略整合互补视图，该策略结合了因果细胞语句语言建模、保持功能从密集到专家混合的扩展以及通过LLM-JEPA目标的潜在空间对齐。使用这个框架，我们在3.905亿个单细胞转录组上训练了一个120亿参数的模型。在跨越细胞状态注释、批次整合和扰动响应预测的多个基准测试中，CellOS持续优于最先进的单细胞基础模型。这些结果表明，互补细胞视图之间的预测对齐为以表示为中心的细胞世界模型和可迁移的AI虚拟细胞提供了一条可扩展的路径。

## Abstract
Foundation models learned from single-cell transcriptomes are central to the prospect of AI virtual cell that can represent, query and predict cellular state. However, most current single-cell foundation models learn from a single view of gene expression and are optimized primarily through reconstruction or next-token prediction. As a result, they capture expression abundance but can-not explicitly reconcile complementary views of cellular state. Here we present CellOS, a multi-view foundation model that learns cellular representations from paired expression and perception views. CellOS integrates complementary views through a scalable three-stage training strategy that combines causal cell-sentence language modelling, function-preserving dense-to-mixture-of-experts expansion and latent-space alignment via an LLM-JEPA objective. Using this framework, we trained a 12-billion-parameter model on 390.5 million single-cell transcriptomes. Across diverse benchmarks spanning cell-state annotation, batch integration and perturbation-response prediction, CellOS consistently outperformed state-of-the-art single-cell foundation models. Together, these results suggest that predictive alignment between complementary cellular views provides a scalable path toward representation-centric cellular world models and transferable AI virtual cells.

---

## 论文详细总结（自动生成）

# CellOS 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：当前大多数单细胞基础模型仅从基因表达的单一视图（如表达丰度）学习，优化目标主要是重建表达值或预测下一个基因 token。这种方法虽然能捕获细胞内的表达丰度模式，但无法显式整合互补的细胞状态视图——例如哪些基因的表达值在统计上最“意外”或最具信息量。这限制了对细胞状态的全面、鲁棒表示，尤其在稀有状态、扰动响应等情境下。
- **整体含义**：论文指出，一个理想的 AI 虚拟细胞应能表示、查询和预测细胞状态，这要求模型学习到超越简单丰度排序的、具有跨视图一致性的潜在表示。作者提出 CellOS，将单细胞转录组表示为互补的表达视图和感知视图，并通过联合嵌入预测（JEPA）对齐它们，从而以可扩展的方式构建以表示为中心的细胞世界模型。

## 2. 论文提出的方法论

### 核心思想
- 为每个细胞构建两种视图的基因序列：
  - **表达视图**：基因按归一化表达丰度降序排列的句子。
  - **感知视图**：基因按**人口相对偶然性**（population-relative surprisal）降序排列的句子。对于基因 $g$ 和细胞 $c$，感知信息分数定义为：
    $$I_{cg} = -\log(1 - q_g(e_{cg}) + \epsilon)$$
    其中 $e_{cg}$ 是归一化表达，$q_g$ 是基因 $g$ 在训练语料中非零表达的经验分位数函数。该分数使落在基因自身分布上尾的低概率值获得高权重。
- 通过三阶段训练整合两视图：
  1. **阶段 1**：在表达视图上训练因果语言模型（自回归预测基因 token）。
  2. **阶段 2**：将训练好的密集 Transformer 通过**功能保持的密集到 MoE（mixture-of-experts）转换**扩展为稀疏模型：一个共享专家（用原密集权重初始化）+ 32 个路由专家（近零初始化），继续预训练。
  3. **阶段 3**：引入感知视图，使用 **LLM-JEPA 目标**对齐两视图的细胞级表示。对齐损失为余弦距离：
     $$L_{\text{JEPA}} = 1 - \cos(\hat{z}_c^{\text{perc}}, z_c^{\text{perc}})$$
     其中 $\hat{z}_c^{\text{perc}}$ 是从表达视图表示通过一个小预测器 $q_\phi$ 得到的预测，$z_c^{\text{perc}}$ 是感知视图的表示。

### 关键技术细节
- **数据预处理**：统一基因符号，库大小归一化 $e_{cg} = 10^4 \cdot x_{cg} / \sum_g x_{cg}$。
- **模型架构**：共享解码器因果 Transformer，添加专门的代表 token 用于细胞级嵌入。
- **总训练目标**：
  $$L = \lambda_{\text{LM}} L_{\text{LM}} + \lambda_{\text{JEPA}} L_{\text{JEPA}} + \lambda_{\text{MoE}} L_{\text{aux}}$$
  三阶段逐步引入各损失项。
- **无重建要求**：JEPA 对齐在潜在空间进行，不要求两个视图的 token 位置匹配，从而强制模型学习跨视图不变的结构。

## 3. 实验设计

### 数据集与场景
- **标注基准（6个数据集）**：
  - PBMC 免疫衰老（13 细胞类型）
  - iPSC 细胞类型分化（25 分化状态）
  - iPSC 分化时间过程（4 天时间点）
  - T 细胞亚簇（16 个精细亚型）
  - 人类肺（16 细胞类型）
  - IFN-β 刺激 PBMC（13 聚类）
- **批次整合基准（2个数据集）**：
  - 人类肺（107 个测序文库）
  - 周仁皮质（2 个样本）
- **扰动响应预测基准**：采用 STATE 框架的 5 个 held-out 细胞上下文（H1, HepG2, Jurkat, K562, RPE1），输入不同基础模型嵌入，保持下游过渡模型和评估协议一致。

### 对比方法
- UCE, State, scGPT, TranscriptFormer, STACK, C2S-2B（C2S-Scale）
- 消融分析对比 CellOS-0.2B、CellOS-2B（单视图）与 CellOS-12B（MoE + JEPA）。

### 评估指标
- **标注**：ARI、NMI、ASW，聚合为生物保守性分数。
- **批次整合**：sil_batch、图连通性（GC）、iLISI，聚合为批次效应分数。
- **扰动预测**：DE Spearman、Pearson edist、聚类一致性、DE 方向匹配。

## 4. 资源与算力
- 论文中未明确说明训练 CellOS 12B 模型所使用的 GPU 型号、数量及训练时长等具体算力资源信息。仅在描述中提及在 390.5M 单细胞转录组上训练了 12B 参数模型，但硬件细节未披露。

## 5. 实验数量与充分性
- **实验数量**：覆盖三大类任务（标注、批次整合、扰动预测）共 8 个以上数据集，并与 6 种现有方法全面比较。此外包括针对规模和 JEPA 的对齐消融分析。
- **充分性与公平性**：
  - 标注和批次整合使用统一处理流程和标准化指标，消融研究直接比较同一骨干的不同规模/阶段。
  - 扰动预测实验严格保证了“仅嵌入不同”，下游模型、训练协议、评估完全一致，隔离了表示质量的影响。
  - 实验设计较为充分和公平，但可考虑增加更多跨平台/跨物种泛化测试。扰动预测仅使用 STATE 框架的一种设置，可能遗漏其他范式。

## 6. 论文的主要结论与发现

- CellOS 在标注基准上取得最高聚合生物保守性分数（0.792），ARI、NMI、ASW 均领先。
- 批次整合方面达到强 GC（0.964）和良好批次效应分数（0.771），优于多数模型，且生物保守性远高于 mixing 最好的 STACK（0.792 vs 0.474），说明 CellOS 避免了过整合。
- 在扰动响应预测中，CellOS 在 DE Spearman（0.590）、Pearson edist（0.619）、聚类一致性（0.633）上均排名第一，显著优于最佳竞争者（如 TranscriptFormer、UCE），表明其表示在状态变化下仍保持信息量。
- 规模扩展（0.2B → 2B → 12B）和多视图 JEPA 对齐均带来持续提升，尤其在精细 T 细胞亚型标注上 ARI 提升 36%。
- 总结：互补细胞视图的预测对齐为构建可迁移的、以表示为中心的 AI 虚拟细胞提供了可扩展的有效路径。

## 7. 优点

- **方法论创新**：首次将 JEPA 思想引入单细胞转录组学，并且使用生物学定义的视图（表达 vs 感知）而非通用数据增广，具有领域 specificity。
- **三阶段训练策略稳定可靠**：先学 dense 语言模型，再通过功能保持的 MoE 扩展容量，最后加入 JEPA 对齐，避免不稳定性并保留已有知识。
- **可扩展性强**：MoE 架构使模型参数达到 12B，同时保持计算效率，论文展示了参数规模与性能的正相关关系。
- **实验设计严谨**：扰动预测中固定下游模型仅比较表示质量；消融分析明确分离了规模和多视图对齐的影响；多个 benchmark 覆盖不同任务和粒度。
- **表现全面优异**：在标注、整合、预测三类任务上均达到最佳或接近最佳，且无过度优化特定指标。

## 8. 不足与局限

- **感知视图定义相对简单**：当前使用全训练语料的基因级经验分位数，未考虑组织、谱系或条件特异性背景，可能限制对高度依赖背景的信号（如组织特异性转录因子）的编码。
- **仅使用转录组数据**：未整合染色质可及性、蛋白质丰度、空间位置或扰动直接读数等模态，限制了多模态世界模型的能力。
- **非因果世界模型**：CellOS 的表示改善了扰动预测，但模型本身并未直接预训练于扰动轨迹或时间过程，无法直接模拟细胞动态或因果干预。
- **算力信息缺失**：未提供训练资源细节（如 GPU 型号/数量/时长），降低了可复现性和透明度。
- **扰动预测范围有限**：仅测试了 5 个细胞上下文和一种下游框架，未检验在更多扰动类型（如化合物、环境应激）和更大规模 Perturb-seq 数据上的泛化能力。
- **可能存在 bias**：训练数据主要来自公开数据库，可能对某些组织或疾病状态存在过度/不足表示，影响模型公平性。

（完）
