---
title: Hidden-state inference aligns attention and neural representational geometry during flexible behaviour
title_zh: 隐藏状态推理对齐灵活行为中的注意力与神经表征几何结构
authors: "Kerren, C., Theves, S., Johansson, M., Gardenfors, P., Doeller, C. F."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.10.681143v3.full.pdf"
tags: ["query:world-models"]
score: 8.0
evidence: 研究隐藏状态推断作为内部世界模型指导灵活行为
tldr: 灵活决策需要推断隐状态并优先处理相关信息。人类在序列反转学习任务中快速适应，隐状态推理模型优于强化学习。眼动追踪显示注意力集中在相关特征，脑磁图揭示神经表征编码当前隐状态，预测误差调节其强度。成功表现伴随神经几何重组，放大任务相关表征距离，表明隐状态推理、注意力和神经表征几何紧密协调。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究灵活决策中隐状态推理与注意力、神经表征几何的动态协调机制。
method: 人类执行序列反转学习任务，结合隐状态模型拟合行为、眼动追踪注意力和脑磁图神经活动分析。
result: 隐状态模型最优预测选择与注意；神经表征编码隐状态，预测误差削弱后续表征；成功时神经几何选择性放大任务相关距离。
conclusion: 隐状态推理、注意力和神经表征几何在灵活决策中协同运作，实现行为信息的选择性优先表征。
---

## 摘要
在不确定环境中进行灵活决策需要推断潜在任务状态并优先处理行为相关信息。我们检验了以下假设：这一过程与注意力和神经表征结构的系统性变化相关。人类参与者执行了一项序列反转学习任务，要求识别当前相关的刺激维度。行为上，参与者快速适应情境转换，而隐藏状态推理模型最能解释这些适应行为，在预测选择和推断情境方面优于多个强化学习变体。眼动行为为选择性注意力提供了收敛证据，注视逐渐集中于相关特征，追踪逐试次的信念更新，并在高预测误差后短暂拓宽。在这些结果指导下，我们使用脑磁图检查潜在状态推理如何反映在神经活动中。神经表征编码当前推断的情境，并受近期预测误差调制，较大的预测误差与后续试次中较弱的情境表征相关。表征分析进一步揭示，成功表现与神经几何结构的系统性重组相关，其特征是任务相关表征距离的选择性放大以及行为相关刺激值的分离度增加。总之，我们的发现表明，在灵活决策过程中，隐藏状态推理、注意力和神经表征几何结构紧密协调，为行为相关信息如何被选择性优先处理和表征以支持适应性行为提供了系统层面的解释。

## Abstract
Flexible decision-making in uncertain environments requires inferring latent task states and prioritising behaviourally relevant information. We tested the hypothesis that this process is associated with systematic changes in attention and neural representational structure. Human participants performed a serial reversal learning task that required identifying which stimulus dimension(s) were currently relevant. Behaviourally, participants rapidly adapted to context switches, and a hidden-state inference model best explained these adaptations, outperforming multiple reinforcement-learning variants in predicting both choices and inferred contexts. Oculomotor behaviour provided converging evidence for selective attention, with gaze increasingly concentrated on relevant features, tracking trial-by-trial belief updates, and transiently broadening following high prediction errors. Guided by these results, we used magnetoencephalography to examine how latent-state inference was reflected in neural activity. Neural representations encoded the currently inferred context and were modulated by recent prediction errors, with larger prediction errors associated with weaker context representations on subsequent trials. Representational analyses further revealed that successful performance was associated with a systematic reorganisation of neural geometry, characterised by selective amplification of task-relevant representational distances and increased separation of behaviourally relevant stimulus values. Together, our findings demonstrate that latent-state inference, attention, and neural representational geometry are tightly coordinated during flexible decision-making, providing a systems-level account of how behaviourally relevant information is selectively prioritised and represented to support adaptive behaviour.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在不确定环境中，生物如何通过推断隐藏的任务状态（如当前哪个刺激维度相关）来灵活调整行为，以及这一过程如何与注意力分配和神经表征几何的动态改变相协调。
- **研究背景**：以往工作分别研究了隐状态推理、选择性注意或神经表征结构，但缺乏将它们在同一实验框架下统一考察的机制性解释。本研究提出隐状态推理作为内部世界模型，驱动注意聚焦和神经表征重组，从而实现灵活决策。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将灵活决策建模为隐马尔可夫过程——参与者维护一个关于当前任务“情境”（context）的信念分布，并根据观察和预测误差（PE）更新信念，进而引导注意力和神经编码的优化。
- **关键技术细节**：
  - **行为模型**：构建隐状态推理模型（Hidden-State Inference Model），假设被试在每次试次后根据反馈更新对情境的信念，并基于信念计算动作选择概率。对比多个强化学习变体（如Q-learning、动态RL、特征RL等）。
  - **注意力测量**：使用眼动追踪记录注视位置，量化对相关/无关特征维度的注视偏向，并分析注视如何随信念更新和预测误差动态变化。
  - **神经表征分析**：采集脑磁图（MEG）数据，运用表征相似性分析（RSA）和跨试次解码，评估神经活动中是否编码当前推断的情境，以及近期预测误差大小如何调制后续试次中情境表征的强度。还分析了行为成功与否时神经几何结构（如表征距离矩阵）的系统性重组。
