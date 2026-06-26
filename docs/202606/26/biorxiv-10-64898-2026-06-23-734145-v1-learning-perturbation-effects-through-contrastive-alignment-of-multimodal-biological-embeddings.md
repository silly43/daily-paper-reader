---
title: Learning Perturbation Effects Through Contrastive Alignment of Multimodal Biological Embeddings
title_zh: 通过多模态生物嵌入的对比对齐学习扰动效应
authors: "Long, W., Liu, T., Szalata, A., Theis, F. J., Xue, L., Zhao, H."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.23.734145v1.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: CLIP风格的对比对齐多模态生物嵌入预测扰动效应
tldr: 现有方法多针对单一扰动模态，且未利用外部语义知识，泛化能力有限。本文提出PertOmni，采用CLIP风格对比学习，对齐转录组扰动特征与基因/化合物文本嵌入及细胞图像嵌入，并通过掩码对比目标增强细胞类型内判别性、消除异质性干扰。在双向检索、药物-基因互作预测和两种扰动类型预测任务上，PertOmni均显著优于基线方法，展示了多模态对齐在扰动效应学习中的有效性。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有扰动表示学习方法模态单一、缺乏语义知识，难以跨数据集和扰动类型泛化。
method: 基于CLIP框架，联合训练共享转录组编码器和数据集特定文本/图像编码器，使用掩码对比损失强化细胞类型内对齐。
result: 在双向检索、药物-基因互作推断和CRISPRi/小分子扰动预测上均取得超越基线的性能提升。
conclusion: PertOmni通过多模态对比对齐有效学习扰动效应，具有良好的跨模态泛化能力。
---

## 摘要
多模态单细胞扰动筛选为表征基因和化学干预对细胞状态的影响提供了一种可扩展的方法。然而，现有的大多数表示学习方法仅针对单一扰动模态设计，未能明确纳入外部语义知识，这限制了它们在数据集和扰动类型之间的泛化能力。在此，我们提出PertOmni，一种CLIP风格的多模态表示学习框架，它将转录组扰动特征与精心策划的基因和化合物描述的文本嵌入以及细胞绘画的图像嵌入对齐。PertOmni联合训练一个共享的转录组编码器和特定数据集的文本编码器，采用掩码对比目标，强调细胞类型内的区分，同时减轻细胞类型异质性带来的混杂效应。我们在双向检索、药物-基因相互作用推断以及小分子和CRISPRi扰动数据集的扰动预测上评估了生成的联合嵌入空间，并展示了相较于强基线方法的一致改进。

## Abstract
Multimodal single cell perturbation screens offer a scalable approach for characterizing the effects of genetic and chemical interventions on cellular state. However, most existing representation learning methods are tailored to a single perturbation modality and fail to explicitly incorporate external semantic knowledge, which limits their ability to generalize across datasets and perturbation types. Here, we introduce PertOmni, a CLIP style multimodal representation learning framework that aligns transcriptomic perturbation signatures with text derived embeddings of curated genes and compound descriptions, as well as image derived embeddings from cell paintings. PertOmni jointly trains a shared transcriptomic encoder and dataset specific text encoders using a masked contrastive objective that emphasizes within cell type discrimination while mitigating confounding effects arising from cell type heterogeneity. We evaluate the produced joint embedding space on bidirectional retrieval, drug gene interaction inference, and perturbation prediction across both small molecule and CRISPRi perturbation datasets, and demonstrate consistent improvements over strong baseline methods.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：单细胞扰动实验（如 CRISPR、小分子处理）能系统量化细胞对干预的响应，但现有表示学习方法大多针对单一扰动模态，未显式利用外部语义知识（如基因功能注释、化合物描述），导致跨数据集和跨扰动类型的泛化能力有限。同时，缺乏统一框架来整合转录组、文本描述和细胞图像等多种模态的扰动效应。
- **整体含义**：本文旨在构建一个多模态对比学习框架，通过学习一个共享嵌入空间，将不同来源的扰动效应（转录组特征、文本语义、图像形态）对齐，从而提升扰动表示的可迁移性和解释性，并支持多种下游应用，如药物-基因相互作用预测和扰动响应预测。

## 2. 方法论

