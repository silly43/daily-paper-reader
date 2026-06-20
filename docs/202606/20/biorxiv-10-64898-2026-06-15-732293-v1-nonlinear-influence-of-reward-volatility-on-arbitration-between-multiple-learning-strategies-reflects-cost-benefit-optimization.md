---
title: Nonlinear influence of reward volatility on arbitration between multiple learning strategies reflects cost-benefit optimization
title_zh: 奖励波动性对多种学习策略间仲裁的非线性影响反映成本-收益优化
authors: "Yamada, T., Samejima, K."
date: 2026-06-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732293v1.full.pdf"
tags: ["query:world-models"]
score: 10.0
evidence: 基于世界模型的强化学习
tldr: 基于双系统强化学习理论，本研究探究奖励波动性如何调节模型自由与模型基础学习策略之间的仲裁。通过两项改进的两步决策任务实验（操纵奖励波动性和时间压力），结合模型无关分析、强化学习模拟和分层贝叶斯建模，发现奖励波动性对策略仲裁呈倒U型非线性影响：中等波动性时模型基础策略最强，且该效应仅出现在学会任务转换结构的个体中。时间压力则促进模型自由策略。结果表明人类在不确定环境中并非总是使用模型基础策略，支持成本-收益优化理论。
source: biorxiv
selection_source: fresh_fetch
motivation: 环境波动性（奖励波动）如何系统性调节模型自由与模型基础学习策略的仲裁尚不清楚。
method: 设计两项两步决策任务，操纵奖励波动性和时间压力，采用行为分析、强化学习模拟和分层贝叶斯模型拟合。
result: 奖励波动性对策略仲裁呈倒U型非线性效应，中等波动性时模型基础策略最强；时间压力增加促进模型自由策略。
conclusion: 人类在动态环境中并非总是使用模型基础策略，即使知道任务结构，也体现成本-收益优化。
---

## 摘要
行动选择涉及两个系统：无模型强化学习策略，它依赖于行动-结果对的经验；以及基于模型的强化学习策略，它通过使用对环境不变结构的模型进行推理，实现更灵活的行为。尽管环境变化需要更灵活的行为，但波动性（一种捕捉环境变化速度或频率的高阶统计量）系统性地调节这些策略的能力仍不清楚。我们使用两种修改后的两步决策任务，研究了奖励波动性对无模型和基于模型强化学习策略之间仲裁的影响。在实验1中，参与者在不同奖励波动性和时间压力水平下完成任务。在实验2中，我们在更广范围内系统地操纵奖励波动性，以评估波动性与学习策略之间的关系。使用模型无关的单次试验和多次试验回溯分析、强化学习模拟以及层次贝叶斯模型拟合对行为数据进行分析。跨实验发现，奖励波动性对无模型和基于模型强化学习策略之间的仲裁产生倒U形非线性效应，因为基于模型的学习策略在中等奖励波动性水平下被强烈驱动。这些调节效应仅在已学习任务中转移结构的个体中观察到，而那些未学习转移结构的个体则无论奖励波动性如何都依赖无模型学习策略。强化学习模拟显示，基于模型学习策略相对于无模型学习策略的相对优势在中等奖励波动性水平下达到峰值。此外，增加时间压力使行为转向无模型学习策略。这些结果表明，在不确定和动态环境中，人类并不总是使用基于模型的强化学习策略，即使他们了解任务结构，这支持了成本-收益优化。

