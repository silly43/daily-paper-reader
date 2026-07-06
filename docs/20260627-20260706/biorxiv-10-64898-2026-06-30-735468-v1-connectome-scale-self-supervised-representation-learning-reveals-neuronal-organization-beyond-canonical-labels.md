---
title: Connectome-scale self-supervised representation learning reveals neuronal organization beyond canonical labels
title_zh: 连接组尺度的自监督表示学习揭示超越经典标签的神经元组织
authors: "Shi, T., Chen, Y., Liu, C., Zhang, R."
date: 2026-07-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.30.735468v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 使用对比学习进行连接组自监督表示学习
tldr: 密集电子显微镜连接组提供突触级分辨率，但整合结构与连接的可扩展表示学习困难。本文提出自监督框架，利用层级图神经网络和骨架分解进行对比学习，并引入坐标无关拓扑减少发育和几何混淆。细骨架保留更丰富身份信息，结构-连接性联合表征改善亚型判别，迭代多跳学习揭示半球侧化和连接定义亚组。该框架无需预设标签即可自动发现神经元组织，为大规模连接组分析提供新路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以在密集连接组中无监督地学习整合神经元结构和突触连接的可扩展表示。
method: 采用层级图神经网络结合骨架分解进行对比学习，利用坐标无关拓扑和结构嵌入构建连接性表征。
result: 细骨架保留更丰富身份信息，坐标无关拓扑改善聚类；结构-连接性表征提升亚型判别，多跳学习发现半球侧化与连接亚组。
conclusion: 建立自监督框架，无需预设标签即可自动发现神经元身份与连接组组织，适用于大规模密集连接组。
---

## 摘要
密集电子显微镜连接组提供了神经元结构和连接的突触分辨率图谱，但学习能够整合结构和连接性、以最少人工干预进行连接组发现的可扩展表示仍然困难。本文提出了一个用于密集连接组中结构-连接性表示学习的自监督框架。具有骨架分解的层次图神经网络能够对精细采样的FlyWire神经元骨架进行对比学习，表明精细骨架比粗糙表示保留了更丰富的身份信息。无坐标拓扑减少了发育和几何混淆，改进了聚类和标签高效推理。然后，我们使用学习到的结构嵌入作为突触伙伴的连续描述符来构建结构驱动的连接性表示，无需预定义的伙伴类型标签即可改善亚型区分。迭代的多跳学习进一步揭示了高阶组织，包括半球连接侧化和连接性定义的亚群。注意力分析将这些差异与特定的突触伙伴联系起来。总之，这些结果建立了一个自监督且可扩展的框架，用于在大规模密集连接组中发现神经元身份和连接组组织。

## Abstract
Dense electron-microscopy connectomes provide synaptic-resolution maps of neuronal structure and wiring, but learning scalable representations that integrate structure and connectivity for connectome discovery with minimal human intervention remains difficult. Here we present a self-supervised framework for structure-connectivity representation learning in dense connectomes. A hierarchical graph neural network with skeleton decomposition enables contrastive learning from finely sampled FlyWire neuronal skeletons, showing that fine skeletons preserve substantially richer identity information than coarse representations. Coordinate-free topology reduces developmental and geometric confounds, improving clustering and label-efficient inference. We then use learned structural embeddings as continuous descriptors of synaptic partners to construct structure-driven connectivity representations, improving subtype discrimination without predefined partner-type labels. Iterative multi-hop learning further reveals higher-order organization, including hemispheric connectivity lateralization and connectivity-defined subgroups. Attention analysis links these differences to specific synaptic partners. Together, these results establish a self-supervised and scalable framework for discovering neuronal identity and connectome organization in a large-scale dense connectome.

---

## 论文详细总结（自动生成）

# 论文总结：Connectome-scale self-supervised representation learning reveals neuronal organization beyond canonical labels

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：密集电子显微镜（EM）连接组提供了突触分辨率级别的神经元结构与连接图谱，但如何从这种大规模、高维数据中学习可扩展的表示，以整合结构信息和突触连接性，并在最少人工干预下自动发现神经元组织，仍然是一个重大挑战。传统方法依赖人工定义的标签或先验分类，难以捕捉超越经典标签的细粒度组织模式。
- **整体含义**：本文旨在建立一个自监督的表示学习框架，无需预设标签即可自动从密集连接组中提取神经元身份和连接组组织，为大规模、无偏的神经科学发现提供新路径。

## 2. 方法论

- **核心思想**：利用自监督对比学习，结合层级图神经网络（Hierarchical GNN）和骨架分解（Skeleton Decomposition），学习神经元结构嵌入；再以结构嵌入作为连续描述符构建结构驱动的连接性表示；通过迭代多跳学习发现高阶组织。
- **关键技术细节**：
  - **骨架分解与层级GNN**：对FlyWire神经元的精细骨架进行分层图神经网络建模，在多个层级上进行对比学习。精细骨架比粗糙表示保留了更丰富的身份信息。
  - **坐标无关拓扑**：去除坐标依赖（如空间位置），仅利用拓扑结构信息，减少发育和几何混淆，改善聚类和标签高效推理。
  - **结构驱动的连接性表示**：将学习到的结构嵌入作为突触伙伴的连续描述符，替代预定义的伙伴类型标签，构建连接性表示，提升亚型判别能力。
  - **迭代多跳学习**：通过多步传播（多跳）学习高阶组织，揭示半球连接侧化（hemispheric connectivity lateralization）和连接性定义的亚组。
  - **注意力分析**：使用注意力机制将发现的差异与特定的突触伙伴联系起来。

