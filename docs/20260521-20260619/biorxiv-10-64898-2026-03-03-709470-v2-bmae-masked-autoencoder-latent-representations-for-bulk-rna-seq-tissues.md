---
title: "bMAE: Masked Autoencoder Latent Representations for Bulk RNA-seq Tissues"
title_zh: bMAE：针对批量RNA-seq组织的掩码自编码器潜在表示
authors: "Wan, Z., Untalan, M. Z. G., Vasconcellos Vargas, D."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.03.709470v2.full.pdf"
tags: ["query:ssl"]
score: 9.0
evidence: 用于批量RNA-seq数据的掩蔽自编码器自监督学习
tldr: 针对批量RNA-seq数据的高维性和噪声问题，提出bMAE掩码自编码器，通过可变掩码调度的自监督学习压缩潜在表示。在GTEx数据上，LOTO验证中轮廓系数、ARI、NMI分别比最佳基线UMAP提升28.6倍、2.3倍、1.8倍，并能发现未训练过的子组织层次结构。该方法将19308基因高效压缩至128维，保留多尺度生物学信息。
source: biorxiv
selection_source: fresh_fetch
motivation: 批量RNA-seq数据高维且存在技术噪声，标准降维方法无法最优保留组织判别信息，且泛化性差。
method: 提出bMAE，使用可变掩码调度的掩码自编码器，对批量RNA-seq数据进行自监督学习，得到128维潜在表示。
result: 在GTEx数据集上，LOTO验证中bMAE比UMAP提升轮廓系数28.6倍（0.20 vs 0.007），ARI 2.3倍（0.58 vs 0.25），NMI 1.8倍（0.84 vs 0.47），并增强子组织分离。
conclusion: bMAE有效压缩批量RNA-seq数据至低维潜在空间，保留组织判别和层次结构，优于现有方法。
---

## 摘要
大规模联盟（如GTEx）的批量组织RNA测序数据提供了跨多种人类组织的全面基因表达谱。然而，批量RNA-seq数据的高维特性，结合技术噪声和批次效应，给下游分析带来了挑战。尽管降维方法被常规应用，但PCA等标准方法往往无法最优保留组织判别信息，并且对未见组织类型的泛化能力较差。我们开发了一种针对批量组织RNA-seq的掩码自编码器，通过具有可变掩码策略的自监督学习来学习压缩潜在表示。在GTEx数据（31种组织类型，19,788个样本，19,308个基因）上评估，我们的方法在留一组织法交叉验证中显著优于所有基线。我们实现了平均轮廓系数0.20、ARI 0.58和NMI 0.84，而最佳基线UMAP为（0.007、0.25、0.47），分别提升了28.6倍、2.3倍和1.8倍。值得注意的是，在包含子组织的保留组织类别中，我们的潜在空间揭示了层次结构，并增强了子组织分离（轮廓系数0.16、ARI 0.35、NMI 0.36），而基线为（轮廓系数0.15、ARI 0.20、NMI 0.20），尽管训练过程中从未观察到这些区别。该方法将19,308个基因压缩至128维，同时保留了多尺度结构。

## Abstract
Bulk tissue RNA-sequencing data from large-scale consortia such as GTEx provide comprehensive gene expression profiles across diverse human tissues. However, the high-dimensional nature of bulk RNA-seq data, combined with technical noise and batch effects, poses challenges for downstream analyses. While dimensionality reduction methods are routinely applied, standard approaches such as PCA often fail to optimally preserve tissue-discriminative information and exhibit poor generalization to unseen tissue types. We developed a masked autoencoder for bulk tissue RNA-seq that learns compressed latent representations through self-supervised learning with variable masking schedules. Evaluated on GTEx data (31 tissue types, 19,788 samples, 19,308 genes), our method substantially outperformed all baselines in leave-one-tissue-out (LOTO) cross-validation. We achieved mean silhouette 0.20, ARI 0.58, and NMI 0.84 versus best baseline UMAP (0.007, 0.25, 0.47), representing 28.6-fold, 2.3-fold, and 1.8-fold improvements. Remarkably, within held-out tissue categories containing subtissues, our latent space revealed hierarchical structure with enhanced subtissue separation (silhouette 0.16, ARI 0.35, NMI 0.36) versus baselines (silhouette 0.15, ARI 0.20, NMI 0.20), despite never observing these distinctions during training. The method compressed 19,308 genes to 128 dimensions while preserving multi-scale structure.