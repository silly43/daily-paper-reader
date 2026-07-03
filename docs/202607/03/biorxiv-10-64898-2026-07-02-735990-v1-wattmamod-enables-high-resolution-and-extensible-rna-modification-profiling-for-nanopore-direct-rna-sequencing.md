---
title: WattmaMod enables high-resolution and extensible RNA modification profiling for nanopore direct RNA sequencing
title_zh: WattmaMod实现纳米孔直接RNA测序的高分辨率、可扩展的RNA修饰分析
authors: "Han, R., Yu, B., Xinghui, S., Xiao, L., Junhai, Q., Ting, Y., Xin, G."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.02.735990v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 自监督预训练和对比微调用于RNA修饰检测
tldr: 纳米孔直接RNA测序可检测天然转录本上的RNA修饰，但现有方法在多修饰准确性和低资源类型扩展上存在局限。本文提出WattmaMod，结合自监督预训练、对比微调、低标签增量适应及小波引导多尺度编码与动态交叉注意力融合，实现对m6A、m5C等11种修饰的稳健检测。该方法高效扩展至低资源修饰，跨测序化学和物种泛化，并预测修饰间高阶局部组织。WattmaMod提供了高分辨率、可扩展的表观转录组分析框架，将单点预测扩展至多修饰协同表征。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有纳米孔RNA修饰检测方法难以同时准确识别多种修饰，且对低资源修饰类型的可扩展性差。
method: 提出WattmaMod，融合自监督预训练、监督对比微调、低标签增量适应以及小波引导多尺度编码与动态交叉注意力。
result: 在11种RNA修饰上实现稳健检测，高效扩展至低资源类型，并跨测序化学和物种泛化。
conclusion: WattmaMod构建了高分辨率、可扩展的表观转录组分析框架，实现从单点预测到多修饰协同表征的扩展。
---

## 摘要
纳米孔直接RNA测序能够直接分析天然转录本上的RNA修饰，但准确的多种修饰检测仍受非平稳信号和不同化学试剂间异质性的限制。在此，我们开发了WattmaMod，一个用于从纳米孔直接RNA测序数据中检测多种修饰的深度学习框架。它结合了自监督预训练、监督对比微调和低标签增量自适应，以改进表示学习并支持高效扩展到低资源修饰类型。该框架进一步整合了小波引导的多尺度编码和动态交叉注意力融合，以建模原始信号和事件级特征。结果表明，WattmaMod实现了多种RNA修饰的稳健检测，包括m6A、m5C、m1A、A-to-I、m7G、hm5C、m1Ψ、f5C、ac4C、m5U和Ψ。它还能以最少的标记数据高效扩展到低资源修饰类型，跨测序化学试剂和物种泛化，并预测不同RNA修饰之间潜在的高阶局部组织。因此，WattmaMod为高分辨率表观转录组分析提供了一个可扩展的框架，并将RNA修饰分析从单一位点预测扩展到协调的多修饰表征。

## Abstract
Nanopore direct RNA sequencing enables direct profiling of RNA modifications on native transcripts, but accurate multi-modification detection remains limited by non-stationary signals and heterogeneity across chemistries. Here, we develop WattmaMod, a deep learning framework for multi-modification detection from nanopore direct RNA sequencing data. It combines self-supervised pretraining, supervised contrastive fine-tuning, and low-label incremental adaptation to improve representation learning and support efficient extension to low-resource modification types. The framework further incorporates wavelet-guided multi-scale encoding and dynamic cross-attention fusion to model raw signals and event-level features. Results show that WattmaMod achieves robust detection of multiple RNA modifications, including m6A, m5C, m1A, A-to-I, m7G, hm5C, m1{Psi}, f5C, ac4C, m5U and {Psi}. It also extends efficiently to low-resource modification types with minimal labeled data, generalizes across sequencing chemistries and species, and predicts potential higher-order local organization among distinct RNA modifications. WattmaMod thus provides a scalable framework for high-resolution epitranscriptome profiling and expands RNA modification analysis beyond single-site prediction to coordinated multi-modification characterization.