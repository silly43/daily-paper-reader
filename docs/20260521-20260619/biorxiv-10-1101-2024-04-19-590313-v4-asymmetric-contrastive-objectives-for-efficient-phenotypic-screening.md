---
title: Asymmetric Contrastive Objectives for Efficient Phenotypic Screening
title_zh: 非对称对比目标用于高效表型筛选
authors: "Nightingale, L., Tuersley, J., Warchal, S., Cairoli, A., Howes, J., Shand, C., Powell, A., Green, D., Strange, A., Howell, M."
date: 2026-05-22
pdf: "https://www.biorxiv.org/content/10.1101/2024.04.19.590313v4.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 用于表型筛选的非对称对比目标
tldr: 表型筛选实验中，细胞图像差异细微，传统方法难以提取有效表示。本文提出不对称对比损失，将实验元数据作为可学习的类向量，并推出SPC变体将类向量约束在单位球面仅通过吸引项更新。在BBBC021、RxRx3-core及HaCaT细胞数据上，该方法在表型分组、生物召回等指标上超越先前方法及大10倍参数模型。该方法简单高效，适用于数据或算力有限场景。
source: biorxiv
selection_source: fresh_fetch
motivation: 表型筛选中生物反应细微难识别，需提取区分活性与对照、聚类相似表型的图像表示。
method: 提出不对称对比损失，结合实验元数据作为类向量；SPC变体将类向量限制在单位球面，仅由吸引项更新以允许表型相似类重叠。
result: 在BBBC021、RxRx3-core及HaCaT细胞数据集上，表型分组、生物召回、药物靶点及机制推断等指标全面超越先前方法及大参数模型。
conclusion: 方法易于实现，在数据或资源有限场景下有效，且可作为微调技术提升性能。
---

## 摘要
表型筛选实验会产生大量在不同扰动条件下细胞的显微镜图像，其中具有生物学意义的响应通常较为微妙或难以通过视觉识别。一个核心挑战是提取能够区分活性物质与对照、并聚类表型相似扰动的图像表征。在本工作中，我们提出了对比损失函数的新适应方法，将实验元数据作为学习到的类向量，并引入一种几何启发变体SPC，其中类向量被限制在单位球面上，且仅通过吸引项更新（允许表型相似类别的更多重叠）。该方法在两个流行的基准数据集BBBC021和RxRx3-core上进行了测试；我们还在HaCaT细胞的非精选筛选中评估了性能，以衡量在真实使用场景中的有效性。我们发现，在三个数据集上以及一系列衡量表型分组、生物召回、药物-靶点相互作用和作用机制推断的指标中，我们的方法优于先前方法。我们还表明，相比于参数数量超过10倍以上的模型，我们保持了这种改进性能，并且SPC可以作为一种有效的微调技术。该方法易于实现，非常适合数据或计算资源有限的场景。

## Abstract
Phenotypic screening experiments produce many microscope images of cells under diverse perturbations, with biologically significant responses often subtle or difficult to identify visually. A central challenge is to extract image representations that distinguish activity from controls and group phenotypically similar perturbations. In this work we propose new adaptations of contrastive loss functions that incorporate experimental metadata as learned class vectors, and a geometrically inspired variant, called SPC, where class vectors are confined to the unit sphere and updated only by attractive terms (allowing more overlap of phenotypically similar classes). The approach is tested on two popular benchmarking datasets, BBBC021 and RxRx3-core; and we also evaluate performance on uncurated screens of HaCaT cells to gauge effectiveness in a realistic use-case scenario. We find we outperform prior methods across the three datasets and on a wide array of metrics measuring phenotype grouping, biological recall, drug-target interaction and mechanism-of-action inference. We also show we maintain this improved performance compared to models over 10x larger in parameter count, and that SPC can be used as an effective fine-tuning technique. The method is easy to implement and is well suited to settings with limited data or compute resources.