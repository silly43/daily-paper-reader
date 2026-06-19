---
title: A genetic algorithm for self-supervised models of oscillatory neurodynamics
title_zh: 一种用于振荡神经动力学自监督模型的遗传算法
authors: "Nejat, H., Sherfey, J., Bastos, A. M."
date: 2026-05-29
pdf: "https://www.biorxiv.org/content/10.1101/2024.12.31.630823v6.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 用于拟合振荡神经动力学自监督模型的遗传算法
tldr: 预测处理理论认为大脑通过内部模型减少预测与感觉信号的差异，这与γ和α/β节律相关。现有模型要么抽象但缺乏振荡尖峰动力学，要么生物物理约束但需手动调参。本文提出GSDR进化优化框架，结合目标引导搜索、随机探索和遗传选择，能够自动调整尖峰网络参数以满足特定频谱目标，并重现预测路由相关的电路表型，且不限于特定神经模型。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有预测处理模型难以同时实现自监督学习和生物合理振荡动力学，需要大量手动调参。
method: 提出遗传随机增量规则（GSDR），一种进化优化框架，结合目标引导搜索、随机探索和遗传选择/淘汰，以及活动依赖性MCDP更新项。
result: GSDR能有效调整尖峰网络参数以达到β/γ频谱目标，并复现猴视觉皮层刺激诱发的γ动态，且适用于Izhikevich模型。
conclusion: GSDR提供了一个多目标探索振荡神经模型的方法学框架，减少了手动调参，可推广到不同神经模型。
---

## 摘要
预测处理理论认为，大脑通过减少内部生成的预测与外部感觉信号之间的差异来构建其环境的内部模型。先前的研究已将这些过程与伽马(40-100 Hz)和alpha/beta(10-30 Hz)频率范围的振荡活动联系起来。当前的计算方法面临权衡：抽象的预测处理模型可以实现自监督计算，但通常忽略振荡尖峰动力学，而生物物理约束的尖峰模型可以生成神经节律，但通常需要大量手动调优。在这里，我们引入了遗传随机Delta规则(GSDR)，这是一种进化优化框架，用于将非线性神经模型拟合到电生理目标。我们首先在简化的优化设置中评估GSDR，然后将其应用于涉及发放率、beta/gamma频谱比率以及来自视觉皮层的经验猕猴刺激诱发的伽马动力学的尖峰网络目标。我们表明GSDR可以搜索受约束的突触参数空间，减少对手动调优的依赖，并再现与预测路由相关的频谱和电路级表型。我们还使用Izhikevich模拟进行模型类鲁棒性分析，表明该方法不限于原始的Hodgkin-Huxley式实现。这些结果将GSDR定位为用于振荡神经模型多目标探索的方法论框架。

作者总结：在预测处理理论中，大脑被假设构建其环境的内部模型。经验和理论研究提示神经元振荡是这一过程的重要组成，异常振荡也与精神分裂症等疾病相关。为了研究这些机制，计算神经科学需要既能够表达具有生物学意义的尖峰和振荡动态，又能够在无需大量手动调优的情况下进行训练的模型。我们开发了遗传随机Delta规则(GSDR)，这是一种用于将非线性神经模型拟合到目标的自监督进化优化框架。GSDR结合了目标引导搜索、随机探索、遗传选择/去选择以及活动依赖的MCDP更新项。我们表明GSDR可以将尖峰网络调整到beta/gamma频谱目标和经验刺激诱发的伽马动态。结果并不证明预测路由或识别出唯一的生物回路；相反，它们表明GSDR可以识别候选电路配置，并可以推广到原始的Hodgkin-Huxley式模型之外的Izhikevich模拟。

## Abstract
Predictive processing theories propose that the brain builds internal models of its environment by reducing the discrepancy between internally generated predictions and external sensory signals. Prior work has linked these processes to oscillatory activity in gamma (40-100 Hz) and alpha/beta (10-30 Hz) frequency ranges. Current computational approaches face a trade-off: abstract predictive-processing models can implement self-supervised computations but often omit oscillatory spiking dynamics, whereas biophysically constrained spiking models can generate neural rhythms but often require extensive manual tuning. Here, we introduce the Genetic Stochastic Delta Rule (GSDR), an evolutionary optimization framework for fitting nonlinear neural models to electrophysiological objectives. We first evaluate GSDR in simplified optimization settings, then apply it to spiking-network objectives involving firing rates, beta/gamma spectral ratios, and empirical macaque stimulus-evoked gamma dynamics from visual cortex. We show that GSDR can search constrained synaptic parameter spaces, reduce reliance on manual tuning, and reproduce spectral and circuit-level phenotypes associated with predictive routing. We also used Izhikevich simulations as a model-class robustness analysis, showing that the approach is not limited to the original Hodgkin-Huxley-style implementation. These results position GSDR as a methodological framework for multi-objective exploration of oscillatory neural models.

Author summaryIn predictive processing theories, the brain is hypothesized to build internal models of its environment. Empirical and theoretical studies suggest that neuronal oscillations are important components of this process, and abnormal oscillations are also linked to disorders such as schizophrenia. To study such mechanisms, computational neuroscience needs models that can express biologically meaningful spiking and oscillatory dynamics while also being trainable without extensive manual tuning. We developed the Genetic Stochastic Delta Rule (GSDR), a self-supervised evolutionary optimization framework for fitting nonlinear neural models to objectives. GSDR combines objective-guided search, stochastic exploration, genetic selection/deselection, and an activity-dependent MCDP update term. We show that GSDR can tune spiking networks toward beta/gamma spectral objectives and empirical stimulus-evoked gamma dynamics. The results do not prove predictive routing or identify a unique biological circuit; rather, they show that GSDR can identify candidate circuit configurations and can generalize beyond the original Hodgkin-Huxley-style model to Izhikevich simulations.