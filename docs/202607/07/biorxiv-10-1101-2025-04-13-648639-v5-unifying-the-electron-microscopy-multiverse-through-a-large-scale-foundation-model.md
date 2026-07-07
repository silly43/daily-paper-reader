---
title: Unifying the Electron Microscopy Multiverse through a Large-scale Foundation Model
title_zh: 通过大规模基础模型统一电子显微镜多元宇宙
authors: "He, L., Shi, R., Wang, W., Fang, G., Cai, Y., Ma, L."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.1101/2025.04.13.648639v5.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 电子显微镜的自监督视觉表示学习
tldr: 电子显微镜图像分析受限于数据异质性与碎片化流程，难以实现规模化洞察。本研究构建了包含500万张图像的大规模标准化EM数据集EM-5M，涵盖多种物种、组织、协议和分辨率，并预训练了首个EM基础模型EM-DINO。EM-DINO的多尺度嵌入捕获丰富特征，支持器官模式识别、图像去重和高质量恢复。基于这些表示，进一步开发了统一密集预测架构OmniEM，在图像恢复任务中性能匹配专有扩散模型且有效减少结构假象，在2D/3D线粒体分割和多类细胞器分割上均超越先前方法。更重要的是，OmniEM能从低分辨率输入生成高质量分割，适用于高通量数据集。结合Napari插件，该端到端工具包为标准化EM分析提供了全面方案，推动亚细胞结构理解并加速新细胞器形态和疾病相关变化的发现。
source: biorxiv
selection_source: fresh_fetch
motivation: 当前EM图像分析因数据异质性和碎片化工作流难以规模化，缺乏能学习跨任务可迁移表征的通用基础模型。
method: 构建含500万图像的标准化数据集EM-5M，预训练首个EM基础模型EM-DINO，并基于其多尺度嵌入开发统一架构OmniEM，实现密集预测任务统一。
result: OmniEM在图像恢复中性能与专有扩散模型相当且假象更少，在2D/3D线粒体及多类细胞器分割任务上超越先前方法；并支持低分辨率输入生成高分辨率分割。
conclusion: EM-5M、EM-DINO、OmniEM及Napari插件形成完整工具包，提供标准化EM分析流程，有助于揭示新细胞器形态和疾病相关变化。
---

## 摘要
电子显微镜图像的精确分析对于探索纳米尺度的生物结构至关重要，但数据异质性和碎片化工作流程阻碍了可扩展的洞察。基于大规模多样化数据集预训练的影像基础模型为跨任务学习可迁移表示提供了稳健框架。在此，我们介绍EM-DINO——首个基于EM-5M（一个经过精心整理和标准化、包含500万张图像，涵盖多物种、组织、方案和分辨率的电子显微镜语料库）预训练的电子显微镜图像基础模型。EM-DINO的多尺度嵌入捕捉到丰富的图像特征，支持多种应用，包括器官特异性模式识别、图像去重和高质量图像恢复。基于这些表示，我们开发了OmniEM，一种用于统一密集预测的U形架构，在图像恢复和分割任务中均优于任务特定模型。在恢复基准测试中，OmniEM匹配了电子显微镜专用扩散模型的性能，同时减少了可能误导解读的伪结构伪影。在2D和3D线粒体分割以及多类细胞器分割任务中，它也优于先前方法。此外，我们展示了OmniEM从低分辨率输入生成高分辨率分割的综合能力，为传统和高通量电子显微镜数据集中的精细亚细胞分析提供了潜力。EM-5M、EM-DINO、OmniEM以及集成的Napari插件共同构成了一套标准化的电子显微镜分析端到端工具包，推进了细胞和亚细胞层面的理解，加速了新细胞器形态和疾病相关改变的发现。

## Abstract
Accurate analysis of electron microscopy (EM) images is essential for exploring nanoscale biological structures, yet data heterogeneity and fragmented workflows hinder scalable insights. Pretrained on large, diverse datasets, image foundation models provide a robust framework for learning transferable representations across tasks. Here, we introduce EM-DINO, the first EM image foundational model pretrained on EM-5M, a large curated and standardized EM corpus (5 million images) encompassing multiple species, tissues, protocols, and resolutions. EM-DINOs multi-scale embeddings capture rich image features that support multiple applications, including organ-specific pattern recognition, image deduplication, and high quality image restoration. Building on these representations, we developed OmniEM, a U-shaped architecture for unified dense prediction that achieves superior performance compared with task-specific models in both image restoration and segmentation. In restoration benchmarks, OmniEM matches the performance of the EM-specific diffusion model while reducing spurious structural artifacts that could mislead interpretation. It also outperforms previous methods across 2D and 3D mitochondrial segmentation, as well as multi-class organelle segmentation tasks. Furthermore, we demonstrate OmniEMs integrated capability to generate high-resolution segmentations from low-resolution inputs, offering the potential to enable fine-scale subcellular analysis in legacy and high-throughput EM datasets. Together, EM-5M, EM-DINO, OmniEM, and an integrated Napari plugin comprise a comprehensive end-to-end toolkit for standardized EM analysis, advancing cellular and subcellular understanding and accelerating the discovery of novel organelle morphologies and disease-related alterations.