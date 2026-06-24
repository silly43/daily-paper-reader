---
title: "CellOS: Learning a World Model of Cellular State through Joint Embedding Prediction"
title_zh: CellOS：通过联合嵌入预测学习细胞状态的世界模型
authors: "Zhou, Q., Le, Y., Qi, X., Chang, S., Lu, H., Wu, Y., Wang, H., Ran, R., li, x."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733163v1.full.pdf"
tags: ["query:world-models"]
score: 10.0
evidence: 明确学习细胞状态的世界模型
tldr: 单细胞转录组基础模型多为单一视图，无法整合互补信息。CellOS提出多视图框架，通过三阶段训练（因果语言建模、Dense-to-MoE扩展、LLM-JEPA对齐）学习配对表达与感知表征。在3.9亿细胞上训练的120亿参数模型在细胞注释和扰动预测上超越现有方法，并保持批次整合能力。该工作为构建表示中心的细胞世界模型和AI虚拟细胞提供了可扩展路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞基础模型仅从单一基因表达视图学习，不能显式整合互补的细胞状态视图。
method: 提出三阶段训练策略：因果细胞句子语言建模、功能保留的Dense-to-MoE扩展、基于LLM-JEPA的潜在空间对齐。
result: 在3.9亿细胞上训练的120亿参数模型在细胞注释和扰动预测上超越SOTA，同时稳健处理批次整合。
conclusion: 互补视图间的预测对齐为构建可转移的表示中心细胞世界模型提供了可扩展路径。
---

## 摘要
基于单细胞转录组学习的基础模型对于能够表示、查询和预测细胞状态的AI虚拟细胞前景至关重要。然而，当前大多数单细胞基础模型从单一视角的基因表达中学习，主要通过重构或下一个词元预测进行优化。因此，它们捕获表达丰度，但无法显式协调细胞状态的互补视角。在这里，我们提出CellOS，一个多视角基础模型，从配对的表达和感知视角学习细胞表示。CellOS通过一个可扩展的三阶段训练策略整合互补视角，该策略结合了因果细胞句子语言建模、功能保持的密集到混合专家扩展以及通过LLM-JEPA目标的潜在空间对齐。利用这一框架，我们在3.905亿个单细胞转录组上训练了一个120亿参数的模型。在跨细胞状态注释、批次整合和扰动响应预测的多样基准测试中，CellOS在细胞状态注释和扰动响应预测方面一致优于最先进的单细胞基础模型，同时保持了稳健的批次整合能力。这些结果共同表明，互补细胞视图之间的预测对齐为以表示为中心的细胞世界模型和可迁移的AI虚拟细胞提供了一条可扩展的路径。

## Abstract
Foundation models learned from single-cell transcriptomes are central to the prospect of AI virtual cell that can represent, query and predict cellular state. However, most current single-cell foundation models learn from a single view of gene expression and are optimized primarily through reconstruction or next-token prediction. As a result, they capture expression abundance but can-not explicitly reconcile complementary views of cellular state. Here we present CellOS, a multi-view foundation model that learns cellular representations from paired expression and perception views. CellOS integrates complementary views through a scalable three-stage training strategy that combines causal cell-sentence language modelling, function-preserving dense-to-mixture-of-experts expansion and latent-space alignment via an LLM-JEPA objective. Using this framework, we trained a 12-billion-parameter model on 390.5 million single-cell transcriptomes. Across diverse benchmarks spanning cell-state annotation, batch integration and perturbation-response prediction, CellOS consistently outperformed state-of-the-art single-cell foundation models in cell-state annotation and perturbation-response prediction while preserving robust batch integration. Together, these results suggest that predictive alignment between complementary cellular views provides a scalable path toward representation-centric cellular world models and transferable AI virtual cells.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

单细胞 RNA 测序（scRNA-seq）能够以转录组尺度测量细胞状态，积累了数亿个细胞图谱（如 Human Cell Atlas、CZ CELLxGENE）。这促使了单细胞基础模型的发展，旨在学习细胞状态的组织规则并用于预测新状态。然而，现有的单细胞基础模型（如 Geneformer、scGPT、TranscriptFormer 等）大多仅从 **单一视图（expression view）** 学习：它们将每个细胞表示为基因按表达丰度排序的“细胞句子”，并通过重建（masked token prediction）或下一个词元预测（next-token prediction）进行优化。这种范式存在两个根本局限：

- **表达量并不等于生物学信息性**：高表达基因（如看家基因）可能携带较少状态特异性信号，而中等表达的转录因子或应激响应基因若在全局分布中罕见则更具诊断信息。现有模型无法显式分离丰度与群体层面的信息含量。
- **输入空间目标消耗容量**：模型花费大量参数重建词元或计数值，而非学习鲁棒的细胞级表示。在视觉和语言领域，联合嵌入预测架构（JEPA）通过潜在空间预测强调语义结构，但尚未引入单细胞转录组学。

