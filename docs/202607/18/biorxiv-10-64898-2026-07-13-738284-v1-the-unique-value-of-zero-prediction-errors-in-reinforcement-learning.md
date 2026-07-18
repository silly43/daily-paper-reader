---
title: The unique value of zero prediction errors in reinforcement learning
title_zh: 强化学习中零预测误差的独特价值
authors: "Lloyd, B., Kikumoto, A., Wurm, F., Vives, M.-L."
date: 2026-07-14
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.13.738284v1.full.pdf"
tags: ["query:world-models"]
score: 7.0
evidence: 研究强化学习中的零预测误差，与预测世界模型相关
tldr: 在强化学习中，零预测误差（结果完美匹配预期）是否具有独特价值尚不清楚。本研究通过人类强化学习任务，操纵部分试次结果与预测完全一致，发现零预测误差带来最高即时幸福感，计算模型揭示其诱导独特潜伏信念状态并引导后续更新，尤其在高度不确定性和不确定性不耐受个体中更显著。EEG结果显示零预测误差诱发独特的P3样神经响应，且残留神经活动能预测更新减弱。这表明完美预测并非中性，而是主动塑造情感、行为与神经处理的信息事件。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738284-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1701, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738284-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1684, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738284-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1677, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-13-738284-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1664, \"height\": 721, \"label\": \"Figure\"}]"
motivation: 探究零预测误差在心理学和计算层面是否具有独特意义，而非仅是中性事件。
method: 人类强化学习任务，操纵部分试次结果精确匹配预测，结合计算建模与EEG分析。
result: 零预测误差产生最高即时幸福感；行为由独特潜伏信念状态驱动；EEG显示独特P3样神经响应且预测更新模式。
conclusion: 完美预测不是中性，而是主动塑造情感、行为与神经反馈处理的信息事件。
---

## 摘要
学习通常被理解为由预测误差驱动的过程，即当结果与预期不符时。然而，完全匹配预期的结果是否具有心理学和计算上的意义仍不清楚。在这里，我们测试了零预测误差是否影响人类强化学习中的情感、信念更新和神经反馈处理。参与者在不确定程度不同的环境中反复预测奖励，其中一部分试验的结果被操纵以精确匹配他们的预测。零预测误差产生了最高的瞬时幸福感，计算模型表明，行为最好由一种模型解释，该模型中零预测误差诱发一种独特的潜在信念状态，指导后续更新，特别是在更高不确定性下以及对不确定性容忍度较低的个体中。结果锁定的脑电图分析进一步表明，零预测误差引发了独特的P3样反应，残留的神经活动预测了零预测误差后更新的减弱，而标准预测误差后更新的增强。这些发现表明，完美预测并非中性，而是主动塑造情感、行为和神经反馈处理的信息性事件。

## Abstract
Learning is typically understood as a process driven by prediction errors, when outcomes differ from expectations. Yet it remains unclear whether outcomes that perfectly match expectations are psychologically and computationally meaningful. Here, we tested whether zero prediction errors shape affect, belief updating, and neural feedback processing in human reinforcement learning. Participants repeatedly predicted rewards in environments varying in uncertainty, with a subset of trial outcomes manipulated to exactly match their predictions. Zero prediction errors produced the highest momentary happiness, and computational modeling showed that behavior was best explained by a model in which zero prediction errors induce a distinct latent belief state that guides subsequent updating, particularly under higher uncertainty and in individuals with greater intolerance of uncertainty. Outcome-locked EEG analyses further showed that zero prediction errors elicited distinct P3-like responses, with residual neural activity predicting attenuated updating after zero prediction errors but enhanced updating after standard prediction errors. These findings suggest that perfect predictions are not neutral, but informative events that actively shape affect, behavior, and neural feedback processing.