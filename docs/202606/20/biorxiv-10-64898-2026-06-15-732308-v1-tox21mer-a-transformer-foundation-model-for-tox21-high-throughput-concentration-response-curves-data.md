---
title: "Tox21mer, A transformer foundation model for Tox21 high-throughput concentration-response curves data"
title_zh: Tox21mer：用于Tox21高通量浓度-响应曲线数据的Transformer基础模型
authors: "Li, L., Hwang, J., Shockley, K., Li, Y., Motsinger-Reif, A., Hsieh, J.-H., Auerbach, S. S., Reif, D."
date: 2026-06-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732308v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 浓度响应曲线的掩码重建自监督学习
tldr: Tox21项目产生了大量浓度-响应曲线数据。我们提出Tox21mer，一个43.5M参数的Transformer模型，通过掩码响应重建预训练于约250万条曲线，学习768维表示。线性探针在保留化合物上预测分类宏F1达0.985，回归R²为0.87，且表示主要来自自监督目标。该模型提供了可复用的基础表示，可结合化学特征或蒸馏到化学模型用于大规模外推。
source: biorxiv
selection_source: fresh_fetch
motivation: 处理Tox21高通量浓度-响应曲线数据，提供可复用的基础表示以支持化合物毒性预测。
method: 用Transformer编码曲线和元数据，以掩码响应重建为主目标预训练，辅以少量监督信号。
result: 线性探针在三种结果分类上宏F1达0.985，log10(AC50)的R²为0.87，表示形成清晰的曲线类簇。
conclusion: Tox21mer为浓度-响应数据提供了可复用基础表示，可通过特征融合或蒸馏支持未测试化合物外推。
---

## 摘要
美国Tox21合作项目已生成一个大型参考文库，包含高通量浓度-响应测定数据。本文提出Tox21mer，一个包含4350万参数的Transformer模型，它将每条Tox21浓度-响应曲线连同测定元数据编码为768维表示。Tox21mer在来自102种测定方案和6727种化合物的约250万条曲线上进行了预训练，主要目标为掩蔽响应重建，并以低权重辅助监督测定结果和AC50。为评估学习到的表示，我们在留出化合物的浓度-响应曲线的冻结嵌入上训练轻量级探针。该表示在三类结果预测（激动剂、拮抗剂、无活性）上实现了0.985的宏F1，在活性/非活性预测上实现了0.994的二值F1，以及log10(AC50)的R²为0.87。学习到的嵌入按曲线类别形成了连贯的分组。仅掩蔽预训练变体保持了接近基线的探针性能，表明表示主要从自监督目标而非辅助标签中学习。消融分析进一步表明，预测性能主要取决于以测定背景为条件的曲线级响应值分布，而对曲线内详细顺序的依赖有限。因此，Tox21mer为Tox21浓度-响应数据提供了可重用的基础表示，可通过与化学特征整合或蒸馏为仅化学属性的学生模型，支持外推至未测试化合物，用于大规模外部筛选。

## Abstract
The U.S. Tox21 collaboration has generated a large reference library of high-throughput concentration-response assays. Here we present Tox21mer, a 43.5-million-parameter transformer that encodes each Tox21 concentration-response curve together with assay metadata into a 768-dimensional representation. Tox21mer was pretrained on ~2.5 million curves from 102 assay protocols and 6,727 compounds using masked-response reconstruction as the primary objective, with low-weight auxiliary supervision on assay outcome and AC50. To evaluate the learned representation, we trained lightweight probes on frozen embeddings from concentration-response curves of held-out compounds. The representation supported a macro-F1 of 0.985 for three-class outcome prediction (agonist, antagonist, inactive), a binary F1 of 0.994 for active/inactive prediction, and an R2 of 0.87 for log10(AC50). The learned embeddings formed coherent groupings by curve-class category. A masked-only pretraining variant retained near-baseline probe performance, indicating that the representation is learned largely from the self-supervised objective rather than from auxiliary labels. Ablation analyses further showed that predictive performance depends mainly on curve-level response-value distributions conditioned on assay context, with limited reliance on detailed within-curve ordering. Tox21mer thus provides a reusable foundation representation for Tox21 concentration-response data that can support extrapolation to untested compounds through integration with chemical features or distillation into chemistry-only student models for large-scale external screening.

---

## 论文详细总结（自动生成）

# Tox21mer：用于Tox21高通量浓度-响应曲线数据的Transformer基础模型 — 结构化总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

美国Tox21合作项目已生成一个包含数千种化合物、多种测定方案的大规模浓度-响应曲线数据库。传统方法通常为每条曲线单独建模或仅使用化学结构特征，缺乏一种能统一编码曲线形态、测定背景和毒性效应的高效表示。  
**本文目标**：构建一个可复用的基础模型（Tox21mer），将浓度-响应曲线及关联元数据编码为低维嵌入，从而支持化合物毒性预测、曲线分类和未测试化合物的外推。

