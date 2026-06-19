---
title: "TifBERT: a self-supervised foundation model for normalization-robust bulk RNA-seq representation learning"
title_zh: TifBERT：一种面向归一化鲁棒的批量RNA-seq表征学习的自监督基础模型
authors: "Hosseini, S., Sharma, D."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.728683v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 全转录组bulk RNA-seq表示学习的自监督框架
tldr: "现有批量RNA-seq基础模型依赖表达离散化或外部知识，对归一化方案敏感，限制鲁棒性。TifBERT采用TF-IDF排序将无序表达谱转换为基因序列，通过掩码基因建模自监督预训练，无需重构表达值或基因子集限制。在33种TCGA癌症分类中达到90.83%准确率和0.996 AUC，嵌入有效秩高达95.6，是现有模型的15倍。该模型在GTEx组织上零样本泛化，捕获通路生物学一致性。TifBERT提供了可扩展、归一化无关的基础模型，支持可复用批量转录组表示学习。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法依赖表达离散化或外部知识，对归一化方案敏感，难以跨队列泛化。
method: 利用TF-IDF排序将表达谱转为样本特异性基因序列，通过掩码基因建模自监督预训练。
result: "在TCGA 33种癌症分类达90.83%准确率，有效秩95.6，通路Pearson相关性0.76，GTEx零样本泛化。"
conclusion: TifBERT实现了归一化无关、可扩展的批量转录组基础模型，提升表示稳定性与丰富性。
---

## 摘要
批量RNA测序仍是转化基因组学的核心，但基础模型开发主要聚焦于单细胞数据。现有的批量RNA-seq Transformer方法通常依赖于表达离散化、数值重构、外部基因嵌入或受限基因集，这限制了跨归一化方案和队列的鲁棒性。本文提出TifBERT，一种全转录组批量RNA-seq表征学习的自监督框架。TifBERT利用词频-逆文档频率（TF-IDF）排序将每个无序表达谱转化为样本特异性基因序列，优先考虑在样本内高表达且在队列中选择性表达的基因。随后通过掩码基因建模进行预训练，从转录组上下文中预测基因身份而非重构表达值。

TifBERT在涵盖五种RNA-seq归一化方案的统一TCGA泛癌数据上预训练，无需表达分箱、标志基因限制或外部生物学嵌入，即可学习约10,000个基因的上下文表征。在33种TCGA癌症类型中，TifBERT实现了90.83%的准确率、0.996的宏AUC-ROC以及0.903的MCC。它还能捕获通路水平生物学特征，在1,387个PARADIGM通路活性上分别达到0.754和0.762的样本-wise和通路-wise平均皮尔逊相关系数。对GTEx健康组织的独立评估显示，无需重新训练即可保留组织水平的转录组结构。与现有模型相比，TifBERT在实现竞争性亚型区分的同时具有更高的稳定性，并产生显著更丰富的嵌入几何结构（有效秩95.6 vs 6.3），且无需表达离散化或分布内预训练暴露。综上，TifBERT为可复用的批量转录组表征学习提供了一种可扩展、与归一化无关的基础模型。

## Abstract
Bulk RNA sequencing remains central to translational genomics, yet foundation-model development has largely focused on single-cell data. Existing transformer approaches for bulk RNA-seq often rely on expression discretization, numerical reconstruction, external gene embeddings, or restricted gene sets, limiting robustness across normalization schemes and cohorts. Here, we introduce TifBERT, a self-supervised framework for full-transcriptome bulk RNA-seq representation learning. TifBERT converts each unordered expression profile into a sample-specific gene sequence using term frequency-inverse document frequency (TF-IDF) ordering, prioritizing genes that are both highly expressed within a sample and selectively expressed across the cohort. It is then pretrained using masked gene modeling, predicting gene identities from transcriptomic context rather than reconstructing expression values.

Pretrained on harmonized TCGA Pan-Cancer data spanning five RNA-seq normalization schemes, TifBERT learns contextual representations across approximately 10,000 genes without expression binning, landmark-gene restriction, or external biological embeddings. Across 33 TCGA cancer types, TifBERT achieved 90.83% accuracy, 0.996 macro AUC-ROC, and 0.903 MCC. It also captured pathway-level biology, achieving mean sample-wise and pathway-wise Pearson correlations of 0.754 and 0.762 across 1,387 PARADIGM pathway activities. Independent evaluation on GTEx healthy tissues showed preservation of tissue-level transcriptomic structure without retraining. In comparison with existing models, TifBERT achieves competitive subtype discrimination with substantially greater stability and produces markedly richer embedding geometry (effective rank 95.6 versus 6.3), without requiring expression discretization or in-distribution pretraining exposure. Together, TifBERT provides a scalable, normalization-independent foundation model for reusable bulk transcriptomic representation learning.