---
title: A unified theory of context-conditioned efficient and predictive coding
title_zh: 上下文条件的高效编码与预测编码的统一理论
authors: "Tavoni, G."
date: 2026-07-06
pdf: "https://www.biorxiv.org/content/10.1101/2025.02.24.639817v2.full.pdf"
tags: ["query:world-models"]
score: 7.0
evidence: 预测编码理论作为内部世界模型
tldr: 针对感官处理中多模态背景影响编码的问题，该研究提出了条件化高效编码与预测编码的统一理论。通过数学推导证明，高效编码解可映射为可解释的神经算法：背景信号提供预测，局部神经元编码残差，循环连接白化残差。该理论将高效编码与预测编码在数学上等价，统一解释了跨模态抑制、多模态感受野等实验现象，并作为经典单模态编码的推广。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-24-639817-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1198, \"height\": 1457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-24-639817-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1358, \"height\": 1303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-24-639817-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 1571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-24-639817-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1493, \"height\": 977, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-02-24-639817-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1657, \"height\": 1220, \"label\": \"Figure\"}]"
motivation: 感官处理受多模态背景影响，现有理论缺乏统一框架解释高效编码与预测编码如何协同。
method: 数学分析建立条件化高效编码与预测编码的等价性，推导出局部电路基于背景预测残差并白化残差的算法。
result: 理论统一解释了跨模态预测抑制、多模态感受野等现象，并恢复经典单模态编码为极限情况。
conclusion: 该框架为分布式神经系统中背景塑造局部表征提供了原理性基础，统一了编码目标、电路机制和实验观察。
---

## 摘要
感觉处理并非孤立发生：在特定感觉模态中，神经元所表征的内容受到来自其他感觉、动作和行为背景的信号塑造。这种上下文依赖性对神经编码理论提出了一个根本性问题：电路如何在利用大脑其他部分可用信息的同时，有效编码其局部输入？在此，我们发展了一个高效编码与预测编码的统一理论，展示了多模态上下文信息如何优化局部感觉电路内的表征。我们通过解析证明，高效编码解映射到一个可解释的神经算法：上下文信号为局部电路提供关于感觉输入的预期，局部神经元编码偏离这些预期的偏差，而循环相互作用则白化残差信号。这一结果建立了上下文条件高效编码与预测编码之间的数学等价性，揭示了预测计算可以从由上下文引导的高效输入压缩中涌现。由此产生的框架既区别于单模态内的经典冗余减少，也不同于分层贝叶斯推断。该理论解释并统一了多种实验现象，包括对预期输入的跨模态反应抑制以及跨感觉运动、视听、视觉-嗅觉和听觉-体感电路的多模态感受野，同时将经典单模态编码效应恢复为极限情况。通过将编码目标、电路机制和实验观察现象融入单一分析框架，这项工作为理解分布式神经系统如何利用上下文塑造局部表征提供了原则性基础。

## Abstract
Sensory processing does not occur in isolation: what neurons represent in a given sensory modality is shaped by signals from other senses, actions, and behavioral context. This context dependence raises a fundamental question for theories of neural coding: how can circuits efficiently encode their local input while using information available elsewhere in the brain? Here we develop a unified theory of efficient and predictive coding that shows how multimodal contextual information can optimize representations within a local sensory circuit. We demonstrate analytically that the efficient-coding solution maps onto an interpretable neural algorithm: contextual signals provide expectations about the sensory input to the local circuit, local neurons encode deviations from those expectations, and recurrent interactions whiten the residual signals. This result establishes a mathematical equivalence between context-conditioned efficient coding and predictive coding, revealing that predictive computations can emerge from efficient input compression guided by context. The resulting framework is distinct from both classical redundancy reduction within a single modality and hierarchical Bayesian inference. The theory explains and unifies diverse experimental phenomena, including cross-modal suppression of responses to predicted inputs and multimodal receptive fields across sensorimotor, audiovisual, visual-olfactory, and auditory-somatosensory circuits, while recovering classical unimodal coding effects as limiting cases. By linking coding objectives, circuit mechanisms, and experimentally observed phenomena within a single analytical framework, this work provides a principled foundation for understanding how distributed neural systems use context to shape local representations.