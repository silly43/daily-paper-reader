---
title: WattmaMod enables high-resolution and extensible RNA modification profiling for nanopore direct RNA sequencing
title_zh: WattmaMod支持纳米孔直接RNA测序的高分辨率和可扩展的RNA修饰分析
authors: "Han, R., Yu, B., Xinghui, S., Xiao, L., Junhai, Q., Ting, Y., Xin, G."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.02.735990v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 使用自监督预训练和对比微调
tldr: 针对纳米孔直接RNA测序中多修饰检测精度低、信号非平稳等问题，提出WattmaMod框架。它采用自监督预训练、对比微调与低标签增量适应提升表征，结合小波多尺度编码和动态交叉注意力融合原始信号与事件特征。在m6A等11种修饰上表现鲁棒，高效扩展至低资源类型，跨化学和物种泛化，并预测修饰间高阶组织。该工作为高分辨率表观转录组分析及多修饰协同研究提供了可扩展方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以从纳米孔直接RNA测序非平稳信号中准确检测多种RNA修饰，且缺乏对低资源修饰类型的可扩展性。
method: 结合自监督预训练、监督对比微调与低标签增量适应，并引入小波引导多尺度编码和动态交叉注意力融合原始信号与事件特征。
result: 在m6A等11种修饰上实现鲁棒检测，高效扩展至低资源类型，跨化学和物种泛化，并揭示修饰间局部组织关系。
conclusion: WattmaMod开创了高分辨率、可扩展的多修饰协同分析框架，推动RNA修饰研究从单点预测走向系统表征。
---

## 摘要
纳米孔直接RNA测序能够直接分析天然转录本上的RNA修饰，但由于非平稳信号和化学试剂的异质性，准确的多重修饰检测仍然受到限制。在此，我们开发了WattmaMod，这是一个用于从纳米孔直接RNA测序数据中检测多重修饰的深度学习框架。它结合了自监督预训练、监督对比微调和低标签增量自适应，以改进表示学习并支持对低资源修饰类型的有效扩展。该框架进一步引入了小波引导的多尺度编码和动态交叉注意力融合，以对原始信号和事件级特征进行建模。结果表明，WattmaMod能够稳健地检测多种RNA修饰，包括m6A、m5C、m1A、A-to-I、m7G、hm5C、m1{Ψ}、f5C、ac4C、m5U和{Ψ}。它还能以最少的标记数据高效扩展到低资源修饰类型，并适用于不同的测序化学试剂和物种，同时预测不同RNA修饰之间潜在的高阶局部组织。因此，WattmaMod为高分辨率表观转录组分析提供了一个可扩展的框架，并将RNA修饰分析从单一位点预测扩展到协调的多重修饰表征。

## Abstract
Nanopore direct RNA sequencing enables direct profiling of RNA modifications on native transcripts, but accurate multi-modification detection remains limited by non-stationary signals and heterogeneity across chemistries. Here, we develop WattmaMod, a deep learning framework for multi-modification detection from nanopore direct RNA sequencing data. It combines self-supervised pretraining, supervised contrastive fine-tuning, and low-label incremental adaptation to improve representation learning and support efficient extension to low-resource modification types. The framework further incorporates wavelet-guided multi-scale encoding and dynamic cross-attention fusion to model raw signals and event-level features. Results show that WattmaMod achieves robust detection of multiple RNA modifications, including m6A, m5C, m1A, A-to-I, m7G, hm5C, m1{Psi}, f5C, ac4C, m5U and {Psi}. It also extends efficiently to low-resource modification types with minimal labeled data, generalizes across sequencing chemistries and species, and predicts potential higher-order local organization among distinct RNA modifications. WattmaMod thus provides a scalable framework for high-resolution epitranscriptome profiling and expands RNA modification analysis beyond single-site prediction to coordinated multi-modification characterization.