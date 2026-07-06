---
title: Generative cell phenotyping with structured latent populations
title_zh: 基于结构化潜在群体的生成式细胞表型分析
authors: "Bodart, F., De Voeght, A., Baron, F., Louppe, G."
date: 2026-07-03
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735507v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 半监督变分自编码器结合高斯混合先验用于细胞表型生成，属于生成式自监督学习
tldr: "流式细胞术产生高维单细胞数据，但分析仍依赖人工设门，可重复性差且不适合大标记面板。现有计算方法将分类与发现割裂，未将细胞类型身份融入生成模型。本文提出MARVIN，一种半监督变分自编码器，通过在潜在空间施加高斯混合先验，假设细胞组织为离散群体且内部连续变异。仅需10%标记细胞即可达到或超越现有方法；在健康样本上训练后，能通过重构误差无监督检测白血病细胞；在配对刺激数据中稳定识别群体并捕捉条件特异性变化。MARVIN是开源、可本地部署的框架，统一了分类、发现与密度估计。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有流式细胞术分析依赖人工设门，效率低且可重复性差；计算法将分类与发现割裂，未将细胞类型身份纳入生成模型。
method: MARVIN采用半监督变分自编码器，潜在空间使用高斯混合先验，每个分量对应一个细胞群体，实现分类、发现与密度估计的联合学习。
result: "在公开基准上仅用10%标记细胞即达顶尖性能；健康样本训练后通过重构误差无监督识别白血病细胞；刺激数据中保持稳定分配并捕捉条件特异性变化。"
conclusion: MARVIN作为开源、可本地部署框架，将细胞表型分析中的分类、发现和异常检测统一为生成模型的一部分，提升了可重复性和实用性。
---

## 摘要
流式细胞术能够产生高维单细胞蛋白测量数据，是免疫表型分析和临床监测的核心技术。然而，其分析仍主要依赖人工设门，这一过程劳动密集、可重复性差，且难以适应大规模标记物组合。现有计算方法孤立地处理分类或发现任务，将细胞类型身份视为事后标注而非生成模型本身的组成部分。我们提出MARVIN——一种半监督变分自编码器，通过在潜在空间中引入高斯混合先验，编码了细胞组织成具有连续群体内变异性的离散群体的假设。由于每个分量代表一个不同的细胞群体，分类、发现和密度估计成为同一表征的互补视角。在公共基准测试中，MARVIN仅使用10%的标记细胞即可达到或超越现有方法的性能。仅用健康样本训练后，它能通过重建误差升高识别白血病细胞，提供无监督异常检测信号。在配对刺激数据上，MARVIN在捕捉患者层面丰度和标记物表达的条件特异性变化的同时，保持稳定的群体分配。MARVIN是开源的，专为本地部署设计，可适应机构特定的标记物组合和仪器。

## Abstract
Flow cytometry produces high-dimensional single-cell protein measurements central to immunophenotyping and clinical monitoring. Yet analysis still relies largely on manual gating, which is labour-intensive, poorly reproducible, and ill-suited to large marker panels. Existing computational approaches address classification or discovery in isolation, treating cell-type identity as a post-hoc annotation rather than as part of the generative model itself. We present MARVIN, a semi-supervised variational autoencoder that encodes the assumption that cells organise into discrete populations with continuous intra-population variability through a Gaussian mixture prior in the latent space. Because each component represents a distinct cell population, classification, discovery, and density estimation emerge as complementary views of the same representation. On public benchmarks, MARVIN matches or exceeds existing methods using as few as 10% labelled cells. Trained exclusively on healthy samples, it identifies leukaemic cells through elevated reconstruction error, providing an unsupervised anomaly detection signal. On paired stimulation data, it maintains stable population assignments while capturing condition-specific shifts in abundance and marker expression at patient-level resolution. MARVIN is open-source and designed for local deployment, adapting to institution-specific panels and instruments