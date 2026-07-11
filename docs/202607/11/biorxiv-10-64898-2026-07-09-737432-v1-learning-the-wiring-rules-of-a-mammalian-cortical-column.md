---
title: Learning the wiring rules of a mammalian cortical column
title_zh: 学习哺乳动物皮层柱的布线规则
authors: "Richter, O., Schneidman, E."
date: 2026-07-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.09.737432v1.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 用于神经回路布线的自监督表征学习
tldr: 传统神经回路模型依赖测量特征与假设，存在局限。本文提出基于表征学习的框架，联合学习神经元的低维嵌入与布线规则，用于预测小鼠视觉皮层柱的突触连接。该模型仅用少量维度即准确预测单个突触、连接度和网络模体统计，优于依赖详细细胞类型分类的标准生成模型。嵌入具有可解释性，能重现皮层深度、细胞类型和树突形态，表明皮层连接遵循简约逻辑，提供了通用的连接组最小生成模型学习工具。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1362, \"height\": 1500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1825, \"height\": 1446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1819, \"height\": 883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1809, \"height\": 1164, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1838, \"height\": 1206, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1824, \"height\": 1631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1069, \"height\": 1194, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1192, \"height\": 688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1786, \"height\": 879, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-09-737432-v1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1821, \"height\": 1106, \"label\": \"Figure\"}]"
motivation: 现有生成模型受限于可测量特征和假设，需要新方法发现简洁的布线规则。
method: 提出表征学习框架，联合学习神经元在抽象特征空间的低维嵌入与预测突触连接的布线规则。
result: 嵌入模型准确预测突触、连接度和网络模体，优于依赖细胞类型分类的传统模型，且嵌入可解释。
conclusion: 皮层连接遵循简约逻辑，框架可作为学习连接组最小生成模型的通用工具。
---

## 摘要
神经回路架构的表征通常依赖于可测量的神经元特征，如形态、分子身份和空间位置。虽然利用这些特性的生成模型已被证明是准确的，但它们仍然受到现有测量数据以及我们对潜在特征假设的限制。在这里，我们提出了一种使用表征学习的替代方法，并将其用于模拟小鼠初级视觉皮层中的一个柱的回路。我们的框架在抽象特征空间中联合学习神经元的低维嵌入，以及预测突触连接的布线规则。这些基于嵌入的模型仅使用少量嵌入维度和布线规则，就能准确预测单个突触、连接度和网络模体统计量，优于依赖于详细细胞类型分类的标准生成模型。关键的是，学习到的表征被证明是可解释的，能够重现皮层深度、细胞类型和树突形态。由此产生的布线蓝图既简单又具有生物学意义，表明皮层连接遵循出奇简约的逻辑。该框架为学习连接组的最小生成模型提供了一个通用且可移植的工具。

## Abstract
Characterization of neural circuits' architecture typically relies on measurable neuronal features such as morphology, molecular identity, and spatial location. While generative models leveraging these properties have proven accurate, they remain constrained by available measurements and our assumptions regarding the prospective features. Here, we present an alternative approach using representational learning and use it to model the circuitry of a column of the mouse primary visual cortex. Our framework learns jointly low-dimensional embeddings of neurons in an abstract feature space alongside wiring rules that predict synaptic connectivity. These embedding-based models accurately predict individual synapses, connectivity degrees, and network motif statistics -- outperforming standard generative models that depend on detailed cell-type classifications -- using only a handful of embedding dimensions and wiring rules. Crucially, the learned representations prove interpretable, recapitulating cortical depth, cell type, and dendritic morphology. The resulting wiring blueprint is both simple and biologically meaningful, suggesting that cortical connectivity follows surprisingly parsimonious logic. This framework offers a general and exportable tool for learning minimal generative models of connectomes.