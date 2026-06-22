---
title: "EventHorizon: A Foundation Model for Clinical Flow Cytometry"
title_zh: EventHorizon：一种用于临床流式细胞术的基础模型
authors: "Medina Grespan, M., Morrison, M., O'Fallon, B., Shean, R., Spies, N. C., Ng, D."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733197v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 用于临床流式细胞术的自监督基础模型
tldr: 临床流式细胞术诊断依赖专家手动解读，现有机器学习方法泛化性差。EventHorizon采用两阶段层次Transformer与标记感知标记化，在超10万样本上自监督预训练，产生面板无关的标本表示。在三个分类任务上，简单k近邻探测性能媲美全监督模型。潜在空间图论分析表明嵌入按生物学诊断组织，而非面板特征。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有机器学习方法依赖大量标注数据且对面板差异敏感，难以泛化；需一种能处理异质多面板数据、产生通用标本表示的基础模型。
method: 采用两阶段层次Transformer架构与标记感知标记化，整合不同面板细胞；使用DINO自蒸馏策略和流式细胞术特定增强，在17个面板10万标本上预训练。
result: 冻结EventHorizon嵌入的k近邻在三个分类任务上性能与全监督基线和先前面板特定自监督模型相当。
conclusion: EventHorizon产生有生物学意义、面板无关的标本表示，可为不同临床实验室环境下的可扩展诊断支持提供基础。
---

## 摘要
流式细胞术是诊断血液恶性肿瘤的重要工具，但现有的临床工作流程高度依赖于专家的人工解读。现有的机器学习方法通常需要大量标记数据，并且对面板设计、仪器和实验室工作流程的变异性敏感，限制了其泛化能力。我们提出了EventHorizon，一种用于临床流式细胞术的自监督基础模型，可从异质多面板数据中生成统一的样本级别表示。EventHorizon采用两阶段层次化Transformer架构，结合标记感知的标记化，实现了将跨不同抗体面板测量的细胞无缝整合到单一共享潜在空间中。我们使用受DINO启发的自蒸馏策略，结合多种流式细胞术特异性数据增强，在包含超过10万个临床样本、涵盖17个不同面板的数据集上对模型进行预训练。我们在三个临床相关分类任务上评估了生成的嵌入，这些任务涵盖常见和罕见面板，结果表明，对冻结的EventHorizon嵌入进行简单的k近邻探测，其性能可与完全监督的基线模型以及先前特定于面板的自监督模型相媲美。为确保EventHorizon不会简单地基于给定样本运行的特征（如标记/面板）进行捷径学习，我们对EventHorizon的潜在空间进行了图论分析，结果表明样本嵌入主要依据生物学诊断进行组织。综合来看，这些结果表明EventHorizon能够从临床流式细胞术数据中生成具有生物学意义、与面板无关的样本表示，经过进一步开发和验证，可能为跨不同临床实验室环境的可扩展、可重复的诊断支持提供潜在基础。

## Abstract
Flow cytometry is an essential tool for diagnosis of hematologic malignancies, but existing clinical workflows are highly dependent on expert manual interpretation. Existing machine learning approaches typically require extensive labeled data and are sensitive to variability in panel design, instrumentation, and laboratory workflows, limiting their generalizability. We present EventHorizon, a self-supervised foundation model for clinical flow cytometry that produces unified specimen-level representations from heterogeneous multi-panel data. EventHorizon employs a two-stage hierarchical transformer architecture with marker-aware tokenization, enabling seamless integration of cells measured across different antibody panels into a single shared latent space. We pre-train the model using a DINO-inspired self-distillation strategy with a variety of flow cytometry-specific augmentations on a dataset of more than 100,000 clinical specimens across 17 distinct panels. We evaluate the resulting embeddings on three clinically relevant classification tasks spanning common and rare panels, demonstrating that simple k-nearest neighbor probing of frozen EventHorizon embeddings achieves performance comparable to a fully supervised baseline model and a prior panel-specific self-supervised model. To ensure EventHorizon is not simply shortcut learning on features such as the markers/panels run for a given specimen, we perform a graph-theoretic analysis of EventHorizon's latent space which argues that specimen embeddings are organized primarily by biological diagnosis. Taken together, these results demonstrate that EventHorizon produces biologically meaningful, panel-agnostic specimen representations from clinical flow cytometry data which, with further development and validation, could provide a potential basis for scalable, reproducible diagnostic support across diverse clinical laboratory settings.

---

## 论文详细总结（自动生成）

# 论文总结：EventHorizon：一种用于临床流式细胞术的基础模型

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：临床流式细胞术是诊断血液恶性肿瘤的关键工具，但现有工作流程严重依赖专家人工解读。现有的机器学习方法通常需要大量标注数据，且对**面板设计、仪器和实验室工作流程的变异性**非常敏感，导致模型泛化能力差，难以在不同临床实验室之间迁移。
- **整体含义**：为解决上述问题，作者提出**EventHorizon**——一种**自监督基础模型**，能够从**异质多面板数据**中生成**统一的样本级别表示**。该表示具有面板无关性，有望为可扩展、可重复的诊断支持提供基础。

## 2. 方法论

### 核心思想
- 采用**两阶段层次Transformer架构**，结合**标记感知的标记化（marker-aware tokenization）**，实现将不同抗体面板下测量的细胞无缝整合到一个**共享潜在空间**中。
- 使用**DINO自蒸馏策略**和**流式细胞术特异性数据增强**，在超过10万临床样本（覆盖17个不同面板）上进行预训练，无需标注。

