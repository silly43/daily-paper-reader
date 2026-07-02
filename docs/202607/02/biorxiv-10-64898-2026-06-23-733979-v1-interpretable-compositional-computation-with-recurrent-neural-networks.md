---
title: Interpretable compositional computation with recurrent neural networks
title_zh: 基于递归神经网络的可解释组合计算
authors: "Pezon, L., Van Meegen, A."
date: 2026-06-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.23.733979v1.full.pdf"
tags: ["query:world-models"]
score: 7.0
evidence: 循环神经网络中的共享潜在动力学作为世界模型组件
tldr: 灵活认知依赖可重用组件实现快速适应，但神经网络中共享组件的性质与任务依赖使用方式不明。我们基于低秩循环神经网络的低维潜空间，提出可解释组合计算理论，发现共享潜组件在神经活动中不可见却与任务依赖兼容。在连接统计和神经表征中识别出共享组件的标志，可预测网络对特定扰动响应，并找到任务依赖性进入计算的多个位置。该理论提供了组合计算通过共享组件的机制理解和可检验预测。
source: biorxiv
selection_source: fresh_fetch
motivation: 理解循环网络中共享动力学结构如何实现任务依赖的组合计算，并揭示其可解释机制。
method: 利用低秩循环网络的低维潜空间，分析共享潜组件的连接统计和神经表征标志。
result: 识别出共享组件在连接和表征中的标志，并发现任务依赖性进入计算的多个位置。
conclusion: 提供了组合计算的可解释机制和实验可检验预测，推动对灵活认知的神经基础理解。
---

## 摘要
灵活认知利用可重用的组件，使行为能够快速适应不同的情境或任务。对在多个任务上训练的人工神经网络的分析表明，这种组合性由跨任务共享和重用的动态结构支持。然而，这些共享组件的本质以及它们如何以任务依赖的方式被使用仍不清楚。在此，我们基于低秩递归神经网络低维潜在空间中的共享动态结构，发展了一种可解释组合计算的理论。我们展示了这些共享潜在组件在神经活动中并不是直接可见的，因此与任务依赖性活动兼容。我们在连接统计和神经表征中识别出共享潜在组件的标志。这些标志为网络对特定扰动实验的响应提供了可检验的预测。最后，我们识别了任务依赖性可以进入计算的的不同位点，从而让我们能够刻画组合任务的定性不同解决方案。总之，我们的理论通过低秩网络中的共享组件提供了组合计算的机制性理解和可检验的标志。

## Abstract
Flexible cognition utilizes reusable components to enable rapid adaptation of behavior to different contexts or tasks. Analysis of artificial neural networks trained on multiple tasks suggested that this compositionality is supported by dynamical structures which are shared and re-used across tasks. However, the nature of these shared components, and how they can be used in a task-dependent manner, remained unclear. Here, we develop a theory of interpretable compositional computation based on shared dynamical structures in the low-dimensional latent space of low-rank recurrent neural networks. We show that these shared latent components are not immediately visible in the neural activity, and are thus compatible with task-dependent activity. We identify hallmarks of shared latent components both in the connectivity statistics and the neural representations. These hallmarks yield testable predictions for the networks response to specific perturbation experiments. Finally, we identify distinct loci where task-dependence can enter the computation, allowing us to characterize qualitatively different solutions to compositional tasks. In summary, our theory provides a mechanistic understanding and testable hallmarks of compositional computation via shared components in low-rank networks.