---
title: Finetuning masking challenges narrow-task evaluation of cell foundation models
title_zh: 微调掩盖效应对细胞基础模型窄任务评估的挑战
authors: "Shakeel, M. H., Shen, M., Mangiola, S."
date: 2026-06-06
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.730272v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 自监督深度学习网络预训练于细胞转录组
tldr: 单细胞基础模型通过自监督预训练于海量转录组数据，期望更大预训练规模带来更好下游性能。然而，在标准微调基准任务上，性能对预训练数据量不敏感，微调掩盖了预训练表示质量的差异。这挑战了当前基于封闭式微调任务的评估范式，并质疑预训练数据规模的重要性。未来应转向开放推断、冻结表示评估和零样本能力等更全面的评测。
source: biorxiv
selection_source: fresh_fetch
motivation: 检验细胞基础模型预训练数据量越大下游性能越好的核心假设是否成立。
method: 在黄金标准基准任务上，对大规模缩减预训练数据后的模型进行微调测试性能。
result: 微调后性能对预训练数据量变化不敏感，存在微调掩盖效应。
conclusion: 当前窄任务评估无法充分反映预训练价值，需引入开放推断和零样本能力等更全面的评测方式。
---

## 摘要
单细胞基础模型是在数百万个细胞转录组上预训练的大型自监督深度学习网络。这些模型有望提供可跨多种生物领域迁移的细胞表示，并且在特定任务中使用时，其性能将优于范围狭窄的模型。一个核心假设是，更多的预训练数据会带来更好的下游性能。然而，尽管这一假设至关重要，但它基本上未经检验。在此，我们在大量数据集缩减的情况下，对黄金标准基准任务的下游性能进行了测试，结果表明，一旦允许微调，性能对预训练数据规模基本不敏感。这一趋势揭示了一种微调掩盖效应，它抵消了预训练引起的表示质量差异，使得在当前基准设置下，额外预训练规模带来的益处基本不可见。这些发现挑战了当前的基准测试标准，该标准依赖于封闭式的微调任务，这些任务过于狭窄，无法暴露预训练的全部表示价值。它们也挑战了通过常见窄任务评估时，单细胞基础模型开发的主要驱动力。我们建议，下一代基础模型的评估应较少依赖其在高度优化的微调任务上的表现，而更多地关注其支持开放式生物推断、冻结表示评估和零样本能力的能力。

## Abstract
Single-cell foundation models are large, self-supervised deep learning networks pretrained on millions of cellular transcriptomes. These models promise to deliver cell representations that are transferable across diverse biological domains and, when used in specific tasks, would outperform narrowly scoped models. A central assumption is that more pretraining data translates to better downstream performance. However, despite its centrality, this assumption remains largely untested. Here, we tested downstream performance on gold-standard benchmarking tasks across massive dataset reductions, showing that performance was largely insensitive to pretraining data size once finetuning was allowed. This trend reveals a finetuning masking effect that offsets differences in representation quality induced by pretraining, making the benefit of additional pretraining scale largely invisible under current benchmark settings. These findings challenge current benchmarking standards, which rely on closed-ended finetuning tasks that are too narrow to expose the full representational value of pretraining. They also challenge the main driving force in single-cell foundation-model development when evaluated through common narrow tasks. We propose that the next generation of foundation models should be assessed less by performance on highly optimised finetuning tasks and more by their ability to support open-ended biological inference, frozen-representation evaluation and zero-shot capability.