- **核心思想**：借鉴 CLIP (Contrastive Language-Image Pre-training) 框架，通过对比学习将配对的多模态数据（转录组扰动特征 ↔ 文本描述嵌入，或图像嵌入 ↔ 文本描述嵌入）拉近，同时推远非配对样本。关键创新在于引入**掩码对比目标 (masked contrastive objective)**：只允许同一细胞系内的样本构成正/负对，跨细胞系的样本被掩码（损失贡献为零），从而强制模型学习细胞系内扰动间的细微差异，避免被细胞系整体的差异所干扰。
- **关键技术细节**：
  - **编码器架构**：共享的转录组编码器 $P_X$ 和数据集特定的文本编码器（化学 $P_Z^d$、遗传 $P_Z^g$）。所有编码器为轻量级两层 MLP（线性层→GELU→线性层+残差连接+LayerNorm），输出 128 维向量。
  - **文本嵌入生成**：使用固定 LLM（`text-embedding-3-small`）对基因描述（GenePT）、化合物描述（MedChemExpress 或 GPT-4o 生成）、细胞系描述（GPT-4o 生成）提取 1536 维向量，并拼接作为文本编码器输入。对遗传扰动还额外拼接目标基因的 GO 生物通路描述（MSigDB）。
  - **图像嵌入**：对 Cell Painting 图像（5 通道），使用预训练 DINOv2 提取各通道 1536 维嵌入，通过三种聚合策略（Concat、ProjMean、Mean）得到图像级表示。
  - **损失函数**：采用 SigLIP 形式的 sigmoid 交叉熵损失：
    $$L_{mCLIP} = -\frac{1}{n}\sum_{i,j} \log\sigma(Y_{ij} \cdot \langle E_i, T_j \rangle / t) - \frac{1}{m}\sum_{i',j'} \log\sigma(Y_{i'j'}' \cdot \langle E_{i'}', M_{j'} \rangle / t)$$
    其中 $Y_{ij}$ 为掩码标签：正对为 $+1$，同细胞系内负对为 $-1$，跨细胞系为 $0$。温度 $t=5$。
  - **训练流程**：联合训练化学和遗传两个小批次，共享转录组编码器和文本编码器最后一层线性层。使用 Adam 优化器，学习率 $1\times10^{-4}$，batch size 128，默认 100 epochs，early stopping 基于 top-1 检索准确率。

## 3. 实验设计

- **数据集**：
  - **转录组-文本对齐**：小分子扰动使用 **Tahoe-100M**（14 plates，380 种化合物，50 个细胞系）；遗传扰动使用合并的 **CRISPRi 数据集**（K562、RPE1、HepG2、Jurkat、HCT116，共 18385 个扰动）。
  - **图像-文本对齐**：**RxRx3-core** 数据集（HUVEC 细胞，736 个基因扰动、1,674 个化合物扰动，共 222,601 张图像）。
  - **药物-基因相互作用**：**DGIdb** 数据库。
- **基准方法**：
  - **转录组-文本检索**：scGPT、PaSCient、随机匹配、One-hot 嵌入。
  - **图像-文本检索**：CellCLIP（预训练及微调版本）。
  - **药物-基因交互预测**：基于 Vision Scores 的余弦相似度、SNN 分类器（文本/转录组/文本+转录组嵌入）。
  - **扰动预测**：LangPert、GenePert、STRING GNN、非控制均值基线、kNN 聚合（文本或转录组嵌入）。
- **评价指标**：检索任务使用 ACC@K、nDCG@K、MRR 及聚合平均分；药物-基因交互使用 AUROC、AUPRC；扰动预测使用预测与真实表达向量之间的 Pearson 相关系数（所有基因或 top-20 DEGs）。

## 4. 资源与算力

- 论文在附录 A 中列出了训练超参数，**未明确说明 GPU 型号、数量及总训练时长**。
- 补充表 4 给出了单次运行的**计算时间（秒）**（使用 8 CPUs + 1 NVIDIA RTX 5000 GPU）：
  - PertOmni-chem: 2006.02 s (约 0.56 h)
  - PertOmni-cri: 796.85 s (约 0.22 h)
  - PertOmni (联合训练): 2576.25 s (约 0.72 h)
  - 对应的基线方法如 scGPT 训练时间略短，但性能较低。

## 5. 实验数量与充分性

