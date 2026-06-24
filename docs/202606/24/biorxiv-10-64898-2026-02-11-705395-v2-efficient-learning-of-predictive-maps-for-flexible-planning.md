---
title: Efficient Learning of Predictive Maps for Flexible Planning
title_zh: 高效学习预测地图以实现灵活规划
authors: "Bazarjani, A., Piray, P."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.11.705395v2.full.pdf"
tags: ["query:world-models"]
score: 9.0
evidence: 学习预测图以灵活规划，预测未来状态的世界模型
tldr: 行为灵活性的关键在于认知地图，但传统预测地图依赖当前策略，限制了规划能力。本文提出SR-IS模型，结合时序差分学习与重要性采样，学习策略无关的预测地图，可高效适应环境变化。实验表明SR-IS在规划任务中优于现有方法，并解释了人类重规划的渐变偏差，为大脑灵活决策提供了新见解。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有预测地图（如继任表示）依赖当前策略，限制了灵活规划，需要策略无关的认知地图。
method: 提出SR-IS模型，结合时序差分学习与重要性采样，构建策略无关的预测地图。
result: SR-IS在规划任务中优于现有模型，并能解释人类重规划的渐变偏差。
conclusion: SR-IS桥接了预测地图理论与规划行为，为认知中的灵活决策提供了新视角。
---

## 摘要
认知地图通过提供可重复使用的任务结构内部表征来实现灵活行为。继任表征是一种预测地图，编码预期的未来状态占用，已被提出作为大脑可能计算此类地图的一种方式，但其策略依赖性严重限制了灵活规划。我们引入了一个新模型，即带有重要性采样的继任表征（SR-IS），该模型结合了时序差分学习和重要性采样，以构建与策略无关的预测地图。SR-IS在不被智能体当前决策策略约束的情况下学习环境结构。当环境变化时，这些表征可以高效更新，从而实现快速的行为适应。我们表明，SR-IS在规划任务中优于现有模型，并更好地解释了先前模型无法解释的人类重新规划中的分级偏差。这项工作将预测地图理论与观察到的规划行为联系起来，为大脑中的灵活决策提供了新见解。

## Abstract
Cognitive maps enable flexible behavior by providing reusable internal representations of task structure. The successor representation, a predictive map that encodes expected future state occupancy, has been proposed as one way such maps might be computed in the brain, but its policy dependence severely limits flexible planning. We introduce a new model, the successor representation with importance sampling (SR-IS), which combines temporal-difference learning with importance sampling to construct policy-independent predictive maps. SR-IS learns the structure of the environment without being constrained by the agent's current decision policy. These representations can be efficiently updated when the environment changes, enabling rapid behavioral adaptation. We show that SR-IS outperforms existing models in planning tasks and provides a better account of the graded biases in human replanning that previous models could not explain. This work bridges theories of predictive maps with observed planning behavior and offers new insights into flexible decision making in the brain.

---

## 论文详细总结（自动生成）