## Abstract
Action selection involves two systems: a model-free reinforcement learning strategy, which relies on experience with action-outcome pairs, and a model-based reinforcement learning strategy, which enables more flexible behavior via inference using a model of the invariant environmental structure. Although environmental change requires more flexible behavior, the ability of volatility, a higher-order statistic that captures how rapidly or frequently the environment changes, to systematically modulate these strategies remains unclear. We examined the effects of reward volatility on arbitration between model-free and model-based reinforcement learning strategies using two modified two-step decision tasks. In Experiment 1, participants performed tasks with different levels of reward volatility and time pressure. In Experiment 2, we systematically manipulated reward volatility across a broader range to assess the relationship between volatility and learning strategy. Behavioral data were analyzed using model-agnostic one-trial and multitrial back analyses, reinforcement learning simulations, and hierarchical Bayesian model fitting. Across experiments, reward volatility exerted an inverse U-shaped nonlinear effect on the arbitration between model-free and model-based reinforcement learning strategies, as the model-based learning strategy was strongly driven at intermediate levels of reward volatility. These modulation effects were observed only in individuals who had learned the transition structure in the task, whereas those who had not learned the transition structure relied on the model-free learning strategy regardless of reward volatility. Reinforcement learning simulations revealed that the relative advantage of the model-based learning strategy over the model-free learning strategy peaked at intermediate levels of reward volatility. Additionally, increased time pressure shifted behavior toward the model-free learning strategy. These results demonstrated that, humans do not always use the model-based reinforcement learning strategy in uncertain and dynamic environments, even when they are aware of the task structure, supporting cost-benefit optimization.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：人类行为受习惯性（无模型强化学习，MF-RL）和深思熟虑（基于模型强化学习，MB-RL）双重系统控制。在动态环境中，如何在这两个系统之间切换是一个核心问题。先前研究表明，环境波动性（reward volatility）可能通过改变MF与MB的相对适应性来调节仲裁，但尚未系统检验波动性与MF-MB平衡之间的非线性关系（尤其是高波动性下MB是否失去优势）。
- **整体含义**：本文通过两项修改后的两步决策任务，揭示了奖励波动性对MF-MB仲裁的**倒U型非线性效应**——中等波动性时MB最强，低或高波动性时MB减弱。这支持了成本-收益优化理论：MB需要更高计算成本，仅在收益超过成本时被调用。此外，时间压力增加会导致转向成本更低的MF策略。结果强调人类在不确定环境中并非无条件使用MB，而是根据环境统计进行适应性优化。

## 2. 方法论

### 2.1 核心思想
- 基于强化学习中的双系统理论，构建**混合RL模型**，将MF和MB的价值函数加权组合：  
  $$Q_{\text{net}}(s_{\text{earth}}, a_i) = w \cdot Q_{\text{MB}}(s_{\text{earth}}, a_i) + (1-w) \cdot Q_{\text{MF}}(s_{\text{earth}}, a_i)$$
  其中$w$为平衡参数（0到1，越大越偏向MB）。
- 假设波动性影响$w$，且这种影响呈现非线性（倒U形），因为极低波动性下MF已足够，极高波动性下MB的预测可靠性下降。

### 2.2 关键技术细节
- **任务结构**：两步决策任务。第一步骤选飞船，概率性转移到第二步骤状态（常见/稀有转移）；第二步骤接收奖励。通过奖励与转移类型的交互项（transition×reward）区分MF与MB：MF表现为奖励主效应大、交互小；MB表现为交互大、奖励主效应小。
- **模型无关分析**：
  - **一次试验回溯**：使用广义线性混合模型（GLMM），以stay为因变量，预测变量包括转移类型、奖励、是否更好选择、条件。
  - **多次试验回溯**：使用广义线性模型（GLM），分析前多个试验的影响，并将效应量汇总。
- **模型拟合**：层次贝叶斯方法，假设所有参数（学习率$\alpha$、逆温度$\beta$、资格迹$\eta$、坚持性$p$、平衡参数$w$）可随波动性条件变化，独立估计。采用马尔可夫链蒙特卡洛（MCMC）采样。
- **收益模拟**：对每个波动性条件，模拟纯MF和纯MB代理在不同学习率和逆温度下的平均奖励，计算MB相对于MF的收益（体积差）。
- **参数恢复**：生成已知参数的数据，再拟合模型验证估计可靠性。

