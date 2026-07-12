---
title: "NiCLIP: Neuroimaging contrastive language-image pretraining model for predicting text from brain activation images"
title_zh: NiCLIP：用于从脑激活图像预测文本的神经影像对比语言-图像预训练模型
authors: "Peraza, J. A., Kent, J. D., Nichols, T. E., Poline, J.-B., de la Vega, A., Laird, A. R."
date: 2026-07-11
pdf: "https://www.biorxiv.org/content/10.1101/2025.06.14.659706v4.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 将CLIP对比学习应用于神经影像
tldr: 预测认知过程从脑激活图是长期难题，现有方法依赖有限指标，难以捕获文本语义。本文提出NiCLIP，基于CLIP对比学习，利用23000篇神经科学文章训练文本-脑关联模型。评估显示使用全文本优于摘要，能准确预测认知任务（如情感、语言、运动）和特定脑区功能，但对噪声个体数据敏感。NiCLIP为神经影像定量功能解码提供强大工具，促进假设生成与科学发现。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-06-14-659706-v4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1825, \"height\": 1810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-06-14-659706-v4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1722, \"height\": 1984, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-06-14-659706-v4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1711, \"height\": 1868, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-06-14-659706-v4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1803, \"height\": 1594, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-1101-2025-06-14-659706-v4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1845, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-1101-2025-06-14-659706-v4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1702, \"height\": 1439, \"label\": \"Table\"}]"
motivation: 现有功能解码方法语义捕获不足，需结合大语言模型与对比学习实现文本-脑关联对齐。
method: 基于CLIP架构，利用23000篇神经科学全文文章训练文本-脑激活图对比模型NiCLIP。
result: NiCLIP在全文本输入时性能最优，准确预测认知任务及脑区功能，但对噪声个体激活图敏感。
conclusion: NiCLIP是神经影像定量功能解码的重大进展，为科研提供假设生成与发现工具。
---

## 摘要
从脑激活图中预测认知过程多年来一直是神经科学领域的一个未解问题。元分析功能解码方法旨在通过提供与特定脑区相关的行为特征的定量估计来解决这一问题。现有方法在神经影像元分析中面临固有挑战，特别是在整合出版物中的文本信息时，因为它们依赖有限的度量标准，无法捕捉文本的语义上下文。大语言模型（LLMs）与先进的深度对比学习模型（如CLIP）相结合，用于对齐文本与图像，彻底改变了神经影像元分析，为功能解码挑战提供了潜在的解决方案。在这项工作中，我们提出了NiCLIP，一个对比语言-图像预训练模型，能够从脑激活模式预测认知任务、概念和领域。我们利用了超过23,000篇神经科学文章来训练一个用于文本-脑关联的CLIP模型。对NiCLIP预测的评估显示，使用全文文章而非摘要时性能最优，同时使用具有精确任务-概念-领域映射的精心策划的认知本体也能提升性能。此外，领域特定微调的LLMs（如BrainGPT模型）在性能上与其基础LLM模型数值上相似。我们的结果表明，NiCLIP能够从人类连接组项目提供的群体级激活图中准确预测跨多个领域（如情感、语言、运动）的认知任务，并精确表征特定脑区（包括杏仁核、海马体和颞顶联合区）的功能角色。然而，NiCLIP在噪声较大的受试者级激活图上显示出局限性。NiCLIP代表了神经影像定量功能解码的重要进展，为研究人员提供了一种用于假设生成和科学发现的强大工具。

## Abstract
Predicting cognitive processes from brain activation maps has remained an open question within the neuroscience community for many years. Meta-analytic functional decoding methods aim to tackle this issue by providing a quantitative estimation of behavioral profiles associated with specific brain regions. Existing methods face intrinsic challenges in neuroimaging meta-analysis, particularly in consolidating textual information from publications, as they rely on limited metrics that do not capture the semantic context of the text. The combination of large language models (LLMs) with advanced deep contrastive learning models (e.g., CLIP) for aligning text with images has revolutionized neuroimaging meta-analysis, potentially offering solutions to functional decoding challenges. In this work, we present NiCLIP, a contrastive language-image pretrained model that predicts cognitive tasks, concepts, and domains from brain activation patterns. We leveraged over 23,000 neuroscientific articles to train a CLIP model for text-to-brain association. Evaluation of NiCLIP predictions revealed that performance is optimized when using full-text articles instead of abstracts, as well as a curated cognitive ontology with precise task-concept-domain mappings. Furthermore, domain-specific fine-tuned LLMs (e.g., BrainGPT models) show numerically similar performance to their base LLM counterparts. Our results indicated that NiCLIP accurately predicts cognitive tasks from group-level activation maps provided by the Human Connectome Project across multiple domains (e.g., emotion, language, motor) and precisely characterizes the functional roles of specific brain regions, including the amygdala, hippocampus, and temporoparietal junction. However, NiCLIP showed limitations with noisy subject-level activation maps. NiCLIP represents a significant advancement in quantitative functional decoding for neuroimaging, offering researchers a powerful tool for hypothesis generation and scientific discovery.

