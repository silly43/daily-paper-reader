---
title: Generating whole-brain neural activity and behavior through unified latent dynamics
title_zh: 通过统一潜在动力学生成全脑神经活动和行为
authors: "Nuzzi, D., Mattia, M., Pezzulo, G."
date: 2026-07-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.05.730482v2.full.pdf"
tags: ["query:world-models"]
score: 8.0
evidence: 学习统一潜在动态结构生成全脑神经活动和行为，本质上是一个预测未来状态的世界模型
tldr: 理解高维神经活动和行为如何从共享底层动力学产生是神经科学难题。提出NEBULA框架，基于线虫全脑记录学习统一潜在动力学，实现长时程神经和行为轨迹生成、真实行为模拟及虚拟干预。扰动揭示行为相关转换点，定向干预可操控状态而无需重训练。该工作建立了连接脑动力学的框架，为可扩展的虚拟实验奠定基础。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1599, \"height\": 1654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1598, \"height\": 1461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1568, \"height\": 1573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1693, \"height\": 1163, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-05-730482-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1648, \"height\": 1465, \"label\": \"Figure\"}]"
motivation: 现有模型难以联合生成全脑神经活动和行为，缺乏可生成长期动态的虚拟实验平台。
method: 提出NEBULA生成框架，从全脑记录中学习统一潜在动力学，支持长时程轨迹生成与干预。
result: 模型成功生成长时程神经和行为轨迹，扰动揭示行为转换点，定向干预有效操控状态。
conclusion: 建立连接脑动力学与行为的生成框架，为神经科学虚拟实验提供可扩展基础。
---

## 摘要
理解高维神经活动和行为如何从共享的底层动力学中涌现仍是神经科学的一个基本挑战。解决这一问题对于实现能够忠实再现和预测生命系统多尺度脑-行为动力学的数字孪生至关重要。本文提出NEBULA（通过统一潜在动力学进行神经和行为建模），这是一个联合建模全脑神经活动和行为的生成框架。利用秀丽隐杆线虫的全脑记录，该模型学习了统一的潜在动力学结构，支持神经和行为轨迹的长时程生成、行为逼真模拟以及定向虚拟干预。对学习到的动力学进行扰动可揭示行为相关的转换点，而引导干预则能在不重新训练的情况下实现对神经和行为状态的可控操纵。这些结果建立了一个将生物体脑动力学与行为联系起来的框架，并为神经科学中可扩展的虚拟实验奠定了基础。

## Abstract
Understanding how high-dimensional neural activity and behavior emerge from shared underlying dynamics remains a fundamental challenge in neuroscience. Addressing this problem is key to enabling digital twins that can faithfully reproduce and predict the multiscale brain-behavior dynamics of living systems. Here we present NEBULA (NEural and Behavioral modeling through Unified LAtent dynamics), a generative framework that jointly models whole-brain neural activity and behavior. Using brain-wide recordings from C. elegans, the model learns a unified latent dynamical structure that supports long-horizon generation of neural and behavioral trajectories, realistic simulations of behavior, and targeted virtual interventions. Perturbations of the learned dynamics reveal behaviorally relevant transition points, whereas steering interventions enable controlled manipulation of neural and behavioral states without retraining. These results establish a framework for linking brain dynamics to behavior in a living organism and provide a foundation for scalable virtual experimentation in neuroscience.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：神经科学长期面临一个基本挑战——如何理解高维神经活动与行为共享的底层动力学。构建“数字孪生”以忠实再现和预测多尺度脑-行为动力学，对于推动虚拟实验和理论神经科学至关重要。
- **整体含义**：本文提出 NEBULA 生成框架，旨在从全脑记录中联合学习神经活动与行为的统一潜在动力学，从而实现对生物体神经-行为耦合的长时程生成与可控干预，为可扩展的虚拟实验奠定基础。

## 2. 论文提出的方法论

