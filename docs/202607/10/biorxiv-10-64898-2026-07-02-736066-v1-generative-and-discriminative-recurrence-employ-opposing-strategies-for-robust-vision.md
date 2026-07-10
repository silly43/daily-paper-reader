---
title: Generative and discriminative recurrence employ opposing strategies for robust vision
title_zh: 生成式与判别式递归采用相反策略实现鲁棒视觉
authors: "Schmitt, L.-M., Koot, M., Heilbron, M., de Lange, F."
date: 2026-07-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.02.736066v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 比较生成与判别递归在鲁棒视觉中的作用，与自监督学习中的生成模型相关
tldr: 生物视觉利用循环连接提升鲁棒性，但具体计算策略未知。本研究向CNN赋予不同循环架构（横向/反馈）和训练目标（生成式/判别式），发现两种对立策略：生成式反馈通过降噪降低表示维度实现鲁棒（无需噪声训练），判别式横向/反馈循环则通过增加维度提升可区分性（需噪声训练）。这揭示了鲁棒视觉的不同计算机制，为神经科学提供可检验预测。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-736066-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1352, \"height\": 816, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-736066-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1295, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-736066-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1336, \"height\": 1446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-736066-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1303, \"height\": 732, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-736066-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1304, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-02-736066-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1324, \"height\": 788, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-02-736066-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1272, \"height\": 353, \"label\": \"Table\"}]"
motivation: 探究不同类型循环连接（生成式/判别式、横向/反馈）在视觉鲁棒性中的计算策略差异。
method: 向CNN注入不同循环架构（横向/反馈）和训练目标（生成式/判别式），对比其内部表征与抗噪行为。
result: 生成式反馈通过降噪降低表示维度实现抗噪（无需噪声训练），判别式循环（横向/反馈）通过增加维度提升可区分性（需噪声训练）。
conclusion: 这两种策略反映了根本不同的鲁棒视觉计算机制，为大脑中循环连接形式提供了可测试预测。
---

## 摘要
递归被认为能增强生物视觉的鲁棒性，但其实现机制尚不清楚。感知鲁棒性可通过两种方式实现：一是通过支持处理阶段内局部整合的侧向连接，二是通过利用来自高级阶段更广泛背景的反馈连接；同时，可通过优化任务相关分类的判别目标或学习重建视觉输入原因的生成目标来实现。但这些不同类型的递归是否采用不同的计算策略？由于这一问题难以在体内测试，我们赋予卷积神经网络不同的递归架构和训练目标，并评估不同噪声水平下内部表征和行为的影响。出现了两种不同的计算策略。生成式反馈遵循还原论策略，通过去噪使表征维度降低，在中等噪声水平下无需噪声训练即可实现鲁棒性。判别式侧向和反馈递归均遵循扩张主义策略，通过增加维度来提高判别能力而不去噪，但需要噪声训练才能实现鲁棒性。这些可分离的特征反映了鲁棒视觉的根本不同计算机制，并为大脑采用何种形式的递归提供了可测试的预测。

## Abstract
Recurrence is thought to enhance the robustness of biological vision, but how it achieves this feat is largely unknown. Perceptual robustness can be implemented through either lateral connections supporting local integration within a processing stage or feedback connections drawing on broader context from higher stages, and through either a discriminative objective optimising task-relevant classification or a generative objective learning to reconstruct the causes of visual input. But do these different types of recurrence engage distinct computational strategies? As this question is difficult to test in vivo, we endowed convolutional neural networks with varying recurrent architectures and training objectives, and evaluated the consequences for internal representations and behaviour across noise levels. Two distinct computational strategies emerged. Generative feedback followed a reductionist strategy, with representations becoming lower-dimensional through denoising, achieving robustness at moderate noise levels without noise training. Both discriminative lateral and feedback recurrence followed an expansionist strategy, increasing dimensionality to sharpen discriminability without denoising, but requiring noise training to achieve robustness. These dissociable signatures reflect fundamentally different computational mechanisms of robust vision and provide testable predictions for which form of recurrence the brain employs.