---

## 论文详细总结（自动生成）

# NiCLIP：用于从脑激活图像预测文本的神经影像对比语言-图像预训练模型 - 详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：从脑激活模式推断认知过程（即**反向推理**，Reverse Inference）是神经科学长期未解决的难题。传统的功能解码方法（如 Neurosynth 相关系数解码器、GC-LDA）依赖词袋模型（TF-IDF）和预计算的元分析图谱，无法捕捉文本的语义上下文，且词汇表固定、缺乏预测能力。
- **背景**：大语言模型（LLM）的发展使语义理解成为可能；CLIP 等对比学习模型成功对齐文本与图像。最新工作 NeuroConText 已初步实现文本-脑对比对齐，但未系统研究脑到文本的正式解码，也未利用认知本体进行结构化预测。本文旨在填补这一空白。

## 2. 论文提出的方法论

### 核心思想
- 基于 CLIP 架构，将脑激活图像与对应的全文文章文本在共享潜在空间中对齐；再通过认知本体（Cognitive Atlas）和贝叶斯框架实现从脑激活到任务、概念、领域的三层次解码。

### 关键技术细节

#### 2.1 文本-脑对齐（CLIP 训练）
- **数据来源**：从 PubMed Central 下载 23,865 篇 fMRI 全文文章（使用 Pubget 提取文本与激活坐标）。
- **文本嵌入**：使用预训练 LLM（比较了 BrainGPT-7B v0.2、Mistral-7B v0.1、BrainGPT-7B v0.1、Llama-2-7b-chat-hf）对全文或摘要编码，长文本通过分块平均得到文章级嵌入。
- **图像嵌入**：将报道的激活坐标通过 MKDA（Multi-Level Kernel Density Analysis）生成二值建模激活图（半径 10mm），再使用 DiFuMo 512 分区降维至 512 维。
- **CLIP 模型**：文本编码器包含一个投影块和两个残差块，图像编码器包含三个残差块。使用 InfoNCE 对比损失，训练 50 个 epoch，batch size 128，学习率 5e-4，早停策略（patience=10）。采用 23 折交叉验证。

