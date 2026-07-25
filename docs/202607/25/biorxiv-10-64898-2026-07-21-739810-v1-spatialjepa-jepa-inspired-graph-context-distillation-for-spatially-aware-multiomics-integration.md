---
title: "SpatialJEPA: JEPA-inspired graph-context distillation for spatially aware multiomics integration"
title_zh: SpatialJEPA：基于JEPA启发的图上下文蒸馏用于空间感知的多组学整合
authors: "Mann-Krzisnik, D., Li, Y."
date: 2026-07-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.21.739810v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: JEPA是一种自监督表示学习框架
tldr: 空间多组学数据整合面临挑战，许多RNA-ATAC数据集缺乏空间坐标。SpatialJEPA采用JEPA启发的教师-学生框架，通过用自恒等图替代空间邻域图实现空间上下文掩码，使学生学习匹配教师嵌入。在小鼠脑多组学中，该方法实现了源-目标对齐，恢复了空间组织的转录组和染色质可及性程序，并与配体-受体通路结构一致。该工作为解离数据赋予空间感知能力提供了新范式。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-21-739810-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1649, \"height\": 835, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-21-739810-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1659, \"height\": 1621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-21-739810-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1640, \"height\": 1257, \"label\": \"Figure\"}]"
motivation: 现有空间多组学整合依赖坐标，但大量配对数据来自解离实验，缺乏空间信息，需将上下文从空间数据迁移到非空间数据。
method: 引入JEPA教师-学生框架，在训练中替换教师空间邻域图为自恒等图，强制学生从非空间视角匹配教师嵌入，实现空间上下文蒸馏。
result: 在小鼠脑多组学上，SpatialJEPA实现源-目标对齐，恢复空间转录组与染色质程序，且与配体-受体通路结构高度一致。
conclusion: 提出一种无需坐标即可赋予解离数据空间感知的整合方法，有效提升多组学表示的空间语义性。
---

## 摘要
整合空间基因组学模态的计算框架将基于细胞的表示学习扩展到分子层，但许多配对的RNA-ATAC数据集是解离的且缺乏空间坐标。我们提出SpatialJEPA，这是一个受JEPA启发的教师-学生框架，用于将空间上下文从空间多组学数据转移到非空间多组学数据。与补丁或特征掩蔽目标不同，SpatialJEPA通过在学生训练期间用仅自体的身份图替换教师的空间邻域图来掩蔽空间上下文，使得空间样本对学生表现为解离状态。学生从这种图上下文受限的视图中学习匹配教师嵌入，因此可以在推理时应用于解离的RNA-ATAC数据。在小鼠脑多组学中，得到的表示支持源-目标对齐，恢复空间组织的转录组和染色质可及性程序，并且与非空间参考相比，显示与配体-受体通路结构的一致性。已被CIBB 2026会议（https://cibb2026.teralab.ai/）接收。

## Abstract
Computational frameworks for integrating spatial genomics modalities extend cell-based representation learning across molecular layers, but many paired RNA-ATAC datasets are dissociated and lack spatial coordinates. We introduce SpatialJEPA, a JEPA-inspired teacher-student framework for transferring spatial context from spatial multiomics data to non-spatial multiome data. In contrast to patch- or feature-masking objectives, SpatialJEPA masks spatial context by replacing the teacher's spatial neighborhood graph with a self-only identity graph during student training, making the spatial sample appear dissociated to the student. The student learns to match teacher embeddings from this graph-context-restricted view and can therefore be applied to dissociated RNA-ATAC data at inference time. In mouse brain multiomics, the resulting representation supports source-target alignment, recovers spatially organized transcriptomic and chromatin-accessibility programs, and shows concordance with ligand-receptor pathway structure compared with non-spatial references. Accepted at the CIBB 2026 conference (https://cibb2026.teralab.ai/)