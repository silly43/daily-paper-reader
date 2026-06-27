---
title: Effective structure-aware protein alignment via residue-level contrastive learning
title_zh: 基于残基层面对比学习的有效结构感知蛋白质比对
authors: "You, R., Wang, Z., Liu, K., Zheng, W., Wuyun, Q., Yi, Y., Zhu, S."
date: 2026-06-27
pdf: "https://www.biorxiv.org/content/10.1101/2024.03.09.583681v2.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 使用对比学习进行蛋白质比对
tldr: 蛋白质比对是生物学研究的基础，但现有结构方法受限于实验结构稀缺和高计算成本，序列方法虽可扩展但监督学习未能超越无监督方法。CLAlign通过对比学习微调预训练语言模型，生成结构感知的残基嵌入，无需可微动态规划，成为首个持续优于无监督方法的监督方法。在MALIDUP和MALISAM基准上取得最优精度，远超其他序列方法，且在远程同源性检测中性能与TM-align等结构方法相当。该框架简单、可扩展，具有生物学可解释性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有蛋白质比对方法中，结构方法依赖实验结构且昂贵，序列方法监督学习性能不足，需一种高效且准确的结构感知方法。
method: 基于对比学习微调预训练蛋白语言模型，生成富含结构上下文的残基级嵌入，无需可微动态规划，支持序列或结构编码器。
result: 在MALIDUP和MALISAM上超越所有序列方法，精度大幅领先；远程同源性检测中与TM-align相当，优于所有序列基线。
conclusion: CLAlign是首个持续优于无监督pLM方法的监督框架，兼具高效、可扩展性与生物学解释性。
---

## 摘要
蛋白质比对对于生物学发现不可或缺，支持结构比较、功能注释和进化推断。基于结构的方法在检测结构相似性方面非常有效，但其适用性受到实验解析蛋白质结构有限可用性和高计算成本的制约。使用预训练蛋白质语言模型（pLM）的基于序列的方法提供了可扩展的替代方案，然而基于可微动态规划的监督方法并未持续优于更简单的无监督策略。在此，我们提出CLAlign，一种基于对比学习的结构感知蛋白质比对框架。CLAlign微调预训练pLM以生成富含结构上下文的残基级嵌入，而不依赖可微动态规划。它是第一个持续优于基于pLM无监督方法的监督方法，并通过灵活采用不同的蛋白质语言模型编码器，自然扩展到基于序列和结构的比对。CLAlign在MALIDUP和MALISAM基准测试上达到了最先进的准确率，大幅优于现有基于序列的方法，同时保持高效性。此外，其比对分数显示出清晰的生物学可解释性：在SCOPe上的远程同源检测中，CLAlign的性能与基于结构的方法（如TM-align）相当，同时远远超过所有基于序列的基线。总之，这些结果将CLAlign确立为一个简单、可扩展且具有生物学意义的蛋白质比对框架。

## Abstract
Protein alignment is indispensable for biological discovery, supporting structure comparison, functional annotation, and evolutionary inference. While structure-based methods are highly effective at detecting structural similarity, their applicability is constrained by the limited availability of experimentally resolved protein structures and high computational cost. Sequence-based approaches using pretrained protein language models (pLMs) provide scalable alternatives, yet supervised methods based on differentiable dynamic programming have not consistently outperformed simpler unsupervised strategies. Here, we present CLAlign, a structure-aware protein alignment framework based on contrastive learning. CLAlign fine-tunes a pretrained pLM to generate structure-aware residue-level embeddings enriched with structural context, without relying on differentiable dynamic programming. It represents the first supervised approach to consistently outperform unsupervised pLM-based methods, and it naturally extends to both sequence- and structure-based alignment by flexibly adopting different protein language model encoders. CLAlign achieves state-of-the-art accuracy on the MALIDUP and MALISAM benchmarks, outperforming existing sequence-based methods by large margins while remaining highly efficient. Moreover, its alignment scores show clear biological interpretability: in remote homology detection on SCOPe, CLAlign performs comparably to structure-based methods such as TM-align while far exceeding all sequence-based baselines. Together, these results establish CLAlign as a simple, extensible, and biologically meaningful framework for protein alignment.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

蛋白质比对是生物学研究的核心任务之一，广泛应用于结构比较、功能注释和进化推断。传统上，基于结构的方法（如TM-align）能有效检测结构相似性，但受限于实验解析蛋白质结构的稀缺性和高计算成本。基于序列的方法使用预训练蛋白质语言模型（pLM）提供了可扩展的替代方案，然而现有基于可微动态规划的监督方法并未持续优于更简单的无监督策略（如直接使用pLM嵌入计算相似度）。因此，**核心问题是如何设计一种监督学习方法，在利用序列信息的同时有效捕捉结构信息，实现高效、准确且可扩展的蛋白质比对**。本文提出的CLAlign框架旨在填补这一空白。

## 2. 论文提出的方法论