#### 2.2 功能解码（NiCLIP）
- 利用训练好的 CLIP 模型，将目标脑激活的图像嵌入与认知本体中每个任务名称+定义的文本嵌入在共享潜在空间计算余弦相似度，通过 softmax 得到似然 $P(A|T)$。
- 利用贝叶斯定理计算任务后验概率：
  $$P(T|A) = \frac{P(A|T) \, P(T)}{\sum_{T'} P(A|T') P(T')}$$
  其中先验 $P(T)$ 由任务在训练语料中的语义相似度频率估计。
- 概念概率 $P(C|A)$ 和域概率 $P(D|A)$ 通过 noisy-OR 模型传播：
  $$P(C|A) = 1 - \prod_{T \in \text{tasks}(C)} \left(1 - P(T|A)\right)$$
  域同理。

## 3. 实验设计

### 数据集与场景
- **训练数据**：PubMed Central 中 23,865 篇 fMRI 全文文章（含坐标）。
- **评估数据**：
  - **组级任务 fMRI 图**：HCP S1200 任务 fMRI 的七个域（情绪、赌博、语言、运动、关系、社会、工作记忆），每个域用一个代表性对比（例如 Story vs Math）。
  - **ROI 图**：六个元分析脑区（杏仁核、海马体、岛叶、纹状体、右颞顶联合区、腹内侧前额叶）。
  - **个体级激活图**：HCP 787 名个体的对应任务激活图。
- **认知本体**：Cognitive Atlas（完整版和精简版，后者为 Menuet et al. 2022 提供的常用任务子集）。

### 基准方法
- **Neurosynth 相关系数解码器**：基于预计算元分析图谱和 TF-IDF。
- **GC-LDA**：无监督主题模型，基于坐标的贝叶斯方法。

### 对比维度
- LLM 类型（四种）
- 文章部分（全文 vs 摘要）
- 本体版本（完整 vs 精简）
- 任务嵌入策略（仅名称 vs 名称+定义）

### 评估指标
- **文本-脑关联**：Recall@k（k=10,100）和 Mix&Match。
- **功能解码**：Recall@K（任务和概念用 Recall@4，域用 Recall@2，因候选集大小不同）。

## 4. 资源与算力

- 论文**未明确说明**使用的 GPU 型号、数量或训练时长。
- 仅提及使用 FIU IRCC 高性能计算资源，以及训练采用 50 个 epoch、batch size 128 等超参数。未提供具体算力细节。

## 5. 实验数量与充分性

- **实验数量丰富**：
  - 文本-脑关联：4种 LLM × 2种文章部分 → 8种配置的交叉验证结果（表1）。
  - 功能解码：4种 LLM × 2种文章部分 × 2种本体 × 2种嵌入策略 → 大量消融（表2列出了关键配置），共约 32 组以上的解码结果。
  - 附加实验：组级图解码详细结果（图2）、ROI 解码结果（图3）、个体级图解码（图S4-S5）、激活图变体实验（图S9）。
  - 与两个基线（Neurosynth、GC-LDA）的定量比较。
- **充分性与公平性**：
  - 对比基线是当前主流坐标法功能解码方法，公平。
  - 消融实验覆盖了关键因素（文本来源、LLM、本体、嵌入策略）。
  - 个体级图表现差，作者已清晰指出。
  - 交叉验证、早停等保证模型选择可靠。
- 但未在更多独立数据集（如 IBC, NSD）上系统验证，仅提及初步 IBC 结果（图S10），实验完整性尚可提升。

## 6. 论文的主要结论与发现

1. **文本-脑关联**：使用全文文章优于仅摘要，且 BrainGPT-7B v0.2 数值最优，但与 Mistral 等通用 LLM 差异很小。
2. **功能解码性能**：
   - 最佳配置（全文 + BrainGPT-v0.2 + 精简本体 + 名称+定义）在 HCP 组级图上达到任务 Recall@4 = 62.86%，概念 Recall@4 = 43.57%，域 Recall@2 = 90.48%。
   - **显著优于基线**：Neurosynth 和 GC-LDA 最高仅 20.71%。
3. **ROI 解码**：能准确识别杏仁核（情绪）、海马体（工作记忆）、岛叶（疼痛）、纹状体（语言）、rTPJ（社会认知）、vmPFC（决策）的功能角色。
4. **个体级解码**：效果较差（任务 Recall@4 = 38.19%），仅个别任务（情绪、社会）可正确预测，主要由于噪声和个体变异性。
5. **本体重要性**：精简版 Cognitive Atlas 显著优于完整版，使用任务定义+名称优于仅名称。

## 7. 优点

- **方法论创新**：首次将 CLIP 对比学习与认知本体融合，实现多层次、结构化功能解码（任务→概念→域），超越传统词袋方法。
- **数据规模**：利用 23,000+ 篇全文文章，是目前最大的神经影像文本-坐标数据库之一，扩大语义覆盖。
- **实用工具**：提供开源代码、Colab 演示、HuggingFace web 接口，便于社区使用。
- **严谨消融**：系统比较 LLM、文章部分、本体、嵌入策略的影响，分析深入。
- **揭示局限性**：坦诚个体级解码的失败，并提出未来改进方向（扩展训练数据、缓解文本分布漂移等）。

## 8. 不足与局限

- **个体级解码差**：对噪声敏感，无法可靠应用于单个被试图；训练数据中个体图极少。
- **训练数据量小**：CLIP 通常需要百万级样本，本文仅 2 万对，虽受限于神经影像文献增长，但制约泛化能力。
- **文本表示粗糙**：长文本通过分块平均，丢失段落结构和细节；训练用文章长文本与推理用本体短文本存在分布偏移。
- **本体不完备**：Cognitive Atlas 社区维护，映射不完全、任务定义不统一；精简版虽提升但仍有限。
- **似然概率缺乏校准**：$P(A|T)$ 经 softmax 虽满足非负且和为1，不是真实统计似然；后验应视为排名分而非概率。
- **算力信息缺失**：未报告具体 GPU 型号、数量、训练时长，影响可复现性评估。
- **未见负激活处理**：训练数据主要基于正激活坐标，对负激活映射的解码效果未充分验证。
- **跨数据集验证有限**：除 HCP 外仅提及 IBC 初步结果，未在更多独立数据集（如 NSD、ABIDE）上系统评估。

（完）
