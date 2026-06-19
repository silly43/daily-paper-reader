---
title: "DOMINO: graph diffusion learning identifies spatial domain structures with enhanced accuracy and scalability"
title_zh: DOMINO：图扩散学习以增强的准确性和可扩展性识别空间域结构
authors: "Jia, P., Liu, N. W., Ran, Z., Maiolo, S., Zhang, T., Mohenska, M., Guo, X., Wang, C., Walters, E., Ricciardelli, C., Lokman, N. A., Morrow, R., Oehler, M. K., Polo, J. M., Liu, N., Li, F."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.15.694536v2.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 使用对比学习框架进行空间域检测
tldr: 空间转录组学分析面临数据规模大、现有方法仅关注局部而忽视全局的挑战。DOMINO框架通过图扩散卷积传播信息至远邻，结合对比学习优化全局结构，实现精准可扩展的空间域检测。在多个基准数据集及大规模卵巢癌数据上，DOMINO优于现有方法，发现保守的增殖/非增殖肿瘤状态及亚型特异性微环境。该工作为揭示组织空间功能区室提供了常规聚类无法获取的生物学新视角。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有空间域检测方法难以扩展到大数据，且仅关注局部结构，忽略全局组织视图。
method: DOMINO利用图扩散卷积传播远邻信息，并通过对比学习联合优化局部和全局图结构。
result: 在健康、恶性肿瘤及大规模卵巢癌数据集上优于现有方法，揭示增殖状态（EIF4A1/HSPA8上调）及亚型特异性细胞生态系统。
conclusion: DOMINO提供可扩展的生物可解释空间域检测，发现常规聚类无法恢复的肿瘤内在状态与微环境相互作用。
---

## 摘要
空间转录组学实现了原位分子分析，能够测量组织内细胞的转录输出。由于组织结构是保守的，可以识别具有特定转录模式的空间域，从而促进功能性组织区室的发现和理解。因此，已经开发了几种揭示和识别这些空间域的方法。然而，现有的大多数方法无法扩展到快速增长的数据量，并且仅关注局部结构而忽略了组织的全局视图。在这里，我们提出了DOMINO，一种用于空间域检测的扩散优化对比学习框架。DOMINO利用图扩散卷积将信息传播到直接邻居之外，并通过对比学习联合优化局部和重要的全局图结构。这一新颖框架产生了具有更清晰边界的生物学可解释域，并且可扩展到大型数据集，在健康和恶性基准数据集上优于最先进的方法。我们将DOMINO应用于新生成的内膜异位症相关卵巢癌空间转录组数据集，该数据集由于规模庞大而无法通过现有域检测方法处理。我们发现了在这些肿瘤中复现的保守增殖和非增殖肿瘤状态，并在外部透明细胞卵巢癌空间转录组数据集中独立验证。增殖域的特征是EIF4A1和HSPA8表达升高、细胞周期活性增加、肥大细胞丰度降低以及协调的基质重塑，包括改变的成纤维细胞状态和空间组织。同时，跨肿瘤的综合分析揭示了与子宫内膜样或透明细胞卵巢癌相关的亚型特异性多细胞生态系统，以及一个只能通过整合空间和转录信息才能解析的肿瘤排斥基质域。这些发现证明了DOMINO的良好扩展性，并且它揭示了跨越肿瘤内在状态、肿瘤微环境相互作用和亚型特异性组织架构的生物学意义空间程序，而这些是传统的基于表达聚类方法无法恢复的。

## Abstract
Spatial transcriptomics enables in situ molecular profiling, allowing to measure the cellular transcriptional output within the tissue. As the tissue architecture is conserved, spatial domains with specific transcriptional patterns can be identified, facilitating the discovery and understanding of functional tissue compartments. Thus, several methods to uncover and identify these spatial domains have been developed. However, most of these existing methods do not scale to rapidly increasing data sizes and focus only on local structure while missing the global view of the tissue. Here, we present DOMINO, a diffusion-optimised contrastive learning framework for spatial domain detection. DOMINO utilises graph diffusion convolution to propagate information beyond immediate neighbours and jointly optimises local and, importantly, global graph structure via contrastive learning. This novel framework yields biologically interpretable domains with clearer boundaries and scales to large datasets, outperforming state-of-the-art methods across healthy and malignant benchmark datasets. We apply DOMINO to a newly generated spatial transcriptomic dataset of endometriosis-associated ovarian cancers, which could not be processed by existing domain detection methods owing to its size. We uncovered conserved proliferative and non-proliferative tumour states that recurred across these tumours and were independently validated in an external clear cell ovarian cancer spatial transcriptomic dataset. Proliferative domains were characterised by elevated expression of EIF4A1 and HSPA8, increased cell cycle activity, reduced mast cell abundance, and coordinated stromal remodelling, including altered fibroblast states and spatial organisation. In parallel, integrative analysis across tumours revealed subtype-specific multicellular ecosystems associated with either endometrioid or clear cell ovarian carcinomas, together with a tumour-excluded stromal domain that could only be resolved through the integration of spatial and transcriptional information. These findings demonstrate how well DOMINO scales up and that it uncovers biologically meaningful spatial programs spanning tumour intrinsic states, tumour microenvironment interactions, and subtype-specific tissue architecture that are not recovered by conventional expression-based clustering approaches.