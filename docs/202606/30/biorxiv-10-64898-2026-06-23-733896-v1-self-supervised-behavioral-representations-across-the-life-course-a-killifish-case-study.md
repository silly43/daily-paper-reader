---
title: "Self-Supervised Behavioral Representations Across the Life Course: A Killifish Case Study"
title_zh: 跨生命历程的自我监督行为表征：以鳉鱼为例
authors: "Chang, J.-C., Komatsu, T. S., Onami, S."
date: 2026-06-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.23.733896v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 自监督行为表征学习
tldr: 研究使用非洲鳉鱼完整生命周期行为数据，构建自监督模型LifeMAE。发现仅凭单日行为就能预测年龄、区分寿命和检测临近死亡；完整生命周期编码并未提升表现，近死亡预测的改进源于时间编码而非行为。结果表明单日行为足以表征生命进程，应优先大量个体短期观测，并警惕时间编码泄漏目标导致的虚假提升。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决自监督衰老模型中因数据片段化而无法评估全生命周期建模必要性的问题。
method: 基于非洲鳉鱼完整生命周期录像，构建两阶段自监督模型LifeMAE：日编码器+生命周期编码器，并对比单日与全序列模型。
result: 单日编码器在年龄、寿命区分上等效或优于全生命周期模型；近死亡预测的增益来自时间位置编码。
conclusion: 个体生命进程在单日行为中已可辨识，支持短时观测策略，且评估需固定时间点避免时间泄漏偏差。
---

## 摘要
基于自我监督的衰老基础模型越来越多地建立在纵向数据（生物银行、电子健康记录、可穿戴设备）之上，这些数据本质上是不完整的：没有个体被追踪整个生命周期，每个生命被记录的部分也差异很大。这引发了两个相互关联的问题：建模个体的整个生命历程而非其当前状态是否值得？这样的模型能否从简短、零碎的记录中构建？没有人类队列能解决这些问题，因为没有任何一个队列能提供完整生命进行对比。我们转而使用非洲绿松石鳉鱼（Nothobranchius furzeri）作为受控实验平台，这些鱼从幼年到自然死亡都被公开录制的记录追踪：其完整的寿命提供了人类数据所缺乏的全生命参考。在这些数据上，我们构建了LifeMAE，一个两阶段自我监督模型：一个日编码器总结每一天的行为，然后一个生命历程编码器处理这些每日总结的轨迹。我们发现仅日编码器就非常强大：从单个行为日就能预测时序年龄，粗略区分长寿与短寿个体，并标记死亡临近。添加生命历程编码器在这三个任务上均未提升；每个任务都可通过简单聚合日级别预测（年龄使用平滑器，寿命使用早期生命平均值）来匹配。短期死亡率似乎是例外，其中全生命周期模型看起来好得多（AUROC 从0.81到0.91），但增益并非源于行为：它反映了每天在观测窗口中的位置（模型对时间的编码提供的线索），而给定该线索的单日模型在任何观测长度下都能缩小差距。对于这些特征，个体在其生命历程中的位置可以从单日行为中解读：轨迹阶段是不必要的，所需记录短至一天，这是我们的日级别设置所能分辨的最细粒度。对于队列特征描述，这倾向于快速观测许多个体而非长期追踪少数。这一结果加入了日益增多的工作，其中深度模型和基础模型在公平基准下未能击败故意简单的基线。我们为过度乐观增添了一个具体机制：模型对时间的编码可能泄露其预测的数量，而回溯性评估将其误认为是学到的生物学，因此只有固定在预测时刻的评估才是可信的。

## Abstract
Self-supervised foundation models of aging are increasingly built from longitudinal data (biobanks, electronic health records, wearables) that is inherently incomplete: no individual is followed across a whole lifetime, and how much of each life is captured varies widely. This raises two linked questions: is it worth modeling an individual's whole life course rather than its current state, and can such a model be built from brief, fragmentary records? No human cohort can settle them, because none offers a complete life to compare against. We turn to the African turquoise killifish (Nothobranchius furzeri), tracked from youth to natural death in publicly released recordings, as a controlled testbed: its complete lifespans provide the full-life reference that human data lacks. On these data we build LifeMAE, a two-stage selfsupervised model: a day encoder that summarizes each day of behavior, then a life-course encoder over the trajectory of those daily summaries. We find that the day encoder alone is already strong: from a single day of behavior it predicts chronological age, separates long- from short-lived individuals (coarsely), and flags nearness to death. Adding the life-course encoder improves on none of the three; each is matched by trivially aggregating the day-level predictions (a smoother for age, an early-life average for lifespan). Near-term mortality seems the exception, where the whole-life model looks far better (AUROC 0.81 to 0.91), but the gain is not behavioral: it reflects where each day falls within the observation window (a cue supplied by the model's encoding of time), and a single-day model given that cue closes the gap at any observation length. For these traits, an individual's place in its life course is legible from a single day: the trajectory stage is unnecessary, and the record it needs is as short as one day, the finest grain our day-level setup resolves. For characterizing a cohort, this favors observing many individuals briefly over tracking a few for long. The result joins a growing body of work in which deep and foundation models, fairly benchmarked, fail to beat deliberately simple baselines. We add a concrete mechanism for the over-optimism: a model's encoding of time can leak the very quantity it predicts, which backwardlooking evaluation mistakes for learned biology, so only evaluation fixed to the moment of prediction is trustworthy.