## 2. 论文提出的方法论

### 核心思想
- 使用 **Transformer** 架构（4350万参数）对每条浓度-响应曲线进行 **自监督预训练**，主要目标为 **掩码响应重建**（Masked Response Reconstruction）。
- 同时以低权重辅助监督信号（测定结果类别、AC50值）训练，增强表示的语义信息。
- 输入：每个浓度点的响应值 + 测定元数据（如测定方案ID、浓度梯度等）；输出：768维嵌入向量。

### 关键技术细节
- **预训练数据**：来自102种测定方案、6727种化合物的约250万条浓度-响应曲线。
- **自监督目标**：随机掩蔽曲线中部分浓度点的响应值，要求模型根据上下文（包括测定背景）预测被掩蔽值。
- **辅助监督**：加入测定结果（激动剂/拮抗剂/无活性）和$\log_{10}(\text{AC}_{50})$的预测损失，权重较低以避免主导自监督信号。
- **微调/评估**：冻结预训练嵌入，训练轻量级线性探针（分类器/回归器）进行下游任务评估。

## 3. 实验设计

### 数据集
- **训练集**：Tox21项目全部高通量浓度-响应曲线（~250万条）。
- **评估方式**：留出化合物（held-out compounds）的曲线，保证训练/测试化合物不重叠。

### Benchmark和评估指标
- **三种结果分类**（激动剂、拮抗剂、无活性）：宏平均F1（macro-F1）达到 **0.985**。
- **活性/非活性二分类**：二值F1达 **0.994**。
- **$\log_{10}(\text{AC}_{50})$回归**：$R^2$达到 **0.87**。

### 对比方法
- 论文未明确列出其他baseline模型对比，但通过消融实验验证了自监督目标的有效性（掩码预训练变体接近全监督性能）。  
- 未与传统化学指纹或分子图模型进行系统性比较（仅提及可蒸馏给化学模型）。

## 4. 资源与算力

论文中 **未明确提及** 具体使用的GPU型号、数量及训练时长。从模型规模（43.5M参数）和数据集（250万曲线）推测，训练可能需在单卡或多卡GPU上进行数天，但作者未报告细节。

## 5. 实验数量与充分性

- 主要实验包括：线性探针评估（分类+回归）、消融实验（掩码预训练 vs. 全目标）、分布 vs. 顺序依赖分析。
- **消融实验**：移除辅助监督后，表示质量几乎不变，证明表示主要来自自监督目标；通过扰乱曲线内顺序发现性能下降有限，表明学习主要依赖曲线级分布而非详细顺序。
- **充分性评价**：实验设计合理，覆盖了核心假设验证，但：
  - 缺乏与其他领域专用模型（如GNN、MLP基线）的对比。
  - 未在独立外部数据集上验证泛化能力（如新测定方案或不同实验室数据）。
  - 未探索不同预训练策略（对比学习、生成式时序模型）的对比。
- 整体较为充分，但横向比较不足。

## 6. 论文的主要结论与发现

1. **Tox21mer通过掩码响应重建自监督学习** 成功从浓度-响应曲线中学习到高质量表示，无需大量标注即可达到极高预测精度。
2. 表示维度（768维）足以区分三种曲线类别，且嵌入空间形成清晰的分组。
3. **监督信号（测定结果、AC50）贡献有限**，模型能力主要源于自监督任务对曲线统计分布的建模（而不是曲线内的精确顺序）。
4. 该表示可结合化学特征或通过知识蒸馏迁移到仅依赖化学结构的轻量模型，用于大规模外部筛选。

## 7. 优点（方法或实验设计亮点）

- **自监督范式的创新应用**：将掩码重建从自然语言/图像推广到浓度-响应曲线，有效利用海量无标注曲线数据。
- **编码测定背景**：将测定方案等元数据作为输入，使表示具有跨测定泛化潜力。
- **轻量级探针验证**：冻结嵌入训练线性模型，表明表示本身包含丰富语义，而非依赖复杂后续网络。
- **消融设计清晰**：明确区分自监督和监督信号贡献，揭示表示的关键来源。

## 8. 不足与局限

- **计算资源未公开**：限制了可复现性和公平比较。
- **缺乏强基线对比**：未与化学结构模型（如GNN、ChemBERTa）或传统曲线拟合模型比较，难以评估表示优越性。
- **泛化性验证不充分**：仅在Tox21内部留出化合物上评估，未在协变量偏移（不同实验室、新测定类型）下测试。
- **线性探针的性能天花板**：极高F1可能表示任务过于简单（数据高度规律），反而掩盖了模型对噪声或罕见曲线的鲁棒性。
- **对曲线顺序的弱依赖**：可能丢失动态响应特征（如形状变化），在需要精确时间/浓度点建模的下游任务中表现未知。
- **应用局限性**：蒸馏至化学模型时，需额外训练学生模型，且蒸馏效率未评估。

（完）
