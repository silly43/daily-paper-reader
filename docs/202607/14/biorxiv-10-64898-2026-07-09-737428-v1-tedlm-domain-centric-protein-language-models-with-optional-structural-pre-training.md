---
title: "TEDlm: domain-centric protein language models with optional structural pre-training"
title_zh: TEDlm：以结构域为中心的蛋白质语言模型，支持可选的结构预训练
authors: "Wei, T., Kandathil, S. M., Buchan, D. W. A., Jones, D. T."
date: 2026-07-13
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.09.737428v1.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 以域为中心的蛋白质语言模型，使用掩码语言模型预训练
tldr: 传统蛋白语言模型在全长序列预训练中，多结构域与松散区域混合稀释了折叠特异性信号。本文提出TEDlm，仅基于结构域序列进行掩码语言模型预训练；其变体TEDlm3D引入Cα距离接触损失监督注意力图。在CATH S40远程同源检测任务上，650M参数TEDlm的AUROC达0.28，优于3B参数的ESM2（0.22），TEDlm3D进一步提升至0.50，接近结构搜索工具Foldseek（0.53）。零样本分子功能预测也显著提升，表明域中心预训练可构建紧凑且结构感知的蛋白语言模型。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737428-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1691, \"height\": 675, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737428-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737428-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 617, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737428-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 619, \"height\": 522, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-09-737428-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1709, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-09-737428-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1709, \"height\": 2158, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-09-737428-v1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1377, \"height\": 875, \"label\": \"Table\"}]"
motivation: 传统蛋白语言模型在全长序列预训练中，域信号被接头和松散区稀释，降低了远同源检测等任务的精度。
method: 从结构域百科全书提取域序列进行MLM预训练；TEDlm3D额外添加Cα距离引导的接触损失以监督注意力图。
result: 在CATH S40上，650M的TEDlm AUROC为0.28，优于3B的ESM2（0.22）；TEDlm3D达到0.50，接近Foldseek的0.53。
conclusion: 域中心预训练用更少参数获得结构信息，提升同源检测和功能预测，且域信号具内在性。
---

## 摘要
传统的蛋白质语言模型是在全长序列上预训练的，这些序列将多个结构域与连接子和无序区域交错排列，从而稀释了折叠特异性的信号。我们的方法在来自《结构域百科全书》的结构定义的结构域片段上预训练掩码语言模型。TEDlm仅使用标准MLM目标从结构域序列中学习，而其变体TEDlm3D添加了Cα距离引导的接触损失来监督注意力图。在CATH S40远程同源性检测（<40%同一性）中，以结构域为中心的预训练比模型规模影响更大：在最后一层，650M参数的TEDlm的AUROC1为0.28，而ESM2 3B为0.22；而TEDlm3D达到0.50，接近仅从序列推断的结构搜索工具Foldseek（0.53）。注意力图和分类雅可比探针显示，接触信号不仅编码在训练的输出头中，还编码在模型表示本身。TEDlm变体在零样本分子功能预测方面也显著优于ESM2，同时在各种生物物理属性任务上与ESM2相当，表明这些信号在很大程度上是结构域固有的。这些结果共同将结构域中心预训练定位为构建紧凑、结构信息丰富的蛋白质语言模型的途径。

## Abstract
Conventional protein language models are pretrained on full-length sequences that interleave multiple domains with linkers and disordered regions, diluting fold-specific signals. Our approach pretrains masked language models on structurally-defined domain segments from The Encyclopedia of Domains. TEDlm learns from domain sequences alone with a standard MLM objective, while its variant TEDlm3D adds a C distance-guided contact loss that supervises the attention maps. On CATH S40 remote-homology detection (<40% identity), the domain-centric pretraining has a bigger effect than model scale: at the final layer, a 650M-parameter TEDlm achieves an AUROC1 of 0.28 compared to 0.22 for ESM2 3B, whereas TEDlm3D reaches 0.50, approaching the structure-based search tool Foldseek (0.53) from sequence alone at inference. Attention-map and categorical Jacobian probes show that the contact signal is encoded in the model representations themselves, not only in a trained output head. TEDlm variants also substantially improve zero-shot Molecular Function prediction over ESM2, while matching it on various biophysical property tasks, indicating that signals are largely domain-intrinsic. Together, these results position domain-centric pretraining as a route to compact, structurally informed protein language models.