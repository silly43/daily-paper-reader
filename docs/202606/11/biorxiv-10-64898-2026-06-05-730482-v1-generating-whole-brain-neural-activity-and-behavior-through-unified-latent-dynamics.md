---
title: Generating whole-brain neural activity and behavior through unified latent dynamics
title_zh: 通过统一潜在动力学生成全脑神经活动和行为
authors: "Nuzzi, D., Mattia, M., Pezzulo, G."
date: 2026-06-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.05.730482v1.full.pdf"
tags: ["query:world-models"]
score: 8.0
evidence: 提出NEBULA，一种统一潜在动态生成框架，用于全脑神经活动和行为
tldr: 神经科学与行为的关联理解仍是挑战。研究提出NEBULA生成框架，利用线虫全脑记录学习统一潜在动力学，实现长时间生成神经与行为轨迹及逼真模拟。模型扰动揭示行为转换点，操纵干预可控神经行为状态，为数字孪生和虚拟实验奠基。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有模型难以联合建模全脑高维神经活动与行为的共享动力学。
method: 提出NEBULA框架，基于线虫全脑记录学习统一潜变量动力学，支持长时程生成与干预。
result: 模型成功生成逼真神经行为轨迹，扰动发现行为相关转换点，干预可控制状态。
conclusion: 建立了连接脑动力学与行为的统一框架，推动神经科学虚拟实验。
---

## 摘要
理解高维神经活动和行为如何从共享的底层动力学中涌现仍然是神经科学中的一个基本挑战。解决这一问题对于实现能够忠实地再现和预测生命系统多尺度脑-行为动力学的数字孪生至关重要。在此，我们提出NEBULA（通过统一潜在动力学进行神经和行为建模），这是一个联合建模全脑神经活动和行为的生成框架。利用秀丽隐杆线虫的全脑记录，该模型学习了一个统一的潜在动力学结构，支持神经和行为轨迹的长时程生成、行为的逼真模拟以及有针对性的虚拟干预。对所学动力学的扰动揭示了行为相关的转变点，而引导性干预使得无需重新训练即可实现神经和行为状态的可控操纵。这些结果为将大脑动力学与活体生物的行为联系起来建立了一个框架，并为神经科学中的可扩展虚拟实验提供了基础。

## Abstract
Understanding how high-dimensional neural activity and behavior emerge from shared underlying dynamics remains a fundamental challenge in neuroscience. Addressing this problem is key to enabling digital twins that can faithfully reproduce and predict the multiscale brain-behavior dynamics of living systems. Here we present NEBULA (NEural and Behavioral modeling through Unified LAtent dynamics), a generative framework that jointly models whole-brain neural activity and behavior. Using brain-wide recordings from C. elegans, the model learns a unified latent dynamical structure that supports long-horizon generation of neural and behavioral trajectories, realistic simulations of behavior, and targeted virtual interventions. Perturbations of the learned dynamics reveal behaviorally relevant transition points, whereas steering interventions enable controlled manipulation of neural and behavioral states without retraining. These results establish a framework for linking brain dynamics to behavior in a living organism and provide a foundation for scalable virtual experimentation in neuroscience.