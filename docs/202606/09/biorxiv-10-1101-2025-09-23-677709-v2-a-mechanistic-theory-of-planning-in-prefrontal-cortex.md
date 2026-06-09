---
title: A mechanistic theory of planning in prefrontal cortex
title_zh: 前额叶皮层规划的机制性理论
authors: "Jensen, K. T., Doohan, P., Sable-Meyer, M., Reinert, S., Baram, A., Sahani, M., Akam, T., Behrens, T. E. J."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.1101/2025.09.23.677709v2.full.pdf"
tags: ["query:world-models"]
score: 7.0
evidence: 通过吸引子动力学预测未来状态
tldr: 规划对适应行为至关重要，但前额叶皮层的神经机制未知。本研究结合神经表征与吸引子动力学，通过将环境结构嵌入突触连接，构建时空吸引子网络实现规划。该网络在复杂任务中表现优异，且梯度下降训练的RNN精确复现其表征、动力学和连接。理论为理解前额叶皮层规划机制提供可检验的路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 前额叶皮层规划机制未知，现有序列记忆任务发现未来时间点表征，需扩展至更丰富的规划问题。
method: 结合神经表征与吸引子动力学，将环境结构嵌入突触连接，构建时空吸引子网络。
result: 时空吸引子在复杂规划任务中表现优异，RNN训练后精确复现其表征、动力学和连接。
conclusion: 理论可检验，为理解前额叶皮层如何结构自适应行为提供机制解释。
---

## 摘要
规划对于在不断变化的世界中的适应性行为至关重要，因为它使我们能够预测未来并相应调整行动。虽然前额叶皮层对这一过程至关重要，但规划如何在神经回路中实现仍不清楚。最近在更简单的序列记忆任务中发现了前额叶表征，其中不同的神经元群体代表不同的未来时间点。我们证明，将这些表征与神经吸引子动力学的普遍原理相结合，可以使回路解决更丰富的问题，包括规划。这是通过将环境结构直接嵌入突触连接中，以实现一个推断理想未来的吸引子网络来实现的。由此产生的时空吸引子在已知依赖于前额叶皮层的具有挑战性的规划任务中表现出色。通过梯度下降在这些任务上训练的递归神经网络学习到的解决方案，在表征、动力学和连接性上精确重现了时空吸引子。对不同环境结构下训练的网络的分析揭示了一种泛化机制，该机制可以快速重新配置用于规划的世界模型，而无需突触可塑性。时空吸引子是一个可检验的规划机制理论。如果成立，它将为详细理解前额叶皮层如何构建适应性行为提供一条路径。

## Abstract
Planning is critical for adaptive behaviour in a changing world, because it lets us anticipate the future and adjust our actions accordingly. While prefrontal cortex is crucial for this process, it remains unknown how planning is implemented in neural circuits. Prefrontal representations were recently discovered in simpler sequence memory tasks, where different populations of neurons represent different future time points. We demonstrate that combining such representations with the ubiquitous principle of neural attractor dynamics allows circuits to solve much richer problems including planning. This is achieved by embedding the environment structure directly in synaptic connections to implement an attractor network that infers desirable futures. The resulting  spacetime attractor excels at planning in challenging tasks known to depend on prefrontal cortex. Recurrent neural networks trained by gradient descent on such tasks learn a solution that precisely recapitulates the spacetime attractor - in representation, in dynamics, and in connectivity. Analyses of networks trained across different environment structures reveal a generalisation mechanism that rapidly reconfigures the world model used for planning, without the need for synaptic plasticity. The spacetime attractor is a testable mechanistic theory of planning. If true, it would provide a path towards detailed mechanistic understanding of how prefrontal cortex structures adaptive behaviour.