### 2.3 公式或算法流程（文字说明）
- **MF更新**（实验1用SARSA，实验2用Q-learning）：  
  第一步骤价值更新：$Q_{\text{MF}}(s_{\text{earth}}, a_i) \leftarrow Q_{\text{MF}}(s_{\text{earth}}, a_i) + \alpha [Q(s_k, a_j) - Q_{\text{MF}}(s_{\text{earth}}, a_i)]$（SARSA）或类似Q-learning形式。  
  第二步骤价值更新：$Q(s_k, a_j) \leftarrow Q(s_k, a_j) + \alpha [r - Q(s_k, a_j)]$。  
  资格迹用于将奖励传播回第一步骤。
- **MB更新**：利用已知的转移概率$P(s_k | s_{\text{earth}}, a_i)$，通过动态规划计算第一步骤价值：  
  $$Q_{\text{MB}}(s_{\text{earth}}, a_i) = \sum_k P(s_k | s_{\text{earth}}, a_i) \cdot \max_{a \in A_t} Q(s_k, a)$$（实验1中$A_t$为当前可用动作集；实验2中用状态值$V(s_k)$代替max值）。
- **选择概率**：softmax函数，包含坚持性项：  
  $$\pi(s, a) = \frac{\exp(\beta [Q(s,a) + p \cdot rep(a)])}{\sum_{a'}\exp(\beta [Q(s,a') + p \cdot rep(a')])}$$
- **模型无关分析**：GLMM公式包括主效应、所有两两及三重交互项，随机效应包括参与者和条件。

## 3. 实验设计

### 3.1 数据集/场景
- **实验1**（N=22，Aware组18人）：操纵奖励波动性（高斯随机游走标准差：低0.4、中1.1、高1.8）和时间压力（ITI 250ms vs 500ms）。同时包含一个状态-动作空间复杂度条件（中波动性下二动作 vs 一动作）。每个条件60个试次，重复两次共480试次。奖励量值连续。
- **实验2**（N=53，Aware组25人）：操纵奖励波动性采用奖励概率分布切换（Poisson分布参数$\lambda = 2,5,23,52$，对应极高、高、中、低波动性）。始终只有一动作，ITI固定350ms。奖励概率性。每个条件60试次，重复两次共480试次。
- **参与者分组**：根据后验问卷中是否能正确报告转移结构分为Aware和Unaware组。

### 3.2 Benchmark
- 无标准benchmark，但采用经典两步任务（Daw et al., 2011）的变体作为baseline，并与前人研究（Kool et al., 2016, 2017; Simon & Daw, 2011）进行定性比较。

### 3.3 对比方法
- 未对比其他模型或方法，内部设计包括：
  - 不同波动性条件相互对比。
  - Aware vs Unaware组对比。
  - 时间压力高/低对比。
  - 状态-空间复杂度（M1 vs M2）对比。
  - 模型对比：混合模型、纯MF、纯MB，通过WAIC选择最佳模型结构。

## 4. 资源与算力
- **文中未明确说明使用的GPU型号、数量或训练时长**。层次贝叶斯模型使用MCMC方法（Stan/Pyro等常见框架），模拟分析基于个人电脑或小型计算集群，但具体细节未报告。推测算力需求不大，因为数据量较小（参与者几十人，每人数百试次）。

## 5. 实验数量与充分性

- **两组实验**（实验1和实验2），实验2是实验1的延伸，覆盖更广波动性范围并纠正了实验1中高波动性下MB优势未下降的不足。
- **每个实验内分析**：进行了模型无关（一次/多次回溯）、模型拟合（多种模型比较）、模拟（收益、参数恢复）、以及与模拟数据的对比映射分析。
- **消融类分析**：
  - 比较Aware与Unaware组。
  - 比较时间压力的两个水平。
  - 比较状态-动作复杂度（M1 vs M2）。
  - 检查参数变化对模型无关效应量的影响（S4 Fig）。
  - 参数恢复验证（S6 Fig）。
  - 模型拟合优度与平衡参数的相关性分析（排除偏差）。
- **充分性评价**：实验设计较为充分，两种波动性操作方式（连续量/离散切换）都一致得到倒U型结果，增强了结论稳健性。但Unaware组样本量较小（实验1仅4人），实验2的Unaware组样本足够（23人），但Unaware组效应模式不同。总体实验数量合理，分析方法多样，结果一致。

## 6. 主要结论与发现

1. **奖励波动性对MF-MB平衡呈倒U型非线性影响**：在Aware组（学会转移结构的参与者），中等波动性时MB最强，低和高波动性时MB减弱。实验2中，这种非线性显著。
2. **效应仅发生在Aware组**：Unaware组中，模型无关分析未显示波动性对转移×奖励交互有显著调节，模型拟合显示Unaware组平衡参数随波动性增加而线性增加（高波动性更偏MB，但可能反映侥幸或策略不同）。
3. **时间压力增加促进MF策略**：较短的ITI（250ms）相比500ms导致更低的MB权重、更低的学习率和资格迹，说明MB需要更多时间成本。
4. **状态-动作空间复杂度**（M2 vs M1）导致更低的MB权重和更高的坚持性，表明复杂度增加认知负担，使人倾向于更简单的MF策略。
5. **收益模拟**支持：MB相对于MF的收益在中等波动性最大（实验2中$\lambda=5$附近），与行为数据峰值对应。
6. **显式知识是关键**：Aware组才表现非线性调节，说明明确知道转移结构是使用MB策略的前提，但即使知道，MB使用也会随波动性自适应调节。

## 7. 优点

- **系统操纵波动性**：实验2使用Poisson分布切换奖励概率，允许在宽广范围内考察波动性，克服了以往研究（如Kool et al.）同时操纵多种因素无法分离波动性效应的局限。
- **多种分析方法互补**：模型无关分析（一次/多次回溯）不依赖模型假设，模型拟合提供参数估计，RL模拟验证收益预测，参数恢复验证估计可靠性。三者结果一致。
- **倒U型假说明确且被证实**：理论上预测双系统在极低和极高波动性下MB优势减小，实验验证了该非线性关系，为成本-收益优化提供了直接证据。
- **关注参与者对结构知识的意识**：将Aware与Unaware分开分析，揭示显式知识是MB使用的前提，这一分离非常重要。
- **控制效应量混淆**：通过包含“是否更好选择”作为预测变量、以及比较RL模拟与实验数据的映射分析，排除了由于波动性差异导致的效应量变化归因于非w参数变化的可能。

## 8. 不足与局限

- **样本量**：实验1中Unaware组仅4人，无法对该组进行可靠统计检验。实验2的Unaware组样本足够，但两组间差异可能受其他因素（如动机、认知能力）影响。
- **模型局限性**：混合RL模型可能无法完全捕捉参与者真实策略，例如“成功表示”（successor representation）可模仿MB行为。作者承认无法在任务中区分SR和纯MB。此外，使用纯MF或MB的极端模型可能误分类行为。
- **波动性估计的在线过程**：文中未建模参与者如何实时估计波动性。实验中波动性条件被分块，参与者可能使用分块内统计学习。若能纳入在线波动性估计算法（如贝叶斯学习），可能更好地预测平衡参数峰值的偏移。
- **成本定义单一**：仅操纵时间压力作为成本代理，但MB可能还有其他认知成本（如工作记忆负荷）。未直接测量个体差异（如认知控制能力）对仲裁的影响。
- **生态效度**：任务为抽象计算机决策，且参与者只有少量训练（20个练习+480个主试），真实世界中的学习策略可能更复杂。
- **性别不平衡**：实验1中女性远多于男性，实验2也类似，可能影响泛化性。
- **未报告计算资源**：缺乏可重复性所需的具体算力信息。
- **高波动性下的表现**：实验2中$\lambda=2$条件下学习任务本身可能无意义（正确率未显著高于随机），在该条件下MB平衡参数的降低可能是由于策略失效而非成本-收益计算驱动。

（完）
