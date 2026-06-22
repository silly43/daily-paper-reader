---
title: A single computational objective can produce specialization of streams in visual cortex
title_zh: 单一计算目标可产生视觉皮层中的流特化
authors: "Finzi, D., Margalit, E., Kay, K., Yamins, D. L. K., Grill-Spector, K."
date: 2026-06-20
pdf: "https://www.biorxiv.org/content/10.1101/2023.12.19.572460v4.full.pdf"
tags: ["query:ssl"]
score: 9.0
evidence: 自监督拓扑深度神经网络用于视觉表示学习
tldr: 人类视觉皮层的背侧、外侧和腹侧流传统上被认为是为了支持不同视觉行为而特化。本研究使用自监督地形深度人工神经网络，结合大规模fMRI数据，发现为特定行为训练的模型无法解释大脑组织，而统一学习目标加局部空间约束的模型却准确预测了跨流的大脑反应、空间分离和功能分化。这挑战了“流源于行为专门化”的假设，表明视觉流可能源自单一计算原则——在空间约束下学习通用视觉表征。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究视觉皮层不同流的功能组织是否源于特定视觉行为的专门化，而非单一计算原则。
method: 构建自监督Topographic Deep ANN，在fMRI数据上训练，通过局部空间约束和通用表征学习模拟大脑组织。
result: 流特定行为训练的模型无法预测大脑响应与组织，而统一学习模型成功预测了跨流的大脑活动、空间分离和功能分化。
conclusion: 视觉流组织可能源于单一目标（学习通用视觉表征）加局部空间约束，而非行为专门化。
---

## 摘要
人类视觉皮层被组织为背侧、外侧和腹侧流。一个长期存在的假设是，这种功能组织成流的形式是为了支持不同的视觉行为。在此，我们使用基于神经网络的计算模型和大量fMRI数据集来研究视觉流出现的原因。我们发现，针对特定流视觉行为训练的模型难以捕捉大脑反应和组织。相反，一个自监督的拓扑深度人工神经网络，它鼓励邻近单元做出相似响应，成功预测了跨流的大脑反应、空间分离和功能分化。这些发现挑战了流行的观点，即流进化是为了分别支持不同的行为，而是表明功能组织可以源于一个单一原则：在局部空间约束下学习普遍有用的视觉表征。

## Abstract
Human visual cortex is organized into dorsal, lateral, and ventral streams. A long-standing hypothesis is that the functional organization into streams emerged to support distinct visual behaviors. Here, we use a neural network-based computational model and a massive fMRI dataset to investigate why visual streams emerge. We find that models trained for stream-specific visual behaviors poorly capture brain responses and organization. Instead, a self-supervised Topographic Deep Artificial Neural Network, which encourages nearby units to respond similarly, successfully predicts brain responses, spatial segregation, and functional differentiation across streams. These findings challenge the prevailing view that streams evolved to separately support different behaviors and suggest instead that functional organization can arise from a single principle: learning generally useful visual representations subject to local spatial constraints.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：人类视觉皮层被组织为背侧、外侧和腹侧流，传统观点认为这种功能分流是为了支持不同的视觉行为（如运动感知、物体识别等）。论文质疑这一假设，探究这些流是否可能源于一个单一计算原则：在局部空间约束下学习通用的视觉表征。
- **整体含义**：如果单一学习目标就能解释视觉流的分化，则意味着大脑的功能组织并非由行为专门化驱动，而是由更基础的普适表征学习与空间约束相互作用产生。这挑战了神经科学中关于视觉系统模块化分工的主流假说，启发我们重新思考大脑组织原则。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：使用自监督拓扑深度人工神经网络（Topographic Deep ANN），通过一个统一的学习目标（自监督表征学习）加上局部空间约束，模拟视觉皮层不同区域的反应模式，而不需要为每个流设置独立的行为目标。
- **关键技术细节**：
  - 采用自监督学习（如对比学习）训练神经网络，使其学习通用的视觉表征（无需类别标签）。
  - 引入拓扑约束：鼓励网络中空间邻近的神经元（或单元）对输入产生相似的响应，模拟皮层中功能柱的局部相关性。
  - 将网络的不同层或不同模块映射到fMRI观测的脑区，通过预测脑响应来验证模型。
- **无具体公式/算法流程**（论文摘要未提供），但整体流程为：构建深度神经网络 → 自监督训练 + 空间约束 → 模型输出 → 与人类fMRI脑活动对比 → 评估预测能力。

### 3. 实验设计：数据集、基准与对比方法

- **数据集**：大规模fMRI数据集（具体名称未在摘要中给出，但提及“massive fMRI dataset”），包含人类视觉皮层对大量自然图像的反应。
- **基准（Benchmark）**：未明确提及标准基准，但实验评估指标包括模型预测的脑响应与真实fMRI响应的匹配程度、空间分离度（不同流之间的分离程度）、功能分化程度。
- **对比方法**：
  - **流特定行为训练的模型**：为模拟背侧/外侧/腹侧流功能而分别训练的网络（例如，一个用于运动感知，一个用于物体识别等）。
  - **标准自监督模型**：无拓扑约束的自监督网络。
  - **监督学习的模型**（可能还包括传统的层级模型）。
- 结果显示：只有自监督拓扑网络能够同时预测跨流的大脑反应、空间分离和功能分化，而流特定模型表现差。

### 4. 资源与算力

- **未明确说明**：论文摘要及元数据中未提及使用的GPU型号、数量、训练时长等算力信息。需要阅读全文才能获得。因此这里只能指出信息缺失。

### 5. 实验数量与充分性

- **实验数量**：从摘要推断，至少包含以下对比：
  1. 多种模型（流特定、标准自监督、拓扑自监督）在不同fMRI数据上的预测实验。
  2. 对空间分离和功能分化的定量分析。
  3. 可能包括消融实验（去掉拓扑约束的效果）。
- **充分性评估**：
  - 比较了多个竞争模型，覆盖了主流假设（行为专门化 vs. 单一目标）。
  - 使用大规模fMRI数据，样本量较大。
  - 但缺少对模型泛化性（其他数据集）、不同自监督架构、不同空间约束强度等维度的细致分析。总体而言实验设计较为有力，但论文篇幅有限可能未能展示所有消融实验。

### 6. 论文的主要结论与发现

- **主要结论**：人类视觉皮层的功能分流（背侧、外侧、腹侧）并非源于为不同行为专门化的训练，而是可以由一个单一计算目标——在局部空间约束下学习通用的视觉表征——自然涌现。
- **具体发现**：
  - 针对单独行为训练的模型无法拟合大脑组织。
  - 自监督拓扑深度网络成功预测了跨流的大脑活动、空间分离和功能分化。
  - 这一结果挑战了“流是为不同行为进化”的经典观点，支持了“单一原则+空间约束”的假说。

### 7. 优点

- **方法创新**：将自监督学习与拓扑约束结合，为大脑功能组织提供了一种新的计算解释，避免了手工设定任务目标的主观性。
- **直接验证**：直接使用大规模fMRI数据作为地面真值，定量比较模型预测，结果客观。
- **挑战旧范式**：用简约原则（单一目标）解释复杂的脑区组织，具有理论简洁性和收敛性。
- **可推广性**：该方法可以应用于其他感觉皮层或跨物种研究。

### 8. 不足与局限

- **实验覆盖有限**：只使用了单一fMRI数据集，未在其他数据集或不同刺激条件下验证（如运动、深度等）。
- **局限性**：
  - 拓扑约束的具体形式（如何定义“邻近”、“相似响应”）可能对结果敏感，但未充分探讨不同约束的效果。
  - 模型架构可能仍无法完全捕捉真实皮层的细节，例如层级间的反馈连接、时间动态等。
  - 未能排除弱行为专门化的可能性——单一目标下涌现的流可能仍暗含对不同行为的偏向，只是未被显式建模。
- **算力信息缺失**：未公开训练成本，不利于复现和评估实际可行性。
- **偏差风险**：自监督学习目标本身可能隐含对某些视觉特征的偏好（如物体形状），这可能已包含了“行为偏向”，但论文未充分讨论。

（完）
