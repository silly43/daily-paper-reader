---
title: "Inside insight: decoding how insight emerges from competing world models"
title_zh: 洞察内部：解码洞察如何从竞争的世界模型中涌现
authors: "Inutsuka, K., Nishioka, T., Macpherson, T., Fujiwara, M., Hikida, T., Naoki, H."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.21.726889v2.full.pdf"
tags: ["query:world-models"]
score: 9.0
evidence: 智能体内部世界模型
tldr: 洞察被认为是世界模型的重组，但其潜在动态难以通过行为直接测量。本文提出Inside Insight Dynamics (IID)框架，利用机器学习从行为数据中估计世界模型的动态变化。通过分析小鼠在间接与直接规则任务中的行为，IID成功推断出洞察式转变的时刻，并揭示不同学习机制：间接任务由门控学习驱动，直接任务由并行学习驱动。该框架为仅从行为数据量化洞察动态提供了新途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以从行为数据直接揭示洞察产生背后的世界模型动态重组过程。
method: 开发Inside Insight Dynamics (IID)框架，通过机器学习从行为数据估计世界模型的潜在动态。
result: 在小鼠间接与直接规则任务中，IID推断出洞察转变时间，并发现分别由门控学习和并行学习解释。
conclusion: IID提供了一种仅从行为数据量化洞察动态的有效方法，可应用于多种认知任务。
---

## 摘要
洞察何时以及如何涌现？我们将洞察概念化为一种来自对世界模型进行重构的突然领悟：世界模型是一种将行动与结果联系起来的内部解释。然而这些潜在动态即使通过行为和口头报告也难以获取。在此，我们开发了内部洞察动力学（IID），一个从行为数据中估计潜在世界模型动态的机器学习框架。使用IID，我们分析了小鼠在间接规则任务和直接规则任务中的行为，每个任务都需要从初始世界模型转换到规则一致的表征。IID通过估计竞争世界模型之间转换的时间点推断类洞察转变的“何时”，并通过比较其背后的不同学习过程来考察“如何”。这一分析揭示了世界模型学习的不同机制：间接规则任务和直接规则任务分别被门控学习和并行学习更好地解释。因此，IID开辟了一条仅从可观察行为量化潜在洞察动态的途径。

## Abstract
When and how does insight emerge? We conceptualize insight as a sudden realization arising from restructuring a world model: an internal interpretation linking actions to outcomes. Yet these latent dynamics remain difficult to access, even with behavior and verbal report. Here we developed inside insight dynamics (IID), a machine-learning framework that estimates latent world-model dynamics from behavioral data. Using IID, we analyzed mouse behavior in indirect- and direct-rule tasks, each requiring a shift from an initial world model to a rule-consistent representation. IID inferred the "when" of insight-like shifts by estimating the timing of transitions between competing world models, and examined the "how" by comparing alternative learning processes underlying them. This analysis revealed distinct mechanisms of world-model learning: the indirect- and direct-rule tasks were better explained by gated learning and parallel learning, respectively. Thus, IID opens a route to quantifying latent insight dynamics from observable behavior alone.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：洞察（insight）作为一种突发的领悟，传统上被理解为内部世界模型的重组，但这一潜在动态过程难以直接通过行为或口头报告测量。论文试图回答两个关键问题：**何时**发生类洞察转变，以及**如何**（通过何种学习机制）实现这种转变。
- **整体含义**：将洞察形式化为竞争世界模型之间的转换，并开发一种计算方法从纯行为数据推断这些隐藏动态。这不仅为研究动物模型中的洞察提供了定量工具，而且揭示了不同任务结构下学习机制的分化，拓展了对灵活认知中内部模型重组过程的理解。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：假设动物的行为由两个竞争的内部世界模型共同驱动：一个侧依赖模型（将奖励解释为取决于所选择的左右侧）和一个线索依赖模型（将奖励解释为取决于线索身份）。洞察被定义为这两个模型相对主导权（用一个潜在权重变量 $w_t$ 表示）的时变转换。
- **关键技术细节**：
  - **多世界模型决策模型**：每个世界模型 $m \in \{\text{side}, \text{cue}\}$ 维护一个潜在奖励状态 $z_{t,s}^{(m)}$，服从随机游走 $z_{t,s}^{(m)} = z_{t-1,s}^{(m)} + \epsilon_t^{(m)}$，奖励概率为 $\sigma(z_{t,s}^{(m)})$。信念近似为高斯分布，后验均值更新公式为：
    $$
    \mu_{t,s}^{(m)} = \mu_{t-1,s}^{(m)} + \alpha \cdot g_t^{(m)} \cdot I_{t-1,s}^{(m)} K_{t,s}^{(m)} \left( r_{t-1} - \sigma(\mu_{t-1,s}^{(m)}) \right)
    $$
    其中 $g_t^{(m)}$ 是门控项，$K_{t,s}^{(m)}$ 是类似卡尔曼增益的系数，$\alpha$ 是学习率。
  - **门控学习 vs 并行学习**：
    - 门控学习：$g_t^{(\text{side})} = 1-\sigma(w_t)$, $g_t^{(\text{cue})} = \sigma(w_t)$，即模型更新受当前依赖权重缩放。
    - 并行学习：$g_t^{(m)} = 1$，两个模型同时更新，与当前依赖无关。
  - **行动选择**：整合两个模型的期望奖励，用 softmax 选择行动，温度参数 $\beta=1$。
  - **Inside Insight Dynamics (IID) 框架**：构建一个观测者状态空间模型（observer-SSM），将未观测到的权重 $w_t$ 和信念变量视为隐藏状态，通过粒子滤波（粒子数 $N$，自适应重采样）从行为序列（行动和奖励历史）中顺序推断后验分布。利用代表性轨迹（基于累积观测对数似然的分层选择）可视化潜在动态。

## 3. 实验设计：数据集、场景、基准与对比方法

- **数据集**：来自先前发表的 Nishioka et al. (2023) 的小鼠视觉辨别任务，包括两个版本：
  - **间接规则任务**（原称 VD-Inhibit）：固定线索 A 总是与无奖励相关，其他随机线索有奖，小鼠需学会抑制对 A 的反应。
  - **直接规则任务**（原称 VD-Attend）：固定线索 B 总是有奖，其他随机线索无奖，小鼠需学会选择 B。
- **场景与基准**：
  - 分析初始学习期，从第一次训练到达到标准（连续两天 >80% 正确）。间接任务 10 只小鼠，直接任务 12 只小鼠。
  - 作为行为基准，对累积奖励曲线进行分段线性拟合，估计行为改变点（breakpoint）。
- **对比方法**：主要对比门控学习模型与并行学习模型，通过比较每个模型预测行动序列的每一步对数似然（predictive log-likelihood）来评估哪个机制更优。模型偏好被量化为在转变定义的分析窗口内逐步对数似然差值的平均值（门控减并行，正值表示门控更好）。

## 4. 资源与算力

- **未明确说明**：论文未提及使用的 GPU 型号、数量或训练时长。粒子滤波和参数推断在 CPU 上也可能完成，但作者未披露具体硬件信息。需要指出这一点。

## 5. 实验数量与充分性

- **实验组数**：
  - 行为描述性分析：每个任务展现了 1 个代表性小鼠的详细轨迹（见 Fig. 2），所有小鼠的个体轨迹在补充图中给出（Fig. S2, S3）。
  - IID 逆估计：间接任务展示了 2 只会小鼠的结果（Fig. 3）；直接任务类似。
  - 模型比较：间接任务 10 只小鼠，直接任务 12 只小鼠，每只小鼠使用 15 个随机种子独立运行粒子滤波以评估稳定性。每个模型得到“洞察时间”和逐步对数似然。
  - 仿真验证：使用已知真实潜在动态生成行为数据，再应用 IID 恢复，验证其可恢复性（补充 Fig. S4）。
- **充分性**：实验覆盖了两种任务类型、多个个体、并使用了重复种子。对比方法直接且符合贝叶斯模型比较标准。但样本量较小（10、12 只小鼠），且仅为雄性 C57BL/6J 小鼠，可能限制泛化性。没有进行跨任务交叉验证或独立测试集评估。整体实验设计合理，但充分性中等。

## 6. 论文的主要结论与发现

- **主要发现**：
  - IID 能从行为数据中成功估计出世界模型依赖权重 $w_t$ 的时变轨迹，表征洞察式转变的“何时”。
  - 在间接规则任务中，**门控学习模型**比并行学习模型更好地预测了 7/10 只小鼠的行动，表明学习依赖于当前模型依赖权重。
  - 在直接规则任务中，**并行学习模型**在 9/12 只小鼠中更优，表明当规则更直接时，两个世界模型可以同时更新。
  - 因此，洞察式行为转变的底层计算机制不是固定的，而是取决于任务结构。
  - IID 检测到的潜在转变往往早于累积奖励曲线上的行为改变点，暗示它捕捉到了内在重组过程。

## 7. 优点：方法或实验设计上的亮点

- **方法论创新**：IID 将洞察建模为竞争世界模型之间的权重转移，并提供了一个完整的逆推断框架，仅通过行为数据恢复潜在动态，无需主观报告或神经记录。
- **机制可区分**：明确建模门控学习与并行学习两种替代机制，并通过模型比较进行区分，使得计算机制可检验。
- **验证充分**：通过仿真验证了 IID 能够恢复已知的真实潜在动态（包括权重和信念），增强了可信度。
- **跨任务对比**：揭示相同计算方法在不同任务结构下表现不同，说明了任务依赖性的存在，具有启发意义。
- **与行为指标结合**：将 IID 推断的转变时间与传统累积奖励改变点对比，展示其超前性，强化了内在重组先于外显表现的论点。

## 8. 不足与局限

- **模型假设简化**：仅考虑两个竞争世界模型（侧依赖和线索依赖），而动物的真实内部假设空间可能更丰富（如对每个单独线索进行建模等）。模型的候选集是假设性的而非从数据中自动发现。
- **样本量与人口学限制**：仅使用雄性 C57BL/6J 小鼠，每组 10-12 只，样本量较小，可能无法代表更广泛的群体，且无女性动物，存在性别偏差风险。
- **未涉及神经数据**：虽然在讨论中展望了与神经活动关联的可能，但论文本身没有提供任何神经记录或因果干预来验证 IID 推断过程的神经基础。
- **参数固定**：学习率 $\alpha$、随机游走方差 $\sigma_z^2$、权重方差 $\sigma_w^2$ 等均预先固定而非从数据拟合，可能影响模型比较的公平性。论文称其在模型比较前固定并保持一致，但未充分论证这些参数选择的敏感性。
- **模型比较窗口定义**：分析窗口基于本身来自模型推断的阈值跨越时间，可能存在循环依赖风险，尽管使用了两个模型的中位数时间。
- **结果外推性**：仅适用于特定视觉辨别任务，能否推广到其他更复杂的洞察任务（如人类经典问题解决范式）尚不清楚。

（完）
