---
title: "DeltaQ: Value-Guided Hebbian Learning in Spiking Neuronal Networks for Multi-Goal Navigation"
title_zh: DeltaQ：脉冲神经网络中基于价值指导的赫布学习用于多目标导航
authors: "Earl, C., Unal, G., Hazan, H., Neymotin, S. A."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731882v1.full.pdf"
tags: ["query:world-models"]
score: 7.0
evidence: 具有网格细胞空间表示的脉冲神经网络用于多目标导航，内部模型
tldr: 动物在稀疏或延迟奖励环境中导航需要内部空间表示和记忆。本文提出DeltaQ模型，一种基于脉冲神经网络的生物启发式模型，结合网格细胞空间编码、ΔQ值引导的赫布可塑性和上下文调制，在两种迷宫任务中实现了高效的多目标导航。关键结果为模型能够生成不同的空间表示、学习稀疏奖励下的导航策略，并通过上下文调制在同一环境中支持多种导航目标。贡献在于桥接了神经回路机制与功能性强化学习，展示了生物启发的可塑性规则如何实现灵活导航。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有计算模型多聚焦于复现神经动力学，而非演示如何利用空间表示学习导航任务，缺乏从机制到功能的桥梁。
method: 构建脉冲神经网络，包含网格细胞、关联细胞和上下文细胞，采用ΔQ值调制的赫布可塑性指导突触权重更新。
result: 在两种迷宫环境中，模型成功学习到稀疏奖励下的高效导航策略，并基于上下文调制实现同一环境中的多目标导航。
conclusion: 生物启发的空间表示、价值引导的可塑性及上下文调制能协同支持灵活导航，为神经回路与强化学习之间提供联系。
---

## 摘要
动物经常需要在关于目标进展的反馈稀疏或延迟的环境中导航，这需要内部空间表征和先前经验的记忆。海马-内嗅系统被认为通过指导目标导向行为的分布式空间表征支持这种能力。然而，这些回路的许多计算模型主要侧重于再现神经动力学，而不是展示这种表征如何支持导航任务的学习。我们提出了一种受生物学启发的脉冲神经网络（SNN）模型，该模型结合了网格细胞衍生的空间表征、DeltaQ调制的赫布可塑性以及上下文依赖的调制，以支持稀疏奖励条件下的导航。网格细胞群体生成分布式空间编码，这些编码由关联细胞群体转化为更具空间选择性的内部表征。学习由从目标条件Q表计算的Q值变化（DeltaQ）驱动，允许局部突触可塑性整合关于长期导航结果的信息。对于包含多个导航目标的环境，上下文细胞群体提供任务依赖的调制，使得共享网络架构能够支持不同的导航策略。在两个互补的迷宫环境中，该模型展示了三个核心能力：生成不同的空间表征、在稀疏和延迟奖励下学习高效导航策略、以及在同一环境中支持多个导航目标。结果进一步表明，上下文调制在基本共享的群体表征中引入了微妙的、任务依赖的变化，使得相同的空间位置能够支持不同的导航行为。这些发现表明，受生物学启发的空间表征、价值指导的可塑性和上下文调制能够共同支持脉冲神经网络中的灵活导航，为机械神经回路模型与功能性强化学习之间架起桥梁。

## Abstract
Animals must often navigate environments where feedback about progress toward a goal is sparse or delayed, requiring internal representations of space and memory of prior experience. The hippocampal-entorhinal system is believed to support this capability through distributed spatial representations that guide goal-directed behavior. However, many computational models of these circuits focus primarily on reproducing neural dynamics rather than demonstrating how such representations support learning on navigation tasks. We present a biologically inspired spiking neuronal network (SNN) model that combines grid-cell-derived spatial representations, {Delta}Q-modulated Hebbian plasticity, and context-dependent modulation to support navigation under sparse reward conditions. Grid Cell populations generate distributed spatial codes that are transformed by an Association Cell population into more spatially selective internal representations. Learning is driven by changes in Q-values ({Delta}Q) computed from a goal-conditioned Q-table, allowing local synaptic plasticity to incorporate information about long-term navigation outcomes. For environments containing multiple navigation objectives, a Context Cell population provides task-dependent modulation that enables a shared network architecture to support distinct navigation policies. Across two complementary maze environments, the model demonstrates three core capabilities: generation of distinct spatial representations, learning of efficient navigation policies under sparse and delayed reward, and support for multiple navigation objectives within a shared environment. The results further show that contextual modulation introduces subtle task-dependent variations into a largely shared population representation, allowing identical spatial locations to support different navigation behaviors. These findings demonstrate that biologically inspired spatial representations, value-guided plasticity, and contextual modulation can jointly support flexible navigation in spiking neuronal networks, providing a bridge between mechanistic neural circuit models and functional reinforcement learning.