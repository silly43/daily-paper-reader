---
title: "Prediction of fMRI activity using vector autoregressive models: a comparison of sparse and low-rank approaches"
title_zh: 使用向量自回归模型预测fMRI活动：稀疏方法与低秩方法的比较
authors: "Tian, X., Gibberd, A., Roy, S., Nunes, M."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731556v1.full.pdf"
tags: ["query:world-models"]
score: 6.0
evidence: 使用VAR模型预测未来的fMRI活动
tldr: fMRI功能连接分析常用向量自回归（VAR）模型，但参数随脑区数平方增长导致高方差。提出低秩预平滑方法，先对观测数据做低秩近似再拟合VAR模型，与稀疏和无约束方法对比。结果显示低秩方法显著降低预测误差，并在合成实验中验证了参数估计的鲁棒性。该方法为高维fMRI数据提供了有效的个体水平参数估计，提升了预测性能。
source: biorxiv
selection_source: fresh_fetch
motivation: VAR模型参数过多导致估计方差高，需有效正则化方法。
method: 对观测数据做低秩预平滑后拟合VAR，比较稀疏和无约束方法。
result: 低秩方法显著降低预测误差，合成实验验证其参数估计准确性。
conclusion: 低秩预平滑实现稳健个体参数估计，优于稀疏和无约束方法。
---

## 摘要
向量自回归（VAR）模型在功能MRI研究中已有用于检查大脑功能连接的历史。这些模型允许估计大脑感兴趣区域之间的格兰杰因果关系。不幸的是，由于VAR模型的参数数量随区域数的平方增长，且通常远大于时间观测数，这些参数估计会表现出高方差。为解决这一挑战，我们引入了一种低秩预平滑方法，在拟合VAR模型之前对观测数据应用低秩近似。我们使用来自任务态和静息态条件的个体被试数据估计这些模型，并在群体水平调整超参数。直接将我们的低秩方法与稀疏和无约束估计方法进行了比较。对预测性能和模型结构的评估表明，我们的预平滑技术能够实现稳健的个体水平参数估计，并显著降低预测误差，这一发现通过已知真实参数的人工合成实验得到了进一步验证。

## Abstract
Vector autoregressive (VAR) models have a history of being used to examine functional connectivity in the brain, as captured by functional MRI studies. Such models allow for an estimation of Granger-causal relationships between regions of interest across the brain. Unfortunately, since the number of parameters in the VAR model scales as the square of the number of regions, and this is typically large compared to the number of temporal observations, these parameter estimates will exhibit high variance. To address this challenge, we introduce a low-rank pre-smoothing method that applies a low-rank approximation to the observations before fitting a VAR model. We estimate these models using individual subject data from both task-based and resting-state conditions, tuning hyperparameters at the population level. Our low-rank approach is directly compared against sparse and unconstrained estimation methods. Evaluations of predictive performance and model structure reveal that our pre-smoothing technique enables robust individual-level parameter estimation and significantly reduces prediction error, a finding further validated by synthetic experiments where the ground-truth parameters are known.