CellOS 提出 **多视图基础模型**，将每个细胞表示为配对的 **表达视图（expression view）** 和 **感知视图（perception view）**，并通过 LLM-JEPA 目标对齐两个视图的潜在表示，同时保留因果语言建模信号。该工作旨在迈向 **表示中心的细胞世界模型** 和可迁移的 AI 虚拟细胞。

---

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 使用 **双视图细胞句子**：表达视图按归一化表达丰度排序；感知视图按群体相对信息含量（surprisal）排序，后者基于每个基因在预训练语料中的经验分布计算上尾分位数。
- 采用 **三阶段训练策略**：1）密集因果语言模型预训练；2）功能保留的密集到混合专家（Dense-to-MoE）扩展；3）引入 LLM-JEPA 目标进行跨视图潜在空间对齐。

### 关键技术细节
#### 3.3 表达视图（Expression View）
- 对细胞 c，将基因按归一化表达 $e_{cg}$ 降序排列：$e_{c,g^{(1)}} \ge e_{c,g^{(2)}} \ge \dots \ge e_{c,g^{(n)}}$，形成句子 $S_c^{\text{expr}} = (g^{(1)}, g^{(2)}, \dots, g^{(n)})$。
- 归一化使用库大小缩放：$e_{cg} = 10^4 \cdot x_{cg} / \sum_g x_{cg}$。

#### 3.4 感知视图（Perception View）
- 对每个基因 g，从预训练语料的非零归一化表达中估计经验分位数函数 $q_g(\cdot)$。
- 定义感知信息分数（upper-tail quantile surprisal）：
  $$I_{cg} = -\log(1 - q_g(e_{cg}) + \epsilon)$$
  其中 $\epsilon$ 是小常数。分数越高表示该表达值在该基因自身分布中位于异常高的尾端。
- 按 $I_{cg}$ 降序排列基因得到感知句子 $S_c^{\text{perc}}$。

#### 3.5 模型架构
- 共享的 **decoder-only 因果 Transformer** $f_\theta$，处理两种句子。
- 每个句子附加一个专用表示词元（如 `<cls>`），其最终隐藏状态作为细胞表示 $z_c^{\text{expr}}$ 和 $z_c^{\text{perc}}$。
- **LLM-JEPA 跨视图预测**：使用预测网络 $q_\phi$ 将表达视图表示映射到感知视图潜在空间：
  $$\hat{z}_c^{\text{perc}} = q_\phi(z_c^{\text{expr}})$$
  对齐损失为余弦距离：
  $$L_{\text{JEPA}} = 1 - \cos(\hat{z}_c^{\text{perc}}, z_c^{\text{perc}})$$
- **MoE 扩展**：将密集 Transformer 的部分前馈层替换为包含 1 个共享专家和 32 个路由专家的 MoE 子层，使用 top-1 路由。初始化保持功能不变：共享专家继承原密集权重，路由专家接近零，路由器接近均匀。

#### 3.6 训练目标
三阶段对应目标：
- **Stage 1**：仅 $L_{\text{LM}}$（标准自回归交叉熵损失）。
- **Stage 2**：$L_{\text{LM}} + L_{\text{MoE}}$（MoE 辅助损失，如负载均衡损失）。
- **Stage 3**：$L = \lambda_{\text{LM}} L_{\text{LM}} + \lambda_{\text{JEPA}} L_{\text{JEPA}} + \lambda_{\text{MoE}} L_{\text{aux}}$

感知视图仅用于 JEPA 对齐，不作为语言建模输入。

---

## 3. 实验设计：使用了哪些数据集 / 场景，Benchmark，对比方法

### 数据集
- **细胞状态注释（6个数据集）**：
  - PBMC 免疫衰老（29,669 细胞，13 种类型）
  - iPSC 细胞型分化（9,029 细胞，25 种状态）
  - iPSC 分化时间序列（36,044 细胞，4 个时间点）
  - T 细胞亚聚类（14,260 细胞，16 个亚群）
  - 人类肺（46,091 细胞，16 种类型）
  - IFN-β 刺激 PBMC（13,999 细胞，13 个聚类）
- **批次整合（2个数据集）**：
  - 人类肺 atlas（使用文库身份作为批次）
  - 嗅周皮层数据集（17,535 细胞，2 个样本批次，16 种类型）
- **扰动响应预测（5个细胞环境）**：H1、HepG2、Jurkat、K562、RPE1，来自 Perturb-seq 数据（State 框架）。

### 基准方法
- UCE、State、scGPT、TranscriptFormer、STACK、C2S-2B（C2S-Scale 的 2B 版本）
- 消融实验使用 CellOS 的 0.2B、2B 单视图预训练检查点，以及最终 12B MoE+LLM-JEPA 版本。

