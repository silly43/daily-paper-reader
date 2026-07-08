---
title: Uncovering internal states with a robust shared-state multi-neuron GLM-HMM framework
title_zh: 利用鲁棒的共享状态多神经元GLM-HMM框架揭示内部状态
authors: "Lawrence, A., Yezerets, E., Janak, P. H., Charles, A."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.27.734988v1.full.pdf"
tags: ["query:world-models"]
score: 6.0
evidence: 从神经群体活动中发现潜在内部状态，类似于学习智能体的内部世界模型
tldr: 神经系统中存在多个发放状态反映内部状态，而传统GLM-HMM多用于行为数据，直接拟合神经数据因稀疏性、共线性和低试验数而困难。本文构建了稳健的多神经元GLM-HMM框架，通过引入神经元自适应惩罚和信赖域算法改进EM过程，并在低试验数数据集上采用留一交叉验证。在灵长类和啮齿类电生理数据上实现了稳定收敛，揭示了与行为相关的内部状态，为理解神经-行为关系提供了有力工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有GLM-HMM难以直接拟合多神经元数据，因稀疏发放、协变量共线性和低试验数导致参数估计不稳定。
method: 通过EM算法结合神经元自适应惩罚解决共线性，使用信赖域算法保证Hessian病态下的收敛，并采用留一交叉验证评估模型。
result: 在三个灵长类和啮齿类决策任务数据集上实现稳定收敛，成功识别出具有行为相关性的神经发放状态。
conclusion: 该框架能稳健地从群体神经活动中提取内部状态，提升了对神经-行为关系的理解。
---

## 摘要
神经系统表现出多种放电状态，这些状态反映生物体的内部状态，并调节外部环境刺激与行为之间的关系。一些研究通过使用非泊松行为观测的广义线性模型（GLM）补充传统隐马尔可夫模型（HMM）来推断这些潜在状态。然而，理解大脑内部状态与行为之间的关系也需要对神经活动进行建模。尽管如此，由于神经元数据集的高度稀疏性、共线性和低试验次数，拟合多神经元GLM-HMM并非易事。因此，我们构建了一个鲁棒的多神经元GLM-HMM框架，该框架从群体活动中揭示潜在状态，同时融入时间戳任务变量和脉冲历史的影响。为了获得可靠的模型参数，我们采用了一种改进的期望最大化程序。具体来说，我们表明在最大化步骤中引入神经元自适应惩罚可以克服时间戳事件和稀疏脉冲典型存在的协变量共线性问题，从而得到泊松GLM系数的稳定估计。此外，我们引入信赖域算法以确保在病态海森矩阵（可能导致不稳定的牛顿-拉弗森更新）存在时M步稳定收敛。我们进一步展示了留一法交叉验证分析在低试验次数且不破坏时间结构的数据集上评估模型性能的实用性。我们在来自灵长类和啮齿类动物执行决策任务时的三个电生理数据集上评估了我们的框架，展示了稳定的模型收敛，并讨论了推断状态的行为相关性。

作者总结：神经系统随时间演化：不仅单个神经元在网络上相互影响，而且当动物进入不同行为（如专注与脱离）或状态（如饥饿或疲劳）时，网络本身及其连接也会发生变化。因此，分析指导行为的神经活动必须考虑大脑的时变特性。最近的建模工作将流行的广义线性模型（一种能将任务和行为与记录的神经动作电位联系起来的模型）扩展到包含隐马尔可夫模型。这一扩展使得生成的GLM-HMM能够表现出几种不同的关系（不同的GLM），这些关系随时间切换以适应动物改变的模式。虽然GLM-HMM已广泛用于行为数据（例如决策范式中的任务选择），但由于样本量较小、活动稀疏和参数空间较大，神经数据的分析要困难得多。我们的工作提出了一种新的拟合方法和最佳实践，以稳健地将GLM-HMM拟合到神经数据。通过多次应用于各种神经数据集，我们证明稳健拟合GLM-HMM能够识别神经活动的重要特征，从而更好地理解其与行为的关系。

## Abstract
Neural systems exhibit multiple firing states that reflect an organisms internal state and modulate the relationship between external environmental stimuli and behavior. Several studies have inferred these latent states by supplementing the traditional hidden Markov Model (HMM) with generalized linear models (GLMs) with non-Poisson behavioral observations. However, understanding the relationship between internal brain states and behavior also requires modeling the neural activity. Nonetheless, fitting multi-neuron GLM-HMMs is non-trivial due to high sparsity, collinearity, and low trial counts in neuronal datasets. Therefore, we built a robust multi-neuron GLM-HMM framework that uncovers latent states from population activity while incorporating the influence of time-stamped task variables and spike histories. To obtain reliable model parameters, we employ a modified expectation-maximization procedure. Specifically, we show that incorporating neuron-adaptive penalization in the maximization step overcomes the covariate co-linearity issues typical of time-stamped events and sparse spiking, yielding stable estimates of Poisson GLM coefficients. Furthermore, we incorporate a trust-region algorithm to ensure stable M-step convergence in the presence of ill-conditioned Hessians that can lead to unstable Newton-Raphson updates. We further demonstrate the utility of leave-one-out cross-validation analysis for evaluating model performance on datasets with low trial counts and without breaking their temporal structure. We evaluate our framework on three electrophysiological datasets from primates and rodents as they perform a decision-making task, demonstrate stable model convergence, and discuss the behavioral relevance of the inferred states.

Author SummaryNeural systems evolve over time: not only do the individual neurons influence each other across the network, but the network and interconnections themselves change as an animal enters different behaviors (e.g., attentive vs. disengaged) or states (e.g., hungry or tired). Analyzing the neural activity that guides behavior thus must incorporate the time-varying nature of the brain. Recent modeling work has extended the popular Generalized Linear Model, a model that can connect task and behavior to recorded neural action potentials, to incorporate a latent Hidden Markov Model. This extension allows the resulting GLM-HMM to exhibit several different relationships (different GLMs) that are switched between over time to account for the animals changing patterns. While GLM-HMMs have been applied extensively on behavioral data (e.g., task choice in a decision making paradigm), neural data is much more difficult due to the smaller sample sizes, sparser activity, and larger parameter space. Our work presents a new fitting approach and best practices to robustly fit GLM-HMMs to neural data. We demonstrate through numerous applications to a variety of neural datasets that by robustly fitting GLM-HMMs to data, we can identify important features of neural activity that let us better understand its relationship to behavior.