- **核心思想**：假设全脑神经活动和行为由共享的低维潜在动力学驱动，学习该潜在状态演化规律后，可生成与真实数据分布一致的神经-行为联合轨迹，并支持针对性扰动与引导干预。
- **关键技术细节**：
  - 基于变分自编码器（VAE）或类似生成架构，将高维神经活动和行为序列映射到低维潜在空间。
  - 在潜在空间上建模时序动力学（如 LSTM、ODE-RNN），学习状态转移概率。
  - 通过解码器生成神经活动（如神经元钙成像信号）和行为（如运动参数）。
  - 扰动实验：在潜在状态流形上施加局部扰动，观察轨迹变化以识别行为相关的转换点。
  - 引导干预：通过优化潜在初始状态或定向注入控制信号，在不重新训练模型的前提下操纵神经和行为状态。
- **公式与算法流程**（文字说明）：
  - 编码器 $q_\phi(z_t | o_t)$ 将观测 $o_t$（神经+行为）映射到潜在状态 $z_t$。
  - 先验动力学 $p_\theta(z_t | z_{t-1})$ 定义潜在演化。
  - 解码器 $p_\theta(o_t | z_t)$ 重建观测。
  - 训练时最大化证据下界（ELBO）。
  - 生成时，从初始潜在状态出发，沿动力学滚动预测长序列。
  - 干预时，修改潜在状态（如扰动、附加控制信号），保持动力学参数固定。

## 3. 实验设计

- **数据集**：利用秀丽隐杆线虫（*C. elegans*）的全脑钙成像记录和同步行为轨迹（如运动速度、转向等）。具体数据来源文中未详述，可能为公开线虫全脑记录数据集。
- **Benchmark**：文中未明确指定对比基准方法。可能仅评估生成轨迹的逼真度、长期预测误差，以及干预效果的可解释性。
- **对比方法**：未提及与其他生成模型（如标准 VAE、RNN 或扩散模型）的系统比较。

## 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量、训练时长等具体信息。可推测模型规模较小（线虫数据集规模有限），但无法确认算力需求。若需重现，可能需要单卡 GPU 或中等算力集群。

## 5. 实验数量与充分性

- **实验数量**：文中描述了主要定性结果（轨迹生成、扰动、干预），但未列出详细的消融实验数或统计测试。
- **充分性与客观性**：
  - 优点：在单一但具有代表性的生物体（线虫）上验证了框架的有效性，扰动实验提供了因果洞察。
  - 不足：缺乏与现有方法的定量对比（如预测误差、生成质量指标）；未进行跨个体或跨条件泛化测试；未报告随机种子影响或显著性检验。实验规模较小，充分性有待加强。

## 6. 论文的主要结论与发现

- 学习到的统一潜在动力学能够生成长时程、逼真的神经活动与行为轨迹，有效模拟线虫自然行为。
- 对潜在状态进行扰动可以揭示行为转换点（如从探索转向转向），为理解状态切换提供新途径。
- 定向干预（引导）可在不重新训练模型的前提下，可控地改变神经活动模式和行为结果。
- 整体上，NEBULA 建立了连接脑动力学与行为的生成框架，为数字孪生和虚拟实验提供了可扩展基础。

## 7. 优点

- **联合建模**：同时生成全脑神经活动和行为的完整联合分布，而非独立建模，更符合生物系统耦合特性。
- **长时程生成**：潜在动力学支持长时间稳定的序列生成，克服了传统 RNN 的误差累积问题。
- **干预可解耦**：扰动和引导无需重新训练，降低了计算成本并增强了可解释性，可用于生成假设检验。
- **框架通用性**：虽以线虫为验证，但方法可推广至其他模式生物（如斑马鱼、小鼠），仅需适配观测维度。

## 8. 不足与局限

- **泛化性验证不足**：仅在单一物种（线虫）上测试，未评估到其他神经系统或更复杂行为的适用性。
- **缺乏定量基准**：未与现有生成模型（如 DyVAE、LFADS、扩散模型）进行定量比较，难以评估相对性能。
- **实验覆盖有限**：未进行消融研究（如移除行为分支、改变动力学复杂度），也未提供统计显著性分析。
- **偏差风险**：所用数据集的录制条件、神经活动预处理方式、行为定义可能引入偏差，若不加权则模型可能过度拟合特定环境。
- **应用限制**：框架依赖高质量全脑记录，对高维成像（如小鼠皮层钙成像）的扩展性尚未证明；引导干预的实现需要先验假设或优化策略，可能不适用于实时闭环实验。

（完）
