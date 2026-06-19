---
title: Topology-aware reconstruction of cellular state landscapes from microscopy using self-supervised learning
title_zh: 利用自监督学习从显微镜图像中实现拓扑感知的细胞状态景观重建
authors: "Messori, E., Taha, D. M., Fournier, L., Foix Romero, A., Uhlmann, V., Frossard, P., Vincent-Cuaz, C., Patani, R., Luisier, R."
date: 2026-06-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.30.728966v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 自监督学习用于从显微镜图像重建细胞状态景观
tldr: 从显微镜图像重建连续细胞状态景观面临挑战，尤其在高密度培养中。本文提出SI-SimCLR，一种空间自监督学习框架，无需分割或注释直接从荧光图像学习表征，并结合图部分最优传输重构静态图像中的细胞表型景观。在iPSC衍生星形胶质细胞多模态数据集上验证，SI-SimCLR分辨出与疾病和炎症相关的不同互连亚状态，ALS星形胶质细胞占据形态空间受限区域，且形态与转录组捕获细胞状态的互补信息。该框架为从显微镜数据无标注重建细胞表型景观提供了可扩展策略。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以从静态显微镜图像连续重建细胞状态景观，尤其缺乏无标注且保留空间信息的表征学习框架。
method: 提出SI-SimCLR自监督学习，利用空间邻近性增强表征，再结合图部分最优传输对齐连续表型景观。
result: SI-SimCLR在星形胶质细胞数据集上成功区分互连的炎性和疾病相关亚状态，ALS细胞形态景观受限。
conclusion: 该框架实现了无需标注的细胞表型景观重建，揭示了形态与转录组的互补性，适用于多种生物系统。
---

## 摘要
形态学和空间组织提供了细胞状态的互补读数。然而，从成像数据重建连续的细胞状态景观仍然具有挑战性，尤其是在密集的生物培养物中。在此，我们提出了SI-SimCLR，一个空间感知的自监督学习框架，它直接从荧光显微镜图像中学习具有生物学信息的表示，无需分割或人工标注。结合基于图的局部最优传输框架，SI-SimCLR能够从静态成像数据重建细胞表型景观，揭示表型亚状态如何组织和连接。为了建立和验证该框架，我们使用高内涵成像和匹配的批量转录组学生成了人iPSC来源星形胶质细胞的多模态数据集。SI-SimCLR解析了与疾病和炎症状态相关的不同且相互连接的星形胶质细胞亚状态。ALS星形胶质细胞占据了形态景观的受限区域。引人注目的是，形态学和转录组学捕捉了星形胶质细胞状态变异的独特且互补的方面。总之，我们的框架建立了一种可扩展且无需标注的策略，用于从显微镜数据重建细胞表型景观，从而能够分析跨生物系统的细胞异质性、景观连通性和表型响应。

## Abstract
Morphology and spatial organisation provide complementary readouts of cellular state. However, reconstructing continuous cellular state landscapes from imaging data remains challenging, particularly in dense biological cultures. Here we present SI-SimCLR, a spatially informed self-supervised learning framework that learns biologically informative representations directly from fluorescence microscopy images without requiring segmentation or manual annotation. Combined with a graph-based partial optimal transport framework, SI-SimCLR enables reconstruction of cellular phenotypic landscapes from static imaging data, revealing how phenotypic substates are organised and connected. To establish and validate this framework, we generated a multimodal dataset of human iPSC-derived astrocytes using high-content imaging and matched bulk transcriptomics. SI-SimCLR resolved distinct interconnected astrocyte substates associated with disease and inflammatory states. ALS astrocytes occupied constrained regions of the morphological landscape. Strikingly, morphology and transcriptomics captured distinct and complementary aspects of astrocyte state variation.Together, our framework establishes a scalable and annotation-free strategy for reconstructing cellular phenotypic landscapes from microscopy data, enabling analysis of cellular heterogeneity, landscape connectivity and phenotypic responses across biological systems.