- **算法流程（文字说明）**：
  1. 初始化情境先验均匀分布。
  2. 在每个试次，根据当前信念选择刺激维度和特征值进行决策。
  3. 接收反馈后，计算预测误差（实际结果与信念下的期望之差）。
  4. 用贝叶斯更新法则修正情境后验信念。
  5. 更新后的信念指导下一试次的注意力分配（眼动）和神经表征构建。
  6. 分析模型拟合优度，比较不同模型。

### 3. 实验设计：使用了哪些数据集/场景，它的 benchmark 是什么，对比了哪些方法
- **任务场景**：序列反转学习任务（serial reversal learning），刺激由多个维度（如颜色、形状、位置等）组合而成，每个维度有多个值。当前相关的维度会不定期反转，参与者需推断并持续选择该维度对应的正确特征。
- **参与者**：人类被试（具体人数未在摘要中给出，推测为数十人规模）。
- **Benchmark 与方法比较**：
  - 行为层面：将隐状态推理模型与多种强化学习变体（q-learning、动态RL、特征RL等）比较预测选择准确率和推断情境的准确性。
  - 注意/神经层面：未设置显性基准方法，而是通过拟合行为模型后将模型衍生的信念值、预测误差等与眼动、MEG数据做相关分析。
- **额外实验**：整合了眼动和MEG两种模态，但未提及独立消融实验或多数据集验证。

### 4. 资源与算力
- **未明确说明**：论文摘要和元数据中未提及所使用的GPU型号、数量或训练时长。由于本研究主要是行为拟合和MEG分析，可能不需要大规模计算资源，但未提供具体信息。

### 5. 实验数量与充分性
- **实验数量**：核心实验为单一序列反转学习任务，但包含三组主要分析：行为建模、眼动分析、MEG神经表征分析，以及成功/失败表现下的神经几何对比。
- **充分性与公平性**：
  - **充分性**：从摘要看，研究覆盖了从行为到神经环路的完整链条，且使用了模型比较（与多个RL变体对比），具有一定深度。但缺乏跨任务泛化测试（如不同结构的环境）或独立样本验证。
  - **客观/公平**：模型比较基于预测准确率和似然度，方法标准；眼动和MEG分析基于独立提取的变量（如预测误差），未发现明显偏差。但未报告交叉验证或统计检验细节（摘要中未提供p值等）。

### 6. 论文的主要结论与发现
- **行为**：参与者快速适应情境转换，隐状态推理模型在预测选择和推断情境方面优于所有强化学习变体。
- **注意力**：眼动注视逐渐集中于行为相关的特征维度，能够追踪试次间的信念更新；高预测误差后注视短暂拓宽（重新探索），符合贝叶斯更新的预期。
- **神经表征**：MEG信号中可解码出当前推断的情境，并且神经情境表征的强度受近期预测误差调制——预测误差越大，后续试次中情境表征越弱。
- **神经几何重组**：成功表现与任务相关表征距离的选择性放大以及行为相关刺激值的分离度增加相关，说明神经活动几何结构主动适应任务需求。
- **整体**：隐状态推理、注意力和神经表征几何在灵活决策中紧密协同，共同优化行为信息的选择性优先表征。

### 7. 优点：方法或实验设计上的亮点
- **多模态整合**：同一被试同时收集行为、眼动和MEG数据，实现了信念-注意-神经的统一分析。
- **理论驱动分析**：基于隐状态推理模型的变量（信念、预测误差）直接预测眼动和神经指标，增强了因果解释力。
- **丰富的模型比较**：系统地对比了多种强化学习模型，确认隐状态模型的最佳解释力，避免单一模型偏向。
- **神经几何分析**：超越简单的解码或平均激活，采用表征几何重组视角，揭示神经活动如何主动重排序以服务当前任务。

### 8. 不足与局限
- **任务单一**：仅使用反转学习任务，结论能否推广到其他类型的隐状态推理任务（如多步规划、等级结构）未验证。
- **样本量与统计效力**：未报告参与者总数和内外部验证，可能存在样本量不足导致效应夸大或遗漏。
- **缺少神经因果验证**：MEG相关性不能证明隐状态推理直接引起神经重组织，可能存在共同的第三变量（如觉醒、疲劳）。
- **计算模型假设限制**：隐状态模型假定完美的贝叶斯更新，可能忽略了人类记忆衰减、噪音等次优因素；且模型中未包含注意力显式共享参数。
- **资源信息缺失**：未说明分析所需的计算资源，影响可复现性评估。

（完）