### 评估指标
- 注释：ARI、NMI、ASW，归一化后平均得到“生物学保留分数”。
- 批次整合：silhouette batch score、graph connectivity、iLISI，平均得到“批次效应分数”。
- 扰动预测：DE Spearman、Pearson edist、聚类一致性、DE 方向匹配、Pearson ∆。

---

## 4. 资源与算力

论文未明确说明训练 CellOS 12B 模型所使用的 GPU 型号、数量及训练时长。仅提及训练数据规模为 390.5M 细胞、47,845 个测序样本，模型参数量 12B 是通过稀疏 MoE 扩展实现。未提及具体硬件资源或训练时间细节。

---

## 5. 实验数量与充分性

- **注释基准**：6 个数据集，涵盖不同组织、细胞类型粒度、扰动状态。
- **批次整合基准**：2 个数据集，具有明确批次标签。
- **扰动预测基准**：5 个细胞环境（H1、HepG2、Jurkat、K562、RPE1），使用 State 的框架隔离表示质量影响。
- **消融实验**：在 T 细胞亚聚类上比较 0.2B、2B、12B（Stage-3）三个检查点，展示缩放效应和多视图对齐贡献。
- **与6个竞争模型公平比较**：统一下游过渡模型、训练流程和评估协议（仅替换嵌入）。

实验总体上覆盖了多个任务和视角，基准设计公平（隔离变量），消融验证了缩放和 JEPA 对齐的收益。但在批次整合基准上仅使用两个数据集，略少；注释基准中部分数据集细胞数较小（如 T 细胞亚聚类 1.4 万细胞），可能限制泛化性评估。整体而言，实验数量充分、设计较为客观。

---

## 6. 论文的主要结论与发现

1. CellOS 在注释基准上 **一致优于** 所有对比模型，达到最高归一化 ARI（0.751）、NMI（0.797）、ASW（0.828），整体生物学保留分数 0.792。
2. 在批次整合基准上，CellOS 获得最高图连通性（GC=0.964），批次效应分数 0.771，仅次于 STACK（0.801），但 STACK 的生物学保留显著弱于 CellOS（0.474 vs 0.792），表明 CellOS 实现了 **良好批次混合而不牺牲生物结构**。
3. 扰动响应预测：CellOS 在 DE Spearman（0.590）、Pearson edist（0.619）、聚类一致性（0.633）上排名第一，DE 方向匹配并列第一，表明其嵌入更能捕获状态变化信息，支持下游因果建模。
4. 消融实验显示：模型参数从 0.2B 到 12B 缩放带来 ARI +36%、NMI +19%，其中多视图 JEPA 对齐（Stage-3）在 2B→12B 中额外贡献显著（ARI +0.042），表明 **缩放和跨视图对齐均有益**。
5. CellOS 是当前 **最大的单细胞基础模型之一**（12B 参数），验证了 Dense-to-MoE 扩展的可行性。

---

## 7. 优点：方法或实验设计上的亮点

- **多视图设计新颖**：首次将 JEPA 风格潜在预测对齐引入单细胞转录组学，显式分离表达丰度与群体信息含量，使罕见但信息性强的基因信号可被模型利用。
- **三阶段训练策略清晰**：先学表达语法，再扩展容量，最后对齐视图，每一步有明确目的，避免了同时引入大量目标导致不稳定。
- **Dense-to-MoE 功能保留初始化**：保留预训练知识，支持稳定扩展到 12B 参数。
- **扰动预测实验隔离表示贡献**：统一下游模型，直接评估嵌入质量，结果可靠。
- **消融实验验证缩放和对齐的独立贡献**，提供了工程和算法洞察。

---

## 8. 不足与局限

- **感知视图依赖全局统计**：当前感知视图基于整个预训练语料的经验分布，未建模组织、谱系或条件特异性背景。作者承认未来可引入上下文感知的感知视图。
- **仅使用转录组数据**：未整合染色质可及性、蛋白质丰度、空间信息等，限制视图多样性。
- **模型尚未直接建模细胞动态**：CellOS 学习静态表示，虽然支持下游扰动预测，但未在预训练中使用时间序列或扰动轨迹数据。作者指出需要扩展至因果虚拟细胞系统。
- **批次整合基准仅两个数据集**：覆盖面可能不足，尤其跨技术和物种的泛化性尚未验证。
- **未报告训练资源细节**：GPU 数量、训练时长等信息缺失，阻碍可重复性和成本评估。
- **感知视图的分数定义**使用上尾分位数，可能对低表达基因（如零膨胀）不敏感，需要进一步研究替代信息度量。

### 实验注意点
- 注释基准中部分数据集细胞数量较少（如 iPSC 细胞型分化中某些类型仅 20 个细胞），小样本下的表现可能受统计波动影响，但 ARI/NMI 等指标在随机标签下期望值已知。
- 对比方法均为公开模型，但 CellOS 训练数据规模（3.9 亿细胞）大于许多竞争模型，需要思考数据规模差异的影响。论文未进行控制数据量的对比实验。

（完）
