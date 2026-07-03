---
title: Raw-count embeddings improve single-cell foundation models
title_zh: 原始计数嵌入改进单细胞基础模型
authors: "Schlede, S., Muruganandan, T. P., Gojjam Kantharaju, S., Kisis, I., Boecker, M., Kim Alves Carpinteiro, M., Schmitz, A., Buchwald, L. M., Sakthivelu, V., Gülcüler Balta, G. S., Anstötz, M., Rueger, M. A., Thomas, R. K., Beleggia, F."
date: 2026-07-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735389v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 通过掩码令牌预测进行单细胞基础模型的自监督预训练
tldr: 单细胞Transformer基础模型预处理复杂且未系统验证，本研究测试七种策略发现非归一化的log转换原始计数性能最优且基因顺序无关。提出Gene Intelligence模型，直接嵌入log1p转换原始计数并联合预测掩码token和计数，无需归一化或位置编码。在基因级任务和双峰检测达SOTA，细胞分类匹配大模型但参数少10-200倍，表明简化设计可提升性能。
source: biorxiv
selection_source: fresh_fetch
motivation: 当前单细胞基础模型依赖复杂预处理，但未经系统验证，需探究简化预处理能否保持或提升性能。
method: 测试七种预处理策略，提出Gene Intelligence模型，使用log1p转换原始计数嵌入，联合预测掩码token和计数，去除归一化、位置编码。
result: 非归一化log转换计数性能最佳，基因顺序无关；Gene Intelligence在基因级任务和双峰检测达SOTA，细胞分类匹配大模型且参数少10-200倍。
conclusion: 简化预处理和模型设计可有效提升单细胞基础模型性能，原始计数嵌入具有潜力。
---

## 摘要
单细胞Transformer基础模型已增长到数亿参数，但其背后的预处理选择（包括基因排序和文库大小归一化）尚未得到系统基准测试。通过测试七种策略，我们发现这些精心设计在很大程度上是不必要的：未经归一化的对数变换计数性能最佳，而基因顺序几乎无关紧要，甚至随机排序也优于复杂的基于排名的方案。由此产生的模型——Gene Intelligence，直接将log1p变换的原始计数投影到每个token嵌入中，并联合预测掩码token和计数，不使用归一化、位置编码或读取深度token。尽管简单，它在测试的基因级任务和双细胞检测中达到了最先进的性能，并在细胞分类任务上与当前大型基础模型相当，同时使用的参数减少了10到200倍。

## Abstract
Single-cell transformer foundation models have grown to hundreds of millions of parameters, yet the preprocessing choices that underlie them, including gene ranking and library-size normalisation, have not been systematically benchmarked. Testing seven strategies, we find these elaborations are largely unnecessary: non-normalised, log-transformed counts give the best performance, and gene order barely matters, with even random ordering outperforming sophisticated rank-based schemes. The resulting model, Gene Intelligence, projects log1p-transformed raw counts directly onto each token embedding and jointly predicts masked tokens and counts, using no normalisation, positional encoding, or read-depth tokens. Despite this simplicity, it achieves state-of-the-art performance in the tested gene-level tasks and in doublet detection, and matches large current foundation models on cell-classification tasks while using 10- to 200-fold fewer parameters.