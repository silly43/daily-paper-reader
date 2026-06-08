---
title: The hippocampus as a small-world cognitive map
title_zh: 海马体作为小世界认知地图
authors: "Kim, J. Z., Sethna, J. P., Cohen, I., Sun, W."
date: 2026-05-31
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.07.704615v2.full.pdf"
tags: ["query:world-models"]
score: 6.0
evidence: 海马体认知地图作为内部世界模型表示状态转换
tldr: 认知地图需同时保证局部精确表征和全局可搜索性，海马体如何实现这一设计问题尚不清楚。本研究使用几何感知自编码器分析小鼠海马CA1群体钙成像数据，发现其通过小世界网络结构实现平衡：群体层面螺旋动力学保留局部信息，细胞层面多野神经元创建远程捷径。离线时群体事件常跳转到远处状态，表明该结构优化了智能系统的搜索效率。
source: biorxiv
selection_source: fresh_fetch
motivation: 认知地图需兼顾局部保真度与全局可搜索性，现有研究对海马如何实现这一设计问题理解不足。
method: 采用几何感知自编码器建模纵向钙成像数据，分析小鼠学习记忆导航任务时海马CA1群体编码结构。
result: 发现海马群体编码具有小世界网络特性，通过螺旋动力学和多野细胞分别实现局部保留与远程捷径，离线活动频繁跳跃至远处状态。
conclusion: 揭示海马表征优化智能系统在精确内部模型上高效搜索的基本挑战，对神经科学与AI有启示。
---

## 摘要
当一只老鼠感知到鹰的影子时，它可能只有几秒钟的时间决定往哪里跑，然而最安全的藏身处往往既不可见也不在附近。为了生存，它必须足够快地搜索其认知地图，以在众多可能性中做出选择，并足够准确地避开沿途的死角和危险，同时随着路径、藏身处和威胁随时间变化，“安全”的定义也在改变。这一场景凸显了一个核心设计问题：认知地图必须保留精细的局部结构以实现可靠行动，同时保持全局可搜索性，以便在空间和时间上高效地找到遥远而有用的解决方案。海马体被认为支持此类地图，其群体活动表征世界状态及其转换——然而这些地图如何构建以解决这一设计问题尚不明确。在此，我们使用一种新颖的几何感知自编码器，对在学习记忆引导导航任务的小鼠海马CA1区数千个神经元的长时程钙成像数据建模，从而揭示认知地图的结构。我们发现，海马群体编码通过神经表征空间中的小世界网络结构实现了局部保真度和全局可搜索性的兼顾，该结构利用了两种互补机制。在群体层面，神经表征相对于过去经验的螺旋（旋转加漂移）动态构建新地图，保留空间和时间上邻近位置的局部信息，同时保持与早期表征的可区分性。在细胞层面，具有协调多野活动的神经元创建了遥远表征之间的稀疏长程捷径。在静止期间的同步群体事件中，解码的活动常跳跃到空间、时间和任务状态上的遥远位置，表明这些捷径在离线处理中被启用。这种功能组织对神经科学和人工智能都有启示，揭示了海马表征如何针对智能系统面临的基本挑战进行优化：通过精确的内心世界模型进行高效搜索。

## Abstract
When a mouse perceives a hawks shadow, it may have only seconds to decide where to run, yet the safest refuge is often neither visible nor nearby. To survive, it must search its cognitive map quickly enough to choose among many possibilities, and accurately enough to avoid dead ends and hazards along the way, all while what counts as "safe" changes as paths, refuges, and threats shift with time. This scenario highlights a core design problem: cognitive maps must preserve fine local structure for reliable action, yet remain globally searchable so that distant, useful solutions can be found efficiently in both space and time. The hippocampus is thought to support such maps, with population activity representing world states and their transitions--yet how these maps are structured to solve this design problem is not well understood. Here, we used a novel geometry-aware autoencoder to model the structure of the cognitive map from longitudinal calcium imaging from thousands of hippocampal CA1 neurons in mice learning a memory-guided navigation task. We discovered that the hippocampal population code achieves both local fidelity and global searchability through small-world network structure in the space of neural representations that leverages two complementary mechanisms. At the population level, helical (rotation-plus-drift) dynamics of neural representations relative to past experience build new maps that preserve local information about nearby positions in space and time while remaining distinguishable from earlier representations. At the cellular level, neurons with coordinated multi-field activity create sparse, long-range shortcuts between distant representations. During synchronous population events in immobility, decoded activity often jumps to distant states in space, time, and task conditions, suggesting these shortcuts are engaged during offline processing. This functional organization, with implications for both neuroscience and artificial intelligence, sheds light on how hippocampal representations may be optimized for a fundamental challenge faced by intelligent systems: efficiently searching through accurate internal models of the world.