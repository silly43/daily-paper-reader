---
title: Small circuit principles for learning in large worlds
title_zh: 大世界学习的小电路原理
authors: "Raman, D. V., Dunne, C. R., Davyson, K., O'Leary, T."
date: 2026-07-06
pdf: "https://www.biorxiv.org/content/10.1101/2025.11.13.688216v2.full.pdf"
tags: ["query:world-models"]
score: 8.0
evidence: 受果蝇启发，提出Hetlearn框架用于在大型不确定世界中学习世界模型
tldr: 动物学习面临未知不确定性，传统贝叶斯方法在有限数据和认知资源下不切实际。受果蝇神经回路启发提出Hetlearn框架，牺牲渐近最优性以增强对环境突变的鲁棒性。该方法在数据有限时提供比标准贝叶斯更准确的状态估计，解释了果蝇蘑菇体生理结构并预测了跨物种的学习行为如二级条件作用和反转学习。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统贝叶斯方法在动物有限经验与认知容量下难以应对未知不确定性，需要更鲁棒的学习框架。
method: 从果蝇蘑菇体神经回路中得到启发，提出Hetlearn学习框架，通过牺牲渐近最优性来适应有限数据与环境变化。
result: Hetlearn在数据有限时比标准贝叶斯提供更准确的状态信息，且对统计环境的突变更不敏感。
conclusion: 该框架解释了果蝇蘑菇体的关键生理特征，并预测了二级条件作用和反转学习等跨物种保守的行为特征。
---

## 摘要
动物必须在一个不仅充满不确定性，而且由未建模的偶然事件（即“未知的未知”）塑造的世界中学习和做出预测。然而，当前关于这一过程的理论基于简单场景下的最优（贝叶斯）策略，在这些场景中，可以完整地表示世界模型并根据感官数据推断其状态。在动物先验经验和认知能力有限的情况下，这可能是不可行的，尤其是对于大脑较小、寿命较短的动物。受果蝇神经回路的启发，我们推导出一个学习框架，称之为“Hetlearn”，用于应对此类情况。Hetlearn牺牲了在理想化推理任务上的渐近最优性，使其对环境统计的突然变化不那么脆弱，并在数据有限时提供比标准贝叶斯过程更准确的状态信息。Hetlearn解释了果蝇蘑菇体关键生理和解剖特征，并预测了跨物种保守的学习行为特征，如二阶条件反射和逆转学习。

## Abstract
Animals must learn and make predictions in a world that is not only uncertain, but shaped by unmodelled contingencies: 'unknown unknowns'. Despite this, current theories of how this is achieved are based on optimal (Bayesian) strategies in simple settings, where it is possible to fully represent a model of the world and infer its state based on sensory data. This could be impractical in situations where an animal has limited prior experience and cognitive capacity, particularly in short-lived animals with small brains. Using the neural circuitry of Drosophila as inspiration, we derive a learning framework, which we call `Hetlearn', for coping in such situations. Hetlearn sacrifices asymptotic optimality on idealised inference tasks, making it less fragile to abrupt changes in environmental statistics and providing more accurate state information than standard Bayesian procedures when data are limited. Hetlearn explains key physiological and anatomical features of the Drosophila Mushroom body (MB), and predicts behavioural features of learning that are conserved across species, such as second-order conditioning and reversal learning.