---
title: "How a Predictive State Observer Can Self-Adapt Its Sensory Prediction-Error Correction Gain: Closed-Loop Evidence from a Muscle-Driven Reaching Task"
title_zh: 预测状态观测器如何自适应调整其感觉预测误差修正增益：来自肌肉驱动到达任务的闭环证据
authors: "Kobayashi, J."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729790v1.full.pdf"
tags: ["query:world-models"]
score: 8.0
evidence: 使用前向预测模型作为状态观测器，在肌肉驱动到达任务中预测未来状态
tldr: 在肌肉驱动到达任务中，前向模型预测状态观测器的感觉预测误差修正增益需根据延迟条件自适应调整。无延迟时中等增益(K=0.25-0.50)最优，18步延迟时高增益(K=1.0)最佳。仅用前向模型(K=0)因自回归漂移而显著变差(1.9-6.1 cm)。基于结果训练的可靠性自适应观测器在延迟条件下提升1.9-2.5 cm，特征条件beta适配器接近但未达到扫描固定K最优性能(差距1.4-1.8 cm)。研究揭示了延迟依赖的修正结构及当前自适应方法的局限。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究前向模型预测状态观测器如何从经验中自适应设置感觉预测误差修正增益，替代依赖真值标签的调参方式。
method: 在34肌肉MyoSuite手臂上，使用残差MLP前向模型和稳定端点探针控制器，闭环评估固定增益扫描与基于创新历史及结果的可靠性自适应观测器。
result: 无延迟时中等增益最优，18步延迟时高增益最优；自适应观测器在延迟条件下提升1.9-2.5 cm，但距扫描最优仍有1.4-1.8 cm差距。
conclusion: 延迟依赖的修正结构需自适应增益，但仅凭经验信号自适应仍受限于信息不足，性能不如固定增益扫描最优值。
---

## 摘要
我们探究基于前向模型的预测状态观测器在肌肉驱动到达过程中应如何设置其感觉预测误差修正增益，以及该增益是否可以从智能体可用的信号（创新历史与每回合到达结果）中自适应调整，而非依赖于扫描的先验标签。我们在一个34肌肉的MyoSuite手臂上评估一个残差MLP前向模型，执行IK可达的肩下任务，并与一个使用非负最小二乘肌肉路由和虚拟目标斜坡的稳定端点探针控制器闭环部署；该控制器是一个用于评估状态估计效果的稳定探针，而非生物运动规划器。扫描固定增益闭环先验揭示了延迟依赖的修正结构：无感觉延迟时，中等修正增益最佳（K=0.25-0.50）；而18步延迟时，重观测修正占优（K=1.0）。仅前向模型的K=0消融并非先验：它系统性地比最佳固定K差1.9-6.1厘米，并显示出由长时域自回归漂移引起的较大NNLS控制器残差；因此我们将K=0作为诊断指标报告。结果训练的信赖自适应观测器在延迟状态下比默认信赖改善1.9-2.5厘米，而在无延迟单元中保持中性，后者中先验已为中等。一个特征条件化的beta适配器将单元级创新统计映射到每场增益参数，在5/6的单元中几乎匹配每单元训练的诊断，但两者在18步延迟时仍比扫描固定K先验差1.4-1.8厘米。这些结果区分了延迟依赖的修正结构、K=0的仅前向模型失效模式，以及智能体可用自适应修正的剩余限制。

## Abstract
We ask how a forward-model-based predictive state observer should set its sensory prediction-error correction gain during muscle-driven reaching, and whether that gain can be adapted from agent-available signals - innovation history and per-episode reaching outcome - rather than from swept oracle labels. We evaluate a residual-MLP forward model in a 34-muscle MyoSuite arm on an IK-reachable below-shoulder task, deployed in closed loop with a stabilized endpoint probe controller that uses non-negative least-squares muscle routing and a virtual target ramp; the controller is a stabilized probe for evaluating state-estimation effects, not a biological motor planner. A swept fixed-gain closed-loop oracle reveals a delay-dependent correction structure: with no sensory delay, intermediate correction gains are best (K = 0.25-0.50), whereas with 18-step delay observation-heavy correction wins (K = 1.0). The forward-model-only K = 0 ablation is not the oracle: it is systematically worse than the best fixed K by 1.9-6.1 cm and shows large NNLS controller residuals caused by long-horizon autoregressive drift; we therefore report K = 0 as a diagnostic. Outcome-trained reliability-adaptive observers improve the delayed regime by 1.9-2.5 cm over default reliability while remaining neutral in no-delay cells, where the oracle is already intermediate. A feature-conditioned beta adapter that maps cell-level innovation statistics to per-field gain parameters nearly matches a per-cell trained diagnostic in 5/6 cells, but both remain 1.4-1.8 cm worse than the swept fixed-K oracle at 18-step delay. These results separate the delay-dependent correction structure, the forward-model-only failure mode of K = 0, and the remaining limits of agent-available adaptive correction.