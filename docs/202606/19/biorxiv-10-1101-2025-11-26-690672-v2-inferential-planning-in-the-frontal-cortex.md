---
title: Inferential planning in the frontal cortex
title_zh: 额叶皮层的推理规划
authors: "Donnarumma, F., Parr, T., Friston, K., Whittington, J., Pezzulo, G."
date: 2026-06-12
pdf: "https://www.biorxiv.org/content/10.1101/2025.11.26.690672v2.full.pdf"
tags: ["query:world-models"]
score: 8.0
evidence: 使用分层生成模型进行推理规划，预测未来动作
tldr: 大脑如何规划未来动作序列是系统神经科学的核心问题。近期额叶皮层研究发现序列多个元素同时表征于可分离神经子空间，挑战串行模型。本文通过层次生成模型实现推理规划，成功复现灵长类额叶皮层中多计划元素同时激活、正交记忆子空间及其跨任务重用等关键现象。该框架统一了规划、工作记忆与运动准备的分散发现，并生成关于主动推理动力学、感觉子空间作用及不确定性影响的新预测。
source: biorxiv
selection_source: fresh_fetch
motivation: 解释额叶皮层中序列规划的多元素同时表征现象，挑战经典串行模型。
method: 构建层次生成模型，通过概率推理从感知证据和目标推断序列动作。
result: 复现灵长类额叶皮层中计划元素同时激活、正交子空间及其在正反向任务中的重用。
conclusion: 推理规划框架统一规划、工作记忆与运动准备，并提出可测试预测。
---

## 摘要
大脑如何规划并维持未来动作的序列仍是系统神经科学的核心问题。最近对额叶皮层的研究揭示，序列的多个元素可在可分离的神经子空间中同时表征，这对经典的序列规划序列模型提出了挑战。在此，我们表明这些表征在推理规划中自然出现，其中序列动作是从感觉证据和目标中推理得出的。通过使用层次生成模型，我们重现了在灵长类额叶皮层中观察到的关键神经现象，包括多个规划元素的同时激活、(几乎)正交记忆子空间的产生，以及它们在正向和反向序列任务中的复用。我们的方法提供了一种机制性解释，说明对控制状态的概率推理如何产生分布的、动态的规划神经表征。该框架不仅统一了先前在规划、工作记忆和运动准备方面分散的发现，还产生了关于主动推理动态、感觉子空间作用以及不确定性对序列处理影响的新颖、可检验的预测。

## Abstract
How the brain plans and maintains sequences of future actions remains a central question in systems neuroscience. Recent studies in the frontal cortex have revealed that multiple elements of a sequence are represented simultaneously in separable neural subspaces, challenging classical serial models of sequential planning. Here, we show that these representations emerge naturally under inferential planning in which sequential actions are inferred from sensory evidence and goals. Using a hierarchical generative model, we reproduce key neural phenomena observed in primate frontal cortex, including the simultaneous activation of multiple plan elements, the emergence of (almost) orthogonal  memory subspaces, and their reuse across forward and backward sequence tasks. Our approach provides a mechanistic account of how probabilistic inference over control states gives rise to distributed and dynamic neural representations of plans. This framework not only unifies previously disparate findings on planning, working memory, and motor preparation, but also generates novel, testable predictions about the dynamics of active inference, the role of sensory subspaces, and the impact of uncertainty on sequence processing.