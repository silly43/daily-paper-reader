---
title: Frozen Protein Foundation-Model Embeddings Improve Antibody-Antigen ΔΔG Ranking
title_zh: 冻结蛋白质基础模型嵌入改进抗体-抗原ΔΔG排序
authors: "Wang, R., Jin, K., Pan, L."
date: 2026-07-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.13.738250v1.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 展示了从自回归蛋白质基础模型提取冻结自监督表示用于排名任务
tldr: "抗体-抗原结合亲和力排序对抗体工程至关重要。本文比较从头训练的序列模型与基于冻结蛋白质基础模型AINN-P1嵌入的轻量下游头，在五折交叉验证下评估。线性探针已超越从头基线，优化轻量头将Spearman秩相关从0.42提升至0.53（相对提升28%），训练仅需数秒。结果表明冻结嵌入是数据高效的默认选择，并为任务自适应微调设定保守下界。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738250-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1621, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738250-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1206, \"height\": 675, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-13-738250-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1711, \"height\": 91, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-13-738250-v1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1707, \"height\": 280, \"label\": \"Table\"}]"
motivation: 探究冻结蛋白质基础模型嵌入能否高效提升抗体-抗原ΔΔG排序性能，避免从头训练的高成本。
method: 将亲和力成熟作为排序问题，比较从头训练的序列模型与基于冻结AINN-P1嵌入的线性探针及轻量头，采用五折交叉验证。
result: "冻结嵌入线性探针超越从头基线；优化轻量头将Spearman相关系数从0.42提升至0.53，相对提升28%。"
conclusion: 冻结基础模型嵌入是数据高效的默认选择，任务自适应微调预期会超越该下界。
---

## 摘要
我们研究了从AINN-P1（一个在数千万条天然蛋白质序列上自回归训练的蛋白质基础模型）中提取的表示是否可迁移到按结合亲和力对抗体-抗原对排序的任务。将亲和力成熟视为一个学习排序问题，依据结合自由能变化（ΔΔG），我们比较了一个从头开始端到端训练的任务特异性序列模型与基于冻结的AINN-P1嵌入构建的轻量级下游头，所有方法均在相同的五折交叉验证协议下评估。在冻结嵌入上的正则化线性探针已经超越了从零开始的基线，而优化的轻量级头将平均Spearman秩相关系数从0.42提高到0.53——相对提升约28%——同时训练时间只需数秒，且无需对基础模型进行任何微调。由于仅线性探针就超过了完全训练的端到端基线，因此增益归因于表示质量而非下游模型容量的增加。这些结果表明，冻结的基础模型嵌入是抗体工程中亲和力排序的一个强大且数据高效的默认选择，并为任务自适应微调预期将超越的结果建立了一个保守的下限。

## Abstract
We investigate whether representations from AINN-P1--a protein foundation model trained autoregressively on tens of millions of natural protein sequences--transfer to the task of ranking antibody-antigen pairs by binding affinity. Casting affinity maturation as a learning-to-rank problem over the change in binding free energy ({Delta}{Delta}G), we compare a task-specific sequence model trained end-to-end from scratch against lightweight downstream heads built on top of frozen AINN-P1 embeddings, all evaluated under an identical five-fold cross-validation protocol. A regularized linear probe on the frozen embeddings already surpasses the from-scratch baseline, and an optimized lightweight head raises the mean Spearman rank correlation from 0.42 to 0.53--a relative improvement of approximately 28%-- while training in seconds and without any fine-tuning of the foundation model. Because a linear probe alone exceeds the fully trained end-to-end baseline, the gain is attributable to representation quality rather than to added downstream-model capacity. These results position frozen foundation-model embeddings as a strong, data-efficient default for affinity ranking in antibody engineering and establish a conservative lower bound that task-adaptive fine-tuning is expected to exceed.