- **实验数量**：论文报告了四大类核心实验（双向转录组-文本检索、图像-文本检索、药物-基因交互预测、扰动预测），并在此基础上进行了多组消融实验（超参数敏感性、编码器结构、损失函数、温度、学习率、最小 epochs、文本/图像嵌入方式等）。每个实验均在多个数据集或设置下重复。
- **充分性**：实验覆盖了不同扰动类型（化学与遗传）、不同模态（转录组、文本、图像）及多种下游任务。基准方法选择全面且大多为强基线。消融实验系统，展示了关键组件（如掩码对比、联合训练、微调）的必要性。统计比较使用箱线图、气泡图、表格，且报告了均值和标准差。
- **公平性**：训练/验证/测试集按扰动而非细胞划分，确保测试扰动完全未见；药物-基因交互任务采用正-未标注 (positive-unlabeled) 设置并保持药物/基因在训练/测试中不重叠。评估指标标准化。整体设计客观、公平。

## 6. 主要结论与发现

- PertOmni 在**所有下游任务上一致超越强基线方法**：
  - **药物-基因交互预测**：微调后的 PertOmni_ft+text 在 Drug2Gene 和 Gene2Drug 任务中取得最高 AUROC 和 AUPRC，显著优于基于 Vision Scores 或 SNN 的方法（图 2）。
  - **扰动预测**：kNN 聚合 PertOmni 文本嵌入在 RPE1、HepG2、Jurkat 三个细胞系上的 Pearson 相关性均高于 GenePert、STRING GNN、LangPert 及非控制均值基线；且 PertOmni 筛选的基因集可提升 LangPert 性能（PertOmni+refined LangPert）（图 3）。
  - **转录组-文本检索**：PertOmni 在 Tahoe 和 CRISPR 数据集上多数指标排名第一或接近第一（图 4）。联合训练显著改善 CRISPR 检索，但对 Tahoe 检索略有下降，推测与数据量不平衡有关。
  - **图像-文本检索**：三种 PertOmni 变体在 RxRx3-core 化合物和基因扰动上均优于 CellCLIP 及微调版本，其中 Concat_PertOmni（保留通道独立性）性能最佳（图 5）。
- 掩码对比学习（仅同细胞系内对比）有效避免模型通过细胞系身份作为捷径，增强了同细胞系内扰动的鉴别力。
- 消融实验（补充图 1-14）验证了关键设计（如文本嵌入拼接顺序、可训练控制嵌入、损失函数、超参数）的合理性。

## 7. 优点

- **多模态统一框架**：首次系统性地对齐转录组、文本和图像三种模态的扰动效应，跨模态泛化能力强。
- **利用外部语义知识**：引入 LLM 生成的基因/化合物/细胞系描述和 GO 通路知识，增强了嵌入的生物学可解释性。
- **掩码对比设计**：巧妙通过细胞系内对比消除了细胞异质性带来的混杂，同时不强制要求扰动效应在细胞系间不变，更符合生物学现实。
- **覆盖多种下游应用**：不仅实现了跨模态检索，还能直接用于药物靶点发现和扰动响应预测，实用价值高。
- **实验全面且代码开源**：在多个数据集、多种扰动类型上验证，并有充分的消融分析，可复现性良好。

## 8. 不足与局限

- **对 LLM 的依赖**：PertOmni 的性能与所采用 LLM（`text-embedding-3-small`）嵌入能力强相关，随着 LLM 迭代需不断更新模型。
- **模态覆盖不完整**：仅整合了转录组、文本和图像，未包含蛋白质组、代谢组等其他功能模态，因数据可及性限制。
- **数据不平衡问题**：联合训练时 CRISPR 数据量远大于 Tahoe，导致检索性能在化学端略有下降；作者虽提及需重加权或平衡批处理，但未在当前版本实现。
- **药物-基因注释稀疏性**：DGIdb 注释不完备，将未注释对视为负例可能低估模型实际能力；任务评估更接近正-未标注设定，但 AUPRC 仍受限于正样本率。
- **计算资源需求**：虽然单次训练时间不长，但调参和多种消融实验累计仍需一定 GPU 算力。
- **仅考虑细胞类型级伪批量表达**：未采用单细胞级预测，可能丢失细胞异质性信息；且未评估 batch 效应消除能力。

（完）