- **公式/算法流程**（文字说明）：
  1. 输入：采样自FlyWire数据集的精细神经元骨架图。
  2. 层级GNN编码：对不同尺度的骨架子图进行图卷积，得到多尺度结构嵌入。
  3. 对比学习：以正负样本对（同一神经元不同尺度/扰动 vs 不同神经元）进行对比损失优化。
  4. 坐标无关拓扑转换：对结构嵌入进行坐标无关化处理。
  5. 连接性构建：将每个神经元的结构嵌入作为其突触伙伴的连续描述符，聚合得到结构驱动的连接性嵌入。
  6. 迭代多跳：将连接性嵌入作为新的节点特征，重复图传播和对比学习。
  7. 聚类与注意力分析：对最终嵌入进行聚类，并利用注意力权重识别关键伙伴。

## 3. 实验设计

- **数据集**：使用了FlyWire密集EM连接组数据集（果蝇半脑连接组），具体为神经元的精细骨架和突触连接。
- **Benchmark**：由于该框架是无监督/自监督的，没有直接对比传统监督方法。但通过聚类质量、亚型判别能力、标签高效推理（少量标注下分类准确率）等指标评估表示的有效性。
- **对比方法**：
  - 不同骨架粒度：精细骨架 vs 粗糙骨架。
  - 有无坐标无关拓扑：使用坐标信息 vs 去除坐标后的纯拓扑。
  - 结构嵌入 vs 结构+连接性联合嵌入。
  - 单跳 vs 多跳学习。
  - （可能还对比了其他无监督图表示学习方法，如GraphSAGE、GCN+对比学习等，但文中未明确列出。）

## 4. 资源与算力

- 论文中**未明确说明**使用了多少GPU型号、数量和训练时长。仅从方法推测需要一定的算力（FlyWire数据集规模大，使用层级GNN和对比学习），但具体资源消耗未给出。

## 5. 实验数量与充分性

- **实验数量**：文中提及了多个比较维度（骨架粒度、坐标信息、结构vs联合、单跳vs多跳、注意力分析等），形成了一组消融实验和有效性验证。具体实验组数未列出数字，但覆盖了关键设计选择。
- **充分性与客观性**：实验设计较为系统，消融实验揭示了各组件的作用（如精细骨架保留更丰富信息、坐标无关改善聚类、联合表示提升亚型区分）。结果客观，无主观偏差。但缺少与其他现有无监督连接组表示方法的直接定量对比（如是否在标准聚类指标上超越已有工作），这是一个不足。此外，仅使用一个数据集（FlyWire），泛化性未验证。

## 6. 主要结论与发现

- 精细骨架比粗糙骨架保留了更丰富的神经元身份信息。
- 坐标无关拓扑显著减少了发育和几何混淆，改善了聚类和标签高效推理。
- 结构-连接性联合表示优于仅用结构表示，无需预定义伙伴类型即可提升亚型判别。
- 迭代多跳学习能够发现高阶组织：半球连接侧化（左右半球在连接模式上的不对称）和连接性定义的亚组。
- 注意力分析将半球差异和亚组差异与特定的突触伙伴关联起来。

## 7. 优点

- **自监督、免标签**：无需人工标注，可扩展到大规模密集连接组，降低了对先验知识的依赖。
- **结构-连接融合**：通过结构嵌入作为连续描述符，巧妙的连接了结构相似性和功能连接性。
- **坐标无关的鲁棒性**：去除空间位置干扰，聚焦于纯粹的网络拓扑，使表示更通用。
- **多尺度与多跳**：层级骨架分解捕捉局部细节，迭代多跳学习捕捉全局组织，层次丰富。
- **可解释性**：注意力分析提供了生物学上可解释的差异来源。

## 8. 不足与局限

- **实验覆盖不足**：仅在FlyWire单一数据集上验证，未在其他物种或脑区连接组上测试，泛化性存疑。
- **缺乏基准比较**：未与现有无监督图表示学习或连接组分析方法（如vGraph、GCCA、t-SNE+聚类等）进行量化对比，难以评估绝对增益。
- **算力与可扩展性**：未报告训练资源，如果模型复杂度高，可能限制对更大规模连接组的应用。
- **对骨架质量的依赖**：框架输入为神经元骨架，若骨架采样或重建有噪声，可能影响表示质量。
- **生物学验证有限**：发现的半球侧化和亚组未与已知细胞类型或功能实验关联，可能只是统计模式。

（完）
