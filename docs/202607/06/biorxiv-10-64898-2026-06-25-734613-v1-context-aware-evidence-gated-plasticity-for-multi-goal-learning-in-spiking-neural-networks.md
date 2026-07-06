---
title: Context-Aware Evidence-Gated Plasticity for Multi-Goal Learning in Spiking Neural Networks
title_zh: 面向脉冲神经网络多目标学习的上下文感知证据门控可塑性
authors: "Neymotin, S. A., Hazan, H., Unal, G., Earl, C., Anwar, H., Franaszczuk, P., Boothe, D."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734613v1.full.pdf"
tags: ["query:world-models"]
score: 6.0
evidence: 具有网格细胞样结构的脉冲神经网络作为导航内部世界模型
tldr: 生物启发的脉冲神经网络在进行多目标学习时，不同目标的突触更新会相互干扰。本文提出一种上下文感知证据门控可塑性(EGP)机制，为每个目标维护独立的候选修改存储和适应性奖励评估。在二维导航任务中，多目标STDP/RL产生严重干扰，而目标上下文EGP实现了更高的累积奖励、改善最弱目标性能并减少错误目标吸引。该方法为脉冲神经网络的持续多目标学习提供了生物可解释的干扰缓解方案。
source: biorxiv
selection_source: fresh_fetch
motivation: 多目标学习时不同目标的突触更新相互干扰，导致脉冲网络无法稳定学习多个导航目标。
method: 提出上下文感知EGP，为每个目标独立累积候选突触修改，仅当奖励证据支持时进行巩固。
result: 目标上下文EGP相比全局EGP和STDP/RL，在多目标导航中提高晚期奖励，减少错误目标吸引，提升弱目标性能。
conclusion: 上下文感知的证据巩固机制能有效减少多目标学习中的干扰，为脉冲网络的持续强化学习提供生物合理方案。
---

## 摘要
背景/引言
生物启发脉冲神经网络可以建模自适应行为，但学习多个目标很困难，因为针对不同目标的突触更新可能相互干扰。我们测试了多时间尺度可塑性和上下文特定信用分配是否能改善受内嗅皮层-海马回路启发的脉冲导航系统中的持续多目标学习。

方法
我们开发了一个闭环脉冲模型，包含网格样、位置样、目标相关、关联和运动输出群体。一个智能体在具有随机起始位置的二维环境中导航，并通过奖励调制脉冲时序依赖可塑性（STDP/RL）和一种新颖的证据门控可塑性（EGP）框架进行学习。EGP积累候选突触修改，使用奖励证据评估它们，并仅整合那些能改善性能的变化。目标-上下文变体为每个目标维护了独立的提议存储和奖励评估。

结果
STDP/RL学习并保留了一个单目标导航策略，但多目标训练产生了显著干扰，包括学习后对错误目标的吸引。在10个连接种子中，目标-上下文EGP比全局EGP实现了更高的后期奖励，改善了最弱目标的性能，并增加了获得正向奖励的目标比例。在一个更长的持续学习模拟中，所有目标的奖励都增加了，测试阶段的性能日益超过训练阶段性能，并且提议幅度在学习过程中增长。停留时间混淆分析表明，与多目标STDP/RL相比，目标-上下文EGP减少了对错误目标的吸引，并提高了目标选择性。

结论
这些结果表明，脉冲导航回路可以使用局部可塑性学习目标导向行为，但鲁棒的多目标学习受益于上下文特定的基于证据的巩固。目标-上下文EGP为脉冲神经网络中持续强化学习期间减少干扰提供了一种生物启发机制。

## Abstract
Background / IntroductionBiologically inspired spiking neural networks can model adaptive behavior, but learning multiple goals is difficult because synaptic updates for different targets can interfere. We tested whether multi-timescale plasticity and context-specific credit assignment could improve continual multi-goal learning in a spiking navigation system inspired by entorhinal-hippocampal circuitry.

MethodsWe developed a closed-loop spiking model containing grid-like, place-like, target-related, association, and motor-output populations. An agent navigated in a two-dimensional environment with randomized starting locations and learned through reward-modulated spike-timing dependent plasticity (STDP/RL) and a novel evidence-gated plasticity (EGP) framework. EGP accumulates candidate synaptic modifications, evaluates them using reward evidence, and consolidates only changes that improve performance. A target-context variant maintained separate proposal stores and reward evaluation for each target.

ResultsSTDP/RL learned and retained a single-target navigation policy, but multi-target training produced substantial interference, including attraction to incorrect targets after learning. Across 10 connectivity seeds, target-context EGP achieved higher late-stage reward than global EGP, improved weakest-target performance, and increased the fraction of targets achieving positive reward. In a longer continual-learning simulation, reward increased for all targets, TEST-phase performance increasingly exceeded TRAIN-phase performance, and proposal magnitudes grew over learning. Dwell-time confusion analyses showed that target-context EGP reduced wrong-target attraction and improved target selectivity relative to multi-target STDP/RL.

ConclusionsThese results demonstrate that spiking navigation circuits can learn goal-directed behavior using local plasticity, but robust multi-goal learning benefits from context-specific evidence-based consolidation. Target-context EGP provides a biologically motivated mechanism for reducing interference during continual reinforcement learning in spiking neural networks.