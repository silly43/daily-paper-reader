---
title: Self-supervised Internal Learning Enhances Isotropic Resolution for Three-dimensional Fluorescence Microscopy
title_zh: 自监督内部学习增强三维荧光显微镜的等向分辨率
authors: "Wei, M., Xu, P., Liu, J., Li, X., Feng, X., Zhu, J., Dong, R., Ran, H., Zhu, W., Han, Y., Li, Y., Guo, M., Liu, H."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.717237v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 自监督内部学习用于各向同性恢复
tldr: 三维荧光显微镜因轴向采样不足和模糊导致各向异性分辨率，影响精细结构定量分析。现有方法依赖精确系统标定或PSF模型，难以普适。本文提出DeepIso自监督内部学习框架，耦合监督预训练与内部推理，直接估计退化，无需显式PSF或结构等效假设。该方法恢复轴向频率，改善细长结构连续性，在共聚焦、光片及3D-SIM等数据上性能优于现有方法，支持下游分割与追踪分析。
source: biorxiv
selection_source: fresh_fetch
motivation: 三维荧光显微镜轴向分辨率低下，现有光学计算恢复方法依赖精确校准或PSF模型，难以通用。
method: DeepIso结合监督预训练与内部学习，直接从测量体积估计退化，无需PSF或结构等效假设。
result: 在合成和实验数据集上，恢复轴向高频，改善结构连续性，定量指标超越现有方法。
conclusion: 提出自监督框架，无需先验，提升三维显微镜各向同性，适用于多种模态，支持下游定量分析。
---

## 摘要
三维荧光显微镜通常呈现各向异性分辨率，因为轴向信息采样不足且比横向信息更模糊，这使精细三维结构的定量解释复杂化。虽然已探索了光学补救措施和计算复原方法，但许多方法要求严格的系统校准，或依赖于精确的PSF模型及难以在所有样本和模态中满足的假设。这里我们提出DeepIso，一个自监督等向性复原框架，它结合了监督预训练与内部学习推理阶段，直接从测量体积估计退化。无需显式PSF说明或强制横向-轴向结构等价，DeepIso恢复轴向频率内容，改善细长结构的连续性，同时保留精细特征，在视觉检查和定量指标上均优于现有计算方法。该方法在合成基准和实验数据集上得到验证，展示了在共聚焦、光片和三维结构光照明显微镜中的等向性增强，从而支持包括分割和跟踪在内的下游体积分析。

## Abstract
Three-dimensional fluorescence microscopy often exhibits anisotropic resolution because axial information is poorly sampled and more blurred than lateral information, which complicates quantitative interpretation of fine 3D structures. Although optical remedies and computational restoration have been explored, many approaches require demanding system calibration or rely on accurate PSF models and assumptions that are difficult to satisfy across all samples and modalities. Here we present DeepIso, a self-supervised isotropy restoration framework that couples supervised pretraining with an internal-learning inference stage to estimate degradation directly from the measured volume. Without explicit PSF specification or enforced lateral-axial structural equivalence, DeepIso recovers axial frequency content and improves the continuity of elongated structures while retaining fine features, with superior performance over existing computational approaches in terms of both visual inspection and quantitative metrics. The method is validated on synthetic benchmarks and experimental datasets, demonstrating isotropy enhancement across confocal, light-sheet, and 3D structured illumination microscopy, thereby supporting downstream volumetric analysis including segmentation and tracking.