---
title: "RepGene: Toward a Unified Gene Representation Space Robust to Missing Biological Views"
title_zh: RepGene：迈向对缺失生物学视图鲁棒的统一基因表示空间
authors: "Hou, H., Xia, T., Hu, L., Qin, H., Zhang, Y., Li, Y., Fang, S., Cao, L."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731512v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 自监督表示学习用于基因嵌入
tldr: 基因多视图表征学习面临模态缺失难题。RepGene提出轻量级单分支框架，通过模态适配器、共享编码器与自监督跨视图目标，将序列、知识、表达等五种视图对齐到统一空间。线性探测评估显示，全模态性能有竞争力，且缺模态时鲁棒性显著，单视图推理仍保持非平凡表现。该工作作为可行性验证，为统一基因表示学习提供基准与起点。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基因嵌入多为模态特定，难以在视图缺失时比较或复用，亟需统一表示空间。
method: RepGene采用固定预训练嵌入，通过模态适配器、共享编码器、存在感知融合及自监督跨视图目标对齐五种生物视图。
result: 全模态线性探测性能优异，移除任一视图性能下降有限，甚至单视图推理仍保持有效。
conclusion: RepGene证明统一基因表示空间在缺失视图下具有鲁棒性，为后续研究提供可行性基准。
---

## 摘要
基因可以通过多种异质生物学视图来描述，包括基因组序列、转录本序列、蛋白质序列、文本知识和单细胞表达背景，然而现有的基因嵌入在很大程度上仍是模态特定的，并且当许多视图不可用时难以比较或重用。我们研究了一个更窄但实际重要的问题：来自这些不同来源的预训练嵌入能否被组织成一个共享的基因表示接口，该接口在严重缺失模态的条件下仍然可用。为了研究这个问题，我们引入了RepGene，一个轻量级的单分支框架，它结合了模态适配器、共享编码器、存在感知融合以及自监督跨视图目标，将五种生物学视图映射到一个潜在空间中。我们的目的不是声称一种新的多模态学习原则，也不是建立优于所有更简单融合策略的优越性，而是提供一个初步的技术实例，用于测试这种共享接口在固定特征设置中是否可行。在一种两阶段协议下，RepGene在冻结的上游嵌入上进行自监督训练，并通过下游线性探测进行评估，我们发现初步证据表明，所学习的表示在全模态设置中具有广泛竞争力，并且在推理时仅观察到部分模态子集时仍然保持信息量。我们研究中最强的信号是缺失视图下的鲁棒性：当移除一种模态时，平均性能变化通常有限，甚至在评估的基准测试体系中，单视图推理仍然具有相当的价值。这些结果并不能解决统一的生物学表示学习问题，并且应在不完整的简单融合基线、有限的结构消融、基准依赖性和可能的上游特征暴露的背景下进行解释。因此，我们将RepGene定位为一项可行性研究，并作为更强比较、更广泛基准和泄漏感知验证的起点。

## Abstract
Genes can be described through multiple heterogeneous biological views, including genomic sequence, transcript sequence, protein sequence, textual knowledge, and single-cell expression context, yet existing gene embeddings remain largely modality-specific and difficult to compare or reuse when many views are unavailable. We study a narrower but practically important question: whether pretrained embeddings from these distinct sources can be organized into a shared gene representation interface that remains usable under severe missing-modality conditions. To investigate this question, we introduce RepGene, a lightweight single-branch framework that combines modality adapters, a shared encoder, presence-aware fusion, and self-supervised cross-view objectives to map five biological views into one latent space. Our goal is not to claim a new multimodal learning principle or to establish superiority over all simpler fusion strategies, but to provide an initial technical instantiation for testing whether such a shared interface is feasible in a fixed-feature setting. Under a two-stage protocol in which RepGene is trained self-supervised on frozen upstream embeddings and evaluated by downstream linear probing, we find preliminary evidence that the learned representation is broadly competitive in the full-modality setting and remains informative when only partial modality subsets are observed at inference time. The strongest signal in our study is robustness under missing views: average performance changes are often limited when one modality is removed, and even single-view inference remains non-trivial in the evaluated benchmark regime. These results do not resolve unified biological representation learning, and they should be interpreted in light of incomplete simple-fusion baselines, limited architectural ablation, benchmark dependence, and possible upstream feature exposure. We therefore position RepGene as a feasibility study and a starting point for stronger comparisons, broader benchmarks, and leakage-aware validation.