# 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **认知地图**是大脑支持灵活行为的关键内部表征，传统强化学习模型中的**继任表征（SR）**通过缓存未来状态访问期望实现高效规划，但其**依赖于当前决策策略**，当目标或环境变化时无法灵活调整，导致行为僵化。
- 近年提出的**线性强化学习（Linear RL）**通过默认策略构建**与策略无关的预测地图（Default Representation, DR）**，可实现灵活重规划，但缺乏高效的在线学习算法——该地图只能通过计算密集型矩阵求逆获得。
- **本文核心问题**：如何在学习过程中（智能体按当前目标策略行动的同时）在线构建策略无关的预测地图，以同时实现灵活性、计算效率和更新效率？
- **整体意义**：提出**SR-IS（Successor Representation with Importance Sampling）**模型，通过将重要性采样融入时序差分（TD）学习，使智能体在按当前策略行动时能无偏学习默认策略下的预测地图，从而弥补SR与线性RL之间的空白，并为人类规划中的分级偏差提供统一计算解释。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- 利用**重要性采样**纠正因决策策略带来的采样偏差：当智能体按当前决策策略$\pi$行动时，TD更新中使用权重$w(s,s')$修正，使得学习到的状态-状态映射$M$逼近默认策略$\pi_d$下的DR。
- 默认策略设为**均匀分布**（或任意固定策略），从而让地图独立于目标任务。

### 关键技术细节
- **定义**：在确定性转移环境中，$w(s,s') = \frac{\pi_d(s'|s)}{\pi(s'|s)}$，其中$\pi(s'|s)$是当前决策策略下的转移概率。
- **TD更新规则**：
  $$M(s, :) \leftarrow (1-\alpha)M(s, :) + \alpha\left[\mathbf{1}_s^T + \gamma M(s', :)\right]w(s,s')$$
  其中$\mathbf{1}_s^T$是仅在状态$s$处为1的二进制行向量。
- **收敛性**：当采样充分时，$M$收敛到完整DR（即$M = (I - \gamma T)^{-1}$，$T$为默认策略下的转移矩阵）。
- **重规划**：继承线性RL的**低秩更新**（基于Woodbury引理），当环境变化（新障碍、新目标）时，只需在局部修改状态的矩阵上进行小规模求逆，无需重建整个地图。
- **决策策略**：使用softmax规则，温度参数$\beta$与控制成本参数$\lambda$关联（通常设为相等）。

### 算法流程（文字说明）
1. 初始化$M$为零矩阵。
2. 在每个时间步，智能体按当前决策策略$\pi$从当前状态$s$选择动作$a$，转移到$s'$并观测奖励。
3. 计算重要性权重$w(s,s') = \pi_d(s'|s) / \pi(s'|s)$。
4. 使用上述TD规则更新$M(s,:)$。
5. 重复步骤2-4，直至收敛。
6. 当需要重规划时，使用学习到的$M$，通过低秩更新公式快速计算新地图，然后利用$v = M r$计算新目标下的值函数并导出策略。

## 3. 实验设计：数据集、场景、基准方法与对比模型

| 实验场景 | 任务类型 | 对比模型 | 主要指标 |
|----------|----------|----------|----------|
| **四房间环境** (7×7) | 收敛性验证 | SR-IS, SR, 完整DR（矩阵求逆） | 平均绝对误差（vs 完整DR） |
| **四房间环境** | 跨房间重规划 | SR-IS, SR | 路径效率（按目标所在房间分类） |
| **复杂迷宫** (10×10) | 低秩更新重规划 | SR-IS, SR, SR* (SR+低秩更新), 完整DR | 路径长度 vs 随机游走 |
| **策略重评价** (Russek et al. 2017, 11×11迷宫) | 完全策略改变后偏好变化 | SR-IS, SR, 线性RL | 选择状态s1 vs s2的概率 |
| **人类重规划实验** (Momennejad et al. 2017, 树形任务) | 奖励/策略/转移重评价 | SR-IS, SR, 线性RL, MB, 混合SR+MB | 偏好切换概率（灵敏度） |
| **两步决策任务** (Kahn & Daw 2024) | 观察试验后选择 | SR-IS, SR, MB, 线性RL, 混合SR+MB, 人类数据 | 回归系数（MB签名、SR签名）；模型比较（保护超越概率） |
| **Tartarus迷宫** (de Cothi et al. 2022, 25种迷宫配置) | 跨物种导航轨迹预测 | SR-IS, SR, MB, MF, 混合SR+MB | 每步对数似然、最大似然分配比例、模型频率 |
| **随机转移环境** (7状态链) | 随机性下的行为偏好 | SR-IS, SR, MB, 混合SR+MB | 训练/测试阶段选择s2 vs s3的概率 |

- **基准**：完整DR（矩阵求逆，理论最优）作为上限；人类/动物数据作为行为参考。
- **参数设定**：多数仿真使用$\alpha=0.05$、$\gamma=0.9$、$\beta=\lambda=1$、非终止奖励$-0.1$、终止奖励$10$。

## 4. 资源与算力

- **论文未明确提及**使用的GPU型号、数量或训练时长。所有仿真均在标准CPU上完成（环境规模较小，如7×7、10×10网格，树形任务状态数少），无需大规模GPU算力。模型拟合使用MATLAB `fmincon`或Python `cbm`包，计算量较小。

## 5. 实验数量与充分性

- **实验组数**：论文包含**7组主要仿真**（收敛性、重规划、策略重评价、人类重规划、两步决策、跨物种导航、随机转移），每组又包含多种条件（如不同目标位置、不同重评价类型、不同迷宫配置）。
- **对比全面性**：对比了SR、MB、线性RL、混合SR+MB、MF等多种主流模型，并在多个场景下进行定量比较（绝对误差、路径效率、概率、回归系数、模型频率）。
- **统计可靠性**：多数结果报告了均值和误差（标准差或95%CI），并使用**随机效应贝叶斯模型选择**（保护超越概率）评估模型优势。
- **主观评价**：实验设计**充分**且**公平**，覆盖了从简单网格到复杂迷宫、从无噪声到随机转移、从模拟到人类/动物数据，能够全面展示SR-IS的优势和局限。唯有的不足是随机转移环境下的预测仅停留在模拟，没有人类数据验证。

## 6. 论文的主要结论与发现

1. **收敛性**：SR-IS通过重要性采样能在线收敛到默认策略下的完整预测地图（DR），而标准SR收敛到截然不同的策略依赖地图。
2. **重规划效率**：在迷宫重规划任务中，SR-IS路径效率接近理论上限的完整DR，显著优于SR和SR*，且能利用低秩更新快速适应环境变化。
3. **策略重评价**：SR-IS能成功适应完全策略改变（改变目标奖励），仅因采样方差略低于完整DR，而SR完全失败。
4. **人类行为匹配**：
   - 在Momennejad等人的人类重规划实验中，SR-IS**唯一**能复现“奖励重评价>策略重评价≈转移重评价”的分级不对称性（混合模型虽拟合但无规范解释）。
   - 在Kahn & Daw的两步任务中，SR-IS同时表现出显著的MB签名和SR签名，且**在模型比较中超越SR、MB、混合模型**（保护超越概率0.99）。
   - 在de Cothi等人的跨物种导航中，SR-IS对**57%的人类试验和52%的大鼠试验**给出最大似然解释，模型频率和保护超越概率均最高。
5. **单一规范机制**：SR-IS用同一个重要性采样机制解释了“双系统”行为，指出混合行为本身是学习策略无关地图过程中采样方差的自然产物。

## 7. 优点：方法或实验设计上的亮点

- **理论创新**：首次将重要性采样与TD学习结合用于学习策略无关的预测地图，填补了SR和线性RL之间的空隙。
- **计算高效**：在线TD更新，复杂度与标准SR相同；低秩更新使重规划只需小矩阵求逆。
- **行为预测力**：在多个公开人类/动物数据集上优于现有模型，且对重规划中的分级偏差给出规范（而非描述）解释。
- **实验设计严谨**：采用多个独立场景、多物种数据、完整的模型比较框架（保护超越概率），结果可信度高。
- **开源代码**：提供完整代码仓库，促进可复现性。

## 8. 不足与局限

- **确定性转移假设**：SR-IS继承线性RL的假设，在随机转移环境中可能产生系统偏差（如图7所示，在随机二步任务中不能正确选择最优动作）；论文指出人类可能通过更慢的MB规划弥补，但缺乏实验验证。
- **重要性采样方差**：当决策策略很少访问默认策略下的常见状态时，权重$w$可能很大，导致学习方差高、收敛慢；这在宏观环境中可能成为瓶颈。
- **非零概率要求**：决策策略必须对所有默认策略可能的动作赋予非零概率，无法处理完全贪婪策略；这限制了在强剥削情况下的应用。
- **低秩更新依赖基线地图质量**：若SR-IS地图学习不充分，低秩更新可能产生不良结果；论文仅通过偏移最小z值处理，未深入讨论。
- **应用范围**：只测试了离散、有限状态空间；未延伸到连续状态或函数近似场景。
- **神经基础**：论文未直接与神经记录（如海马)关联，虽讨论可能，但缺乏实证。
- **控制成本参数**：固定参数，未研究动态调整机制；且接近零控制成本时数值不稳定，与生物系统精度的关系未深入。

（完）
