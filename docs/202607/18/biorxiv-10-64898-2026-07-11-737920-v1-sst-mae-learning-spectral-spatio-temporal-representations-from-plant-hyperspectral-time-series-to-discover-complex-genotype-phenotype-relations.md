---
title: "SST-MAE: Learning Spectral-Spatio-Temporal Representations from Plant Hyperspectral Time Series to Discover Complex Genotype-Phenotype Relations"
title_zh: SST-MAE：从植物高光谱时间序列学习光谱-时空表征以发现复杂基因型-表型关系
authors: "Okyere, F. G. G., Mehrem, S. L., Snoek, B. L., Van den Ackerveken, G., Abeln, S."
date: 2026-07-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.11.737920v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 自监督掩码自编码器用于植物高光谱时间序列
tldr: "植物育种中关联基因型与表型是关键，但现有方法依赖昂贵标注且忽略时间动态。本文提出SST-MAE，一种自监督框架，从高光谱时间序列学习基因型判别表征，无需表型标签。模型通过掩码重建捕获多生长轨迹，在194个生菜基因型8个时间点数据上，冻结编码器用于基因型分类，在花青素着色SNP上AUROC>0.89，叶锯齿上0.77。仅用30-50%标注数据即达近全性能，为高光谱表型高通量遗传筛选提供可扩展路径。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737920-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1245, \"height\": 1054, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737920-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1252, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737920-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1261, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737920-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1265, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-11-737920-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1268, \"height\": 471, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-11-737920-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1163, \"height\": 264, \"label\": \"Table\"}]"
motivation: 现有监督方法需要昂贵表型标注，且将高光谱影像视为静态快照，忽略植物发育时间动态，难以发现复杂基因型-表型关系。
method: 提出自监督框架SST-MAE，通过掩码自动编码器从高光谱时间序列学习表征，无需标签，重建多个生长轨迹。
result: "在194个生菜基因型8时间点数据上，冻结编码器在基因型分类任务中，花青素着色SNP的AUROC>0.89，叶锯齿0.77，且仅需30-50%标注数据即达近全性能。"
conclusion: SST-MAE有效利用时间动态与自监督学习，为从基于图像的表型进行高通量遗传筛选提供可扩展、标签高效的路径。
---

## 摘要
理解遗传变异与可观察性状之间的联系是作物育种的关键。高光谱成像捕捉生理和生化特征，但当前的监督方法需要昂贵的性状标注，并将每个观测视为静态快照，忽略了植物发育的时间动态。我们提出 SST-MAE，一种自监督框架，无需表型标签即可从植物高光谱发育轨迹中学习基因型判别性表征。该模型学习重建掩膜信息，捕捉多个生长轨迹。在 194 个田间生菜基因型（跨越八个时间点）上验证，冻结的编码器作为下游基因型分类的特征提取器。SST-MAE 优于原始光谱和线性基线，对花青素色素沉着 SNP 的 AUROC > 0.89，对叶锯齿的 AUROC 为 0.77。学习到的特征具有高度标签效率，仅使用 30-50% 的标记数据即可达到接近完整的性能，为从基于图像的表型进行高通量遗传筛选提供了可扩展的途径。关键词：基因型预测，高光谱成像，掩膜自编码器，植物表型分析，自监督学习

## Abstract
Understanding the link between genetic variation and observable traits is key to crop breeding. Hyperspectral imaging captures physiological and biochemical profiles, but current supervised methods require costly trait annotations and treat each observation as a static snapshot, ignoring the temporal dynamics of plant development. We introduce SST-MAE, a self-supervised framework that learns genotype-discriminative representations from plant hyperspectral developmental trajectories, without requiring phenotypic labels. The model learns to reconstruct masked information, capturing multiple growth trajectories. Validated on 194 field-grown lettuce genotypes across eight time points, the frozen encoder serves as a feature extractor for downstream genotype classification. SST-MAE outperforms raw spectral and linear baselines, achieving AUROC > 0.89 for anthocyanin pigmentation SNPs and 0.77 for leaf serration. The learned features are highly label-efficient, attaining near-full performance with only 30-50% of labeled data, offering a scalable pathway toward high-throughput genetic screening from image-based phenotypes. Keywords: Genotype prediction, Hyperspectral imaging, Masked autoencoder, Plant phenotyping, Self-supervised learning