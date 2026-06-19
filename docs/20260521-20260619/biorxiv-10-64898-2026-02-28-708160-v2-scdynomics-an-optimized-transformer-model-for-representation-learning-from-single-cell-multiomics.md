---
title: "scDynOmics: An Optimized Transformer Model for Representation Learning from Single-Cell Multiomics"
title_zh: scDynOmics：一种用于单细胞多组学表示学习的优化Transformer模型
authors: "Yu, G., Ramnarine, T. J. S., Klughammer, J., Mages, S. W."
date: 2026-05-24
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.28.708160v2.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 使用Transformer对单细胞多组学进行自监督表示学习
tldr: 单细胞基础模型常消耗大量资源但性能不稳定。scDynOmics采用Linformer注意力机制处理全基因组多组学输入，在配对转录组和染色质可及性数据上预训练，生成紧凑高保真细胞嵌入。通过低秩适应微调，它在多个下游任务中大幅超越现有模型，达到或超越简单方法，并提供可解释的发育与扰动因子。该框架高效、可扩展、灵活且可解释。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞基础模型资源消耗大且性能不如简单方法，亟需高效、可扩展且可解释的多组学表征模型。
method: 采用Linformer注意力降低复杂度，预训练于配对转录组和染色质可及性数据，使用低秩适应模块进行参数高效微调。
result: 在多种下游任务中大幅超越现有单细胞基础模型，性能媲美或超越简单方法，同时提取可解释的发育和扰动响应因子。
conclusion: scDynOmics提供了高效、可扩展、灵活且可解释的框架，用于单细胞多组学表征，解析细胞异质性与动态。
---

## 摘要
随着基础模型在多个领域的广泛应用，利用单细胞转录组数据预训练模型引起了广泛关注。尽管现有的单细胞基础模型已证明基于Transformer的设计可应用于各种生物学任务，但与更简单的方法相比，它们并未持续展现出具有竞争力的性能，同时需要更多的数据和计算资源。为此，我们提出了scDynOmics，一种可预训练、支持多组学的Transformer模型，用于从单细胞数据中学习表示。该模型受基因调控网络启发，不排除基因间未知的相互作用，并采用Linformer风格的注意力机制，以扩展到编码基因组范围内的多模态输入。在配对的单细胞转录组和染色质可及性数据上的预训练生成了紧凑且高保真的嵌入，这些嵌入代表了细胞状态和发育动态。为实现多功能应用，scDynOmics采用了低秩适应模块，支持下游任务的参数高效微调。我们证明，scDynOmics大幅优于现有的单细胞基础模型，并在性能上达到或超越了更简单的方法，同时揭示了驱动发育轨迹和扰动响应的可解释因素，而更简单的方法无法提供这些信息。总体而言，scDynOmics是一个高效、可扩展、灵活且可解释的框架，用于细胞表示学习以及解析细胞异质性与动态。

## Abstract
As foundation models have become increasingly prevalent in several fields for multiple purposes, pretraining models with single-cell transcriptomic data has gained significant interest. Although existing single-cell foundation models have demonstrated that transformer-based designs can be applied to various biological tasks, they do not show consistently competitive performance compared to much simpler approaches while requiring much more resources in terms of data and compute. Here, we introduce scDynOmics, a pretrainable multiomics-capable transformer for representation learning from single-cell data. The model is motivated by gene regulatory networks without excluding unknown interactions between genes and adopts a Linformer-style attention mechanism to scale to coding-genome wide multimodal inputs. Pretraining on paired single-cell transcriptomic and chromatin accessibility profiles yields compact high-fidelity embeddings that represent cellular states and developmental dynamics. For versatile application, scDynOmics employs low-rank adaptation modules, enabling parameter-efficient fine-tuning for downstream tasks. We demonstrate that scDynOmics outperforms existing single-cell foundation models by a large margin and achieves or surpasses state-of-the-art performance compared to simpler approaches, while revealing interpretable factors driving developmental trajectories and perturbation responses that simpler approaches cannot provide. Overall, scDynOmics is an efficient, scalable, flexible, and interpretable framework for cellular representation learning and deciphering cellular heterogeneity and dynamics.