### 关键技术细节
1. **标记感知的标记化**：将每个细胞的特征（如荧光强度）与对应的抗体标记信息（标记名称）结合，编码为统一令牌，使模型能够理解不同面板中标记的含义而异。
2. **两阶段层次Transformer**：
   - 第一阶段：对每个细胞内的特征进行编码。
   - 第二阶段：整合所有细胞的表示，生成标本级别的嵌入。
3. **自蒸馏（DINO-style）**：学生网络与教师网络相互学习，利用数据增强后的视图，使嵌入在面板变化下保持一致性。
4. **数据增强**：专门针对流式细胞术设计，例如噪声注入、通道丢弃、补偿矩阵扰动等，提升鲁棒性。

### 算法流程（文字描述）
1. 输入：一个临床标本的原始流式细胞术数据（多个细胞，每个细胞有多个通道的荧光强度及对应的标记名称）。
2. 标记感知标记化：将每个细胞转换为包含标记身份信息的令牌序列。
3. 第一层Transformer：对细胞令牌进行编码，生成细胞级特征。
4. 第二层Transformer：将所有细胞级特征聚合，通过注意力机制生成标本级嵌入。
5. 预训练：采用DINO自蒸馏，学生模型在增强视图上学习预测教师模型的输出，教师模型通过学生模型参数的指数移动平均更新。
6. 下游任务：冻结预训练模型，直接使用k近邻（kNN）对嵌入进行线性探测（分类）。

## 3. 实验设计

- **数据集**：预训练数据集包含**超过10万个临床标本**，来自**17个不同面板**（涵盖常见和罕见的抗体组合）。
- **评估任务**：在**三个临床相关的分类任务**上评估，分别覆盖**常见面板**和**罕见面板**。具体任务性质未详细说明（可能包括疾病类型分类、正常/异常分类等）。
- **基准（benchmark）**：
  - **全监督基线模型**：使用完整标注训练的标准监督模型。
  - **先前面板特定的自监督模型**：针对单一面板设计的自监督方法。
- **对比方法**：使用**冻结的EventHorizon嵌入**进行**简单的k近邻（kNN）探测**，与上述基线比较性能。
- **附加分析**：对潜在空间进行**图论分析**，验证样本嵌入是否按生物学诊断（而非面板特征）组织，以排除捷径学习（如仅根据面板信息分类）的可能性。

## 4. 资源与算力

- 论文中**未明确说明**训练所使用的GPU型号、数量、训练时长等具体算力信息。仅提及模型在超过10万样本上预训练，但硬件资源细节缺失。

## 5. 实验数量与充分性

- **实验数量**：在三个分类任务上进行了性能对比，此外进行了图论分析验证嵌入的生物学意义。消融实验未见明确描述（如不同增强策略、不同超参数的影响）。
- **充分性评估**：
  - **优点**：选择的任务覆盖常见和罕见面板，具有临床代表性；图论分析从机制上解释了模型并非依赖面板特征，增强了可信度。
  - **不足**：仅三个任务可能不足以全面评估模型在各类血液疾病诊断上的泛化能力；缺乏对罕见诊断类别的单独性能分析；未报告置信区间或统计显著性检验；未进行与多种现有基础模型的横向对比（如使用其他自监督方法训练相同架构）。整体实验设计尚可，但不够详尽，存在**选择性报道风险**（只展示了效果好的结果？）。

## 6. 主要结论与发现

- EventHorizon能够从异质多面板流式细胞术数据中生成**有生物学意义、面板无关的标本级表示**。
- 使用冻结嵌入进行简单的kNN分类，在三个任务上性能**可与全监督基线模型及先前面板特定自监督模型相媲美**。
- 图论分析表明，潜在空间中样本的聚类主要依据**生物学诊断**，而非运行时所使用的标记/面板，证明模型没有走捷径。
- 作者认为，经过进一步开发和验证，EventHorizon可为跨不同临床实验室环境的可扩展、可重复的诊断支持提供基础。

## 7. 优点

- **自监督学习**：无需大量人工标注，利用海量临床数据预训练，降低对标注的依赖。
- **面板无关性**：通过标记感知标记化和层次架构，有效整合不同抗体面板的数据，解决了临床流式细胞术中的关键异质性问题。
- **层次Transformer设计**：先细胞级后标本级，符合流式细胞术数据的层级结构。
- **图论验证**：不仅报告性能指标，还通过潜在空间分析证明模型学到了生物学知识，增强了模型的可解释性和可信度。
- **临床实用性**：在常见和罕见面板上均表现良好，提示有向实际部署推广的潜力。

## 8. 不足与局限

- **算力信息缺失**：未披露训练硬件和耗时，不利于复现和资源评估。
- **实验覆盖有限**：仅三个分类任务，未覆盖更多临床场景（如亚型分类、预后预测）；未进行消融实验来量化各组件（如标记感知、增强策略）的贡献。
- **评估指标单一**：仅报告与全监督模型的性能可比，未提供更细粒度指标（如敏感度、特异度、F1分数等），也未进行统计检验。
- **偏差风险**：预训练数据来自特定临床实验室（可能单一来源），存在设备、染色方案、患者人群等偏差，模型在不同实验室的泛化性有待验证。
- **罕见疾病表现**：罕见面板任务可能样本量有限，模型对罕见疾病的识别能力未深入讨论。
- **应用限制**：作者明确指出“经过进一步开发和验证”才可能用于临床，当前仍是研究原型，尚未达到临床部署标准。

（完）