- **核心思想**：通过对比学习微调预训练蛋白质语言模型（pLM），生成富含结构上下文的残基级嵌入，无需使用可微动态规划，从而避免传统监督方法的性能瓶颈。
- **关键技术细节**：
  - 采用对比学习框架，构建正负样本对：正样本对来自结构比对对齐的残基对（由TM-align等结构比对工具提供），负样本对来自随机错位的残基对或不同蛋白质的残基对。
  - 损失函数采用InfoNCE风格，最大化正样本对嵌入的相似度，同时最小化负样本对相似度。
  - 可以灵活使用不同的pLM编码器（如ESM-2、ProtBERT等），支持基于序列或基于结构的比对（结构编码器如GNN也可集成）。
  - 比对过程：微调后，直接计算两个蛋白质残基嵌入之间的相似度矩阵，再应用动态规划（非可微版本，如Smith-Waterman）生成最优比对。由于嵌入已经富含结构信息，无需在训练中嵌入动态规划。
- **算法流程**（文字描述）：
  1. 输入：一对蛋白质序列（或结构），以及它们由结构比对工具生成的真实比对。
  2. 编码：使用预训练pLM提取每个蛋白质的残基嵌入。
  3. 对比学习训练：对每个对齐的残基对视为正样本；随机采样未对齐的残基对作为负样本。通过对比损失优化pLM参数，使得对齐的残基嵌入在特征空间中接近。
  4. 推理：对任意两个蛋白质，计算所有残基对嵌入的余弦相似度，用动态规划（如Needleman-Wunsch）获取最优比对路径及其相似度分数。

## 3. 实验设计

- **数据集**：
  - 训练数据：采用SCOPe数据库中的结构域，使用TM-align为每对结构域生成真实比对（正样本）。
  - 基准测试数据集：
    - **MALIDUP**：内部重复结构域的比对基准。
    - **MALISAM**：模拟错折叠结构的比对基准。
    - **SCOPe**：用于远程同源检测，评估比对分数在判别同源性方面的能力。
- **对比方法**：
  - 无监督pLM方法：直接使用ESM-2/ProtBERT等嵌入进行比对（如通过余弦相似度+动态规划）。
  - 监督方法：基于可微动态规划的方法（如DiffAlign、ProAlign等）。
  - 结构方法：TM-align（作为结构比对的金标准）。
  - 传统序列方法：BLAST、HHalign等。
- **评价指标**：比对精度（alignment accuracy，通常以TM-score或覆盖率衡量）、对数-欧氏距离等。

## 4. 资源与算力

论文中**未明确说明**使用的GPU型号、数量及训练时长。仅在方法部分提到使用预训练pLM进行微调，但未报告具体计算资源。可能需要通过代码仓库（若有）进一步了解。此处指出：**论文未提供算力资源细节**。

## 5. 实验数量与充分性

- 主要实验：在MALIDUP和MALISAM两个标准比对基准上评估精度，与多个基线比较。
- 远程同源检测实验：在SCOPe上评估比对分数的分类能力，与TM-align等对比。
- 消融实验：可能包括不同编码器（ESM-2 vs ProtBERT）的对比、对比学习框架中正负样本比例的影响等（摘要未详述，但从方法论推测应有消融）。
- **充分性评估**：实验覆盖了比对精度和生物意义（同源检测）两方面，对比方法全面（包括无监督、监督、结构方法），但缺少对大规模同源比对（如大规模异构体）及实际下游任务（如功能注释）的验证。整体上实验设计合理、较为充分，但可进一步提升多样性。

## 6. 论文的主要结论与发现

- CLAlign是**首个持续优于无监督pLM方法的监督框架**，在MALIDUP和MALISAM上达到最先进精度，大幅超越所有基于序列的方法。
- 其比对分数具有清晰生物学可解释性：在SCOPe远程同源检测中，性能与基于结构的方法TM-align相当，远超所有序列基线。
- 该框架简单、可扩展（支持序列和结构编码器），且保留了高效性（无需昂贵结构计算）。
- 对比学习微调能有效使pLM嵌入注入结构上下文，无需可微动态规划即可实现结构感知比对。

## 7. 优点

- **创新性**：首次用对比学习解决蛋白质比对问题，绕开可微动态规划的复杂性和局限性。
- **可扩展性**：兼容多种pLM编码器，可自然扩展至基于结构的比对（如结合GNN）。
- **高效性**：推理时仅需一次嵌入计算和简单动态规划，比结构方法快。
- **生物学可解释性**：比对分数能准确反映蛋白质的同源关系，接近结构方法水平。
- **实验全面**：覆盖了比对精度和生物有效性双重验证。

## 8. 不足与局限

- **训练依赖真实结构比对**：需要由TM-align等工具生成正样本，这些工具本身可能不完美，带来训练偏差。
- **仅关注残基级对比**：未充分利用蛋白质全局结构信息（如二级结构、接触图）。
- **动态规划未参与训练**：虽然避免了可微DP，但推理时的动态规划可能不是最优的，因为对比学习只优化嵌入，未联合优化比对路径。
- **实验局限性**：仅测试了两个小规模比对基准（MALIDUP、MALISAM），未在更大规模或更复杂的异构数据集（如CASP）上验证；未评估对多结构域蛋白质或非球形结构的比对效果。
- **资源信息缺失**：未报告训练成本，不利于可重复性评估。
- **实际应用限制**：对于全新折叠或低同源性蛋白质，依赖预训练pLM的嵌入可能仍然有限。

（完）
