---
title: Connectome-scale self-supervised representation learning reveals neuronal organization beyond canonical labels
title_zh: 连接组尺度的自监督表示学习揭示超越经典标签的神经元组织
authors: "Shi, T., Chen, Y., Liu, C., Zhang, R."
date: 2026-07-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735468v1.full.pdf"
tags: ["query:ssl"]
score: 9.0
evidence: 在连接组尺度上使用对比学习的自监督表示学习
tldr: 密集电子显微镜连接组提供突触级结构，但融合结构与连接的可扩展表示学习困难。本文提出自监督框架，用层次图神经网络和骨骼分解进行对比学习，坐标无关拓扑减少混淆。精细骨骼保留更丰富身份信息；结构嵌入改善亚型区分；多跳学习发现半球连接侧向化和亚群。实现了无需预设标签的大规模连接组发现。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以从密集连接组中学习融合结构与连接的可扩展表示。
method: 自监督框架，层次图神经网络结合骨骼分解进行对比学习，使用坐标无关拓扑。
result: 精细骨骼保留丰富身份信息；结构嵌入改善亚型区分；多跳学习揭示半球连接侧向化和亚群。
conclusion: 建立可扩展自监督框架，无需预设标签即可发现神经元身份和连接组组织。
---

## 摘要
密集电子显微镜连接组提供了神经元结构和连接的突触级图谱，但学习能够整合结构和连接性、以最少人工干预进行连接组发现的可扩展表示仍然困难。本文提出了一种用于密集连接组中结构-连接性表示学习的自监督框架。通过骨架分解的层次图神经网络实现了对精细采样的FlyWire神经元骨架的对比学习，表明精细骨架比粗粒度表示保留了更丰富的身份信息。无坐标拓扑减少了发育和几何混淆，改进了聚类和标签高效推理。然后，我们利用学习到的结构嵌入作为突触伙伴的连续描述符，构建结构驱动的连接性表示，无需预定义的伙伴类型标签即可改善亚型区分。迭代多跳学习进一步揭示了高阶组织，包括半球连接偏侧化和连接性定义的亚群。注意力分析将这些差异与特定的突触伙伴联系起来。这些结果共同建立了一个自监督且可扩展的框架，用于在大规模密集连接组中发现神经元身份和连接组组织。

## Abstract
Dense electron-microscopy connectomes provide synaptic-resolution maps of neuronal structure and wiring, but learning scalable representations that integrate structure and connectivity for connectome discovery with minimal human intervention remains difficult. Here we present a self-supervised framework for structure-connectivity representation learning in dense connectomes. A hierarchical graph neural network with skeleton decomposition enables contrastive learning from finely sampled FlyWire neuronal skeletons, showing that fine skeletons preserve substantially richer identity information than coarse representations. Coordinate-free topology reduces developmental and geometric confounds, improving clustering and label-efficient inference. We then use learned structural embeddings as continuous descriptors of synaptic partners to construct structure-driven connectivity representations, improving subtype discrimination without predefined partner-type labels. Iterative multi-hop learning further reveals higher-order organization, including hemispheric connectivity lateralization and connectivity-defined subgroups. Attention analysis links these differences to specific synaptic partners. Together, these results establish a self-supervised and scalable framework for discovering neuronal identity and connectome organization in a large-scale dense connectome.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究动机**：密集电子显微镜连接组提供了突触级的神经元结构与连接图谱，但现有方法难以从这种大规模数据中学习能够同时整合结构与连接性、且可扩展的表征，往往需要大量人工标注。
- **整体含义**：本文提出一种自监督表示学习框架，能够在无需预设标签的前提下，从密集连接组中自动发现神经元身份和连接组高阶组织。这为连接组学中的无监督发现和标签高效推理提供了新途径，有助于揭示传统分类体系之外的神经元组织原则。

### 2. 方法论

- **核心思想**：利用自监督对比学习，在神经元骨架的精细尺度上学习结构-连接性融合表征，并通过无坐标拓扑、多跳学习等手段进一步挖掘组织规律。
- **关键技术细节**：
  - **层次图神经网络 + 骨架分解**：将神经元骨架分解为精细采样的片段（fine skeletons），构建层次图，通过对比学习拉近同一神经元不同骨架片段的表征，推开不同神经元的表征。
  - **对比学习目标**：采用标准对比损失（如InfoNCE），基于正负样本对进行训练。
  - **坐标无关拓扑**：在训练中去除骨架节点的空间坐标信息，仅利用拓扑结构，从而消除发育和几何上的混淆因素，使表征更专注于连接组组织的本质特征。
  - **结构驱动的连接性表示**：将学习到的结构嵌入作为突触伙伴的连续描述符，构建结构-连接性融合表征，无需预定义的伙伴类型标签。
  - **迭代多跳学习**：通过多轮（multi-hop）信息传递，揭示高阶组织模式，如半球连接偏侧化和连接性定义的亚群。
  - **注意力分析**：利用注意力机制识别与特定差异（如偏侧化）相关的关键突触伙伴。

### 3. 实验设计

- **数据集**：使用 **FlyWire** 数据集的果蝇半脑连接组（密集EM重建的突触级连接组）。
- **Benchmarks**：
  - 聚类效果（如NMI、ARI等）
  - 标签高效推理（半监督场景下，少量标注后的分类性能）
  - 神经元亚型区分能力（通过OOD检测或聚类纯度评估）
  - 高阶组织发现（如半球连接偏侧化的量化、亚群划分的合理性）
- **对比方法**：
  - 粗粒度骨架 vs 精细骨架（验证精细骨架更优）
  - 有/无坐标拓扑（验证坐标无关拓扑的效果）
  - 消融实验：去除结构嵌入、去除多跳学习等
- **注意**：文中未明确与其他自监督学习方法（如GraphCL、SimGRACE等）进行对比，也未使用公开的神经元类型标注数据集进行定量分类评测。实验主要围绕FlyWire自身结构进行内部验证。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量及训练时长。仅能推断该方法在FlyWire数据集上可训练，但具体硬件需求未报告。

### 5. 实验数量与充分性

- **实验数量**：摘要提及了多个分析维度，包括：
  1. 精细骨架 vs 粗粒度骨架的对比学习效果。
  2. 坐标无关拓扑对聚类和标签高效推理的影响。
  3. 结构嵌入对亚型区分的改进。
  4. 多跳学习揭示偏侧化和亚群。
  5. 注意力分析关联具体突触伙伴。
- **充分性与公平性**：
  - **优点**：实验覆盖了自监督学习的多个关键环节（骨架粒度、拓扑、结构嵌入、高阶结构），消融设计合理，每个组件都得到验证。
  - **不足**：
    - 缺少与其他现有自监督图学习方法的直接对比（如对比损失是否采用标准设置、是否有baseline如随机初始化表征）。
    - 未提供统计显著性检验或多次重复实验的结果。
    - 仅使用FlyWire一个数据集，泛化性验证不足。
    - 缺乏对下游任务（如神经类型分类）的公开基准测试。

### 6. 论文的主要结论与发现

- 精细骨架比粗粒度骨架保留了更丰富的神经元身份信息。
- 坐标无关拓扑减少了发育和几何混淆，显著改善了聚类和标签高效推理。
- 结构嵌入作为突触伙伴的连续描述符，无需预设伙伴类型即可改善亚型区分。
- 迭代多跳学习揭示了高阶组织现象，包括半球连接偏侧化和连接性定义的亚群。
- 注意力分析将这些偏侧化差异与特定的突触伙伴联系起来。
- 总体建立了**自监督且可扩展**的框架，能够在大规模密集连接组中实现无标签发现。

### 7. 优点

- **自监督性**：无需人工标注，可直接从结构与连接数据中学习，适用于未标注的大规模连接组。
- **可扩展性**：基于层次图神经网络和骨架分解，可处理数十万神经元级别的数据。
- **融合结构-连接性**：通过结构嵌入作为连续描述符，避免了离散伙伴类型带来的信息损失。
- **坐标无关设计**：消除了空间位置引起的混淆，使表征更集中于连接组拓扑的本质。
- **多跳高阶分析**：能够发现超出局部连接的全局组织规律，如偏侧化。
- **注意力可解释**：提供了将宏观差异归因于具体突触伙伴的机制。

### 8. 不足与局限

- **实验覆盖有限**：仅基于FlyWire数据集，未在其他连接组（如小鼠、人类皮层）上验证泛化性。
- **缺乏与现有SSL方法对比**：未与GraphCL、SimGRACE、BGRL等主流图自监督方法比较，无法说明方法的相对优势。
- **算力需求未报告**：对训练效率、硬件资源无说明，限制了可复现性。
- **注意力分析可能粗糙**：注意力权重仅反映相关度，不能直接证明因果性。
- **依赖骨架分解质量**：精细骨架的提取可能受重建噪声影响，对下游任务敏感。
- **下游任务验证不充分**：虽提到标签高效推理，但未使用标准神经元类型基准数据集（如FlyWire中有ground truth类型标签），缺乏量化评估。
- **消融实验统计严谨性**：未说明是否进行了多次独立重复实验或统计检验，结果可靠性待加强。

（完）
