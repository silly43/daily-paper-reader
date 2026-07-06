---
title: Integrating morphology and gene expression of neural cells in unpaired single-cell data using GeoAdvAE
title_zh: 使用GeoAdvAE整合非配对单细胞数据中神经细胞的形态和基因表达
authors: "Du, J. T., Chartrand, T., Jayadev, S., Prater, K. E., Lin, K. Z."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.1101/2025.11.19.689368v3.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 基于几何感知对抗自编码器的非配对表征学习
tldr: 单细胞形态与转录组因测量技术不同而难以关联。本文提出GeoAdvAE，利用几何感知对抗自编码器整合非配对的形态和RNA-seq数据。在patch-seq神经元上取得最佳跨模态细胞类型匹配，并在5xFAD阿尔茨海默病模型小胶质细胞中恢复形态-转录组轴，识别了DNA修复、细胞杀伤等转录组变化及Ms4a6b等基因标记。该方法为难以同时测量形态和转录组的研究提供了可扩展的整合方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 单细胞形态和转录组难以同时测量，现有方法无法整合非配对数据，阻碍了揭示形态与功能关联。
method: GeoAdvAE通过模态特定变分自编码器、Gromov-Wasserstein正则化和对抗判别器，将非配对形态和转录组嵌入共享潜在空间，同时保持重建保真度和跨模态几何结构。
result: 在patch-seq神经元上跨模态细胞类型匹配准确率最优；在5xFAD模型小胶质细胞中恢复了一维形态-转录组轴，并识别出DNA修复（分枝状）和细胞杀伤（阿米巴状）相关基因标记如Ms4a6b、Ftl1/Fth1。
conclusion: GeoAdvAE提供了可扩展、可解释的形态-转录组整合方法，揭示了疾病相关小胶质细胞特征与形态解耦的现象。
---

## 摘要
背景在许多疾病中观察到细胞形态转变，但由于很少有技术在同一细胞中同时分析形态和功能，这些转变的功能作用仍不清楚。将单细胞形态与转录组学联系起来很困难：这两种模态之间没有特征对应关系，并且通常在不同细胞中测量。
方法我们提出GeoAdvAE，一种几何感知对抗自编码器，用于单细胞形态和单细胞RNA测序的对角线（非配对）整合。GeoAdvAE将模态特异性变分自编码器与Gromov-Wasserstein正则化器和对抗判别器相结合，将非配对的形态和转录组嵌入到一个共享潜在空间中，同时保持重构保真度和跨模态几何结构。
结果使用具有联合形态-RNA测量的patch-seq神经元作为真实数据，在对角线整合方法中，GeoAdvAE实现了最佳的跨模态细胞类型匹配准确性，优于最优传输、潜在对齐和对抗基线。应用于来自5xFAD阿尔茨海默病模型的98个CAJAL定量小胶质细胞形态和31,948个单细胞转录组，GeoAdvAE恢复了一个排列两种模态的一维轴。积分梯度归因突出了转录组变化（分支状小胶质细胞中的DNA修复；阿米巴样小胶质细胞中的细胞杀伤），提名了基因标记物（Ms4a6b；Ftl1/Fth1），并揭示了与形态解耦的疾病相关小胶质细胞特征。
结论当形态和转录组的联合分析不可行时，GeoAdvAE提供了一种可扩展且可解释的方法来连接细胞的“形态”和“功能”。我们的方法公开可用，网址为https://github.com/turbodu222/GeoAdVAE。

## Abstract
BackgroundCellular morphological transitions are observed across many diseases, yet their functional role remains unclear because few technologies profile form and function in the same cell. Linking single-cell morphology to transcriptomics is difficult: the two modalities share no feature correspondence and are typically measured in different cells.

MethodsWe present GeoAdvAE, a geometry-aware adversarial autoencoder for diagonal (unpaired) integration of single-cell morphology and single-cell RNA sequencing. GeoAdvAE couples modality-specific variational autoencoders with a Gromov-Wasserstein regularizer and an adversarial discriminator to embed unpaired morphologies and transcriptomes into a shared latent space that preserves both reconstruction fidelity and cross-modal geometry.

ResultsUsing patch-seq neurons with joint morphology-RNA measurements as ground truth, GeoAdvAE attains the best cross-modal cell-type matching accuracy among diagonal integration methods, outperforming optimal-transport, latent-alignment, and adversarial baselines. Applied to 98 CAJAL-quantified microglial morphologies and 31,948 single-cell transcriptomes from the 5xFAD Alzheimers disease model, GeoAdvAE recovers a one-dimensional axis that aligns the two modalities. Integrated-gradient attribution highlights transcriptomic shifts (DNA repair in ramified microglia; cell killing in amoeboid microglia), nominates gene markers (Ms4a6b; Ftl1 /Fth1), and reveals disease-associated microglia signatures that are decoupled from morphology.

ConclusionsGeoAd-vAE provides a scalable and interpretable approach to connecting cellular "form" and "function" when joint profiling of morphology and transcriptomics is impractical. Our method is publicly available at https://github.com/turbodu222/GeoAdVAE.