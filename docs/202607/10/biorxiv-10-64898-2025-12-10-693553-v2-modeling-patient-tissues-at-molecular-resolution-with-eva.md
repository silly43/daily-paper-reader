---
title: Modeling patient tissues at molecular resolution with Eva
title_zh: 利用Eva以分子分辨率建模患者组织
authors: "Liu, Y., Sharma, R., Bieniosek, M., Kang, A., Wu, E., Chou, P., Li, I., Rahim, M., Bauer, E., Ji, R., Duan, W., Qian, L., Luo, R., Sharma, P., Dhanasekaran, R., Schürch, C. M., Charville, G., Mayer, A., Zou, J., Trevino, A. E., Wu, Z."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.10.693553v2.full.pdf"
tags: ["query:ssl"]
score: 9.0
evidence: 在组织图像上使用掩码重建预训练，属于自监督视觉表征学习中的掩码自编码器方法
tldr: "组织结构与功能及稳态密切相关，其破坏通常指示疾病。Eva是一个针对组织成像数据的基础模型，采用新型视觉变换器架构，通过掩码重建在超4000万张空间蛋白质组学和组织病理学图像上预训练，学习分子、细胞和样本级别的多尺度空间表示。在H&E到蛋白质组学的跨模态推断、质量控制、数据注释、零样本检索、生存分析和患者分层等任务中表现优异。Eva有望通过桥接基础研究与临床实践来加速转化科学。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-10-693553-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1656, \"height\": 2278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-10-693553-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1648, \"height\": 2039, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-10-693553-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1654, \"height\": 1224, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-10-693553-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1564, \"height\": 2289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-10-693553-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1664, \"height\": 2403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2025-12-10-693553-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1575, \"height\": 2442, \"label\": \"Figure\"}]"
motivation: 现有方法难以从空间蛋白质组学等组织成像数据中提取有效信息，亟需统一的模型来建模结构-分子-临床关系。
method: 提出Eva基础模型，采用新颖的视觉变换器架构，在大规模配对空间蛋白质组学和组织病理学图像上通过掩码图像重建进行预训练。
result: Eva在跨模态推断、质量控制、数据注释、零样本检索、生存建模和患者分层等多项任务上均取得优异性能。
conclusion: Eva通过学习多尺度空间表示，有效桥接基础研究与临床实践，有望加速转化科学发展。
---

## 摘要
组织结构对所有器官的功能和稳态至关重要，结构破坏通常意味着疾病。建模组织结构、分子和临床方面之间的关系可以推动新的诊断和治疗策略。尽管空间蛋白质组学等分析技术能够捕捉这些关系，但从这些数据中提取洞察仍然具有挑战性。在此，我们提出Eva，一种用于组织成像数据的基础模型，可在分子、细胞和样本水平学习组织的多尺度空间表征。Eva采用新颖的视觉变换器架构，并在超过4000万张配对的H&E与空间蛋白质组图像上通过掩码重建进行预训练。我们展示了Eva在多种任务上的卓越表现，包括从H&E到蛋白质组染色的跨模态推理、质量控制、数据注释、零样本检索、生存建模和患者分层。在保留验证数据上的广泛评估证明了所学习嵌入的通用性和泛化能力。我们预期Eva将通过连接基础研究和临床实践来加速转化科学。

## Abstract
Tissue structure is essential to function and homeostasis in all organs, and disruptions to structure usually indicate disease. Modeling relationships between structural, molecular, and clinical aspects of tissues could advance new diagnostics and treatment strategies. Although profiling techniques like spatial proteomics can capture these relationships, the data remain challenging to extract insight from. Here, we present Eva, a foundation model for tissue imaging data that learns multi-scale spatial representations of tissues at the molecular, cellular, and sample level. Eva uses a novel vision transformer architecture and is pre-trained on masked reconstruction of over 40 million matched spatial proteomics and histopathology images. We show that Eva excels at a variety of tasks, including cross-modal inference from H&E to proteomics stains, quality control, data annotation, zero-shot retrieval, survival modeling, and patient stratification. Extensive evaluations on held-out validation data demonstrate the versatility and generalizability of the learned embeddings. We anticipate that Eva will accelerate translational science by bridging basic research and clinical practice.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 组织结构对器官功能和稳态至关重要，结构破坏通常指示疾病。空间蛋白质组学等分析技术能够捕获结构、分子和临床信息之间的关系，但数据维度高、异质性强，难以提取有效洞察。
- 现有基础模型主要面向常规组织病理学（H&E）图像，而对多通道、多标记的多重组织成像数据（如CODEX、MIBI、IMC）缺乏统一的表示学习框架。
- 论文提出Eva（Encoder of visual atlas），一个针对组织成像数据的基础模型，旨在学习分子、细胞和样本级别的多尺度空间表示，桥接基础研究与临床实践。

## 2. 论文提出的方法论

### 2.1 核心思想

- 采用掩码自编码器（Masked Autoencoder, MAE）架构，在大规模配对的空间蛋白质组学和H&E图像上进行自监督预训练，通过重建被掩码的图像区域来学习通用表示。
- 设计新颖的两阶段层次化Transformer架构，分别处理通道间协方差和空间关系。

### 2.2 关键技术细节

- **两阶段编码器-解码器框架**：
  - **第一阶段：通道级编码器（Channel-level Encoder）**：输入为 $C \times H \times W$ 的多通道图像，首先将每个通道的 $8\times8$ 块独立嵌入（共享卷积核），实现通道无关处理，以支持任意通道组合。然后使用多头部注意力在通道轴上整合信息，并引入基于GenePT的生物标记物语义嵌入（自然语言描述），增强生物先验。
  - **第二阶段：令牌级掩码自编码器（Token-level MAE）**：将通道编码器输出的聚合令牌与位置编码结合，通过标准ViT编码器学习空间关系。解码器由轻量ViT块组成，将压缩表示扩展到原始像素空间，完成图像重建。
- **训练目标**：最小化掩码位置上的均方误差（MSE）。
- **掩码策略**：训练时使用随机掩码（mask ratio 0.75），同时掩码不同通道和位置。推理时可使用令牌掩码（整令牌掩码）、通道掩码（整通道掩码）或H&E/MIF掩码，以评估不同重建能力。
- **跨模态预测**：通过微调Eva，可从H&E图像预测MIF图像（H&E→MIF翻译），即仅输入H&E和标记名称，模型预测标记通道强度。

### 2.3 算法流程（文字说明）

- 输入：多通道图像块 $X \in \mathbb{R}^{B \times C \times H \times W}$。
- 通道级编码：对每个单通道 $8\times8$ 块进行独立卷积嵌入→每个令牌生成通道聚合嵌入（含一个CLS令牌）→多头部注意力。
- 令牌级编码：将聚合令牌与位置编码相加，经ViT块输出令牌序列嵌入。
- 解码：扩展通道维度，加入生物标记嵌入和位置嵌入，经轻量ViT块还原为像素级输出 $\hat{X}$。
- 损失：$\mathcal{L}_{MSE} = \frac{1}{|V|} \sum_{i \in V} ||X_i - \hat{X}_i||^2$，其中$V$为掩码令牌集合。

## 3. 实验设计

### 3.1 数据集

- **训练集**：超过4,000个人类组织区域，多种器官（96%癌症），约1,100,000个224×224图像块（41.6 million单通道块）。平台分布：CODEX/Phenocycler 24%，PhenoCycler Fusion 64%，MIBI 1%，IMC 11%。66%有配对H&E。
- **验证集**：超过8,000个区域（71%完全未见于预训练），涵盖12个数据集，包括：
  - Stanford-GC、EM-Mixed、Stanford-GIST、Stanford-PC、MDACC-HCC、UKT-GEJ、UPMC-HNC、Stanford-CRC、MDACC-MM、RAHBT-DCIS、IUCPQ-LUAD、Stanford-HCC、UHB-CRC、DFCI-HNC、EM-PanCancerAtlas（EM-PCA）等。
  - 每个数据集包含细胞类型注释、微环境注释、临床标签（生存、免疫治疗反应、HPV状态等）。

### 3.2 任务与场景

1. **图像重建**（定性+定量）：随机掩码、令牌掩码、通道掩码重建，H&E→MIF和MIF→H&E翻译。
2. **质量评估**：NIQE分数预测、成像伪影检测、标记染色质量预测。
3. **细胞类型分类**（12个数据集，线性探测）。
4. **细胞标签迁移**（零样本/少样本从Stanford-GC到UKT-GEJ）。
5. **微环境分类**（UPMC-HNC、MDACC-HCC上的邻居分类）。
6. **细胞组成预测**（回归）。
7. **零样本补丁检索**（基于细胞组成相似性）。
8. **组织分类**（9种癌症类型、肺癌亚型）。
9. **生存分析**（UPMC-HNC、EM-PCA-CRC，Cox比例风险模型）。
10. **患者分层**（HPV状态、炎症水平、预后、免疫治疗响应等）。
11. **零样本病例检索**。

### 3.3 对比方法

- **VirTues**：IMC预训练的MAE模型（使用ESM蛋白质序列嵌入）。
- **KRONOS**：基于DINOv2的多重成像基础模型。
- **ROSIE**：H&E→MIF翻译专用模型（ConvNeXt）。
- **GigaTIME**：H&E→MIF翻译模型（UNet++）。
- **UNI**、**Prov-GigaPath**：病理学基础模型（H&E输入），用于对比病例级任务。
- 对比指标：AUC、F1、PCC、Spearman相关、MSE、C-index、SSIM等。

## 4. 资源与算力

- 训练在8×141 GB NVIDIA H200 GPU上进行，共20个epoch，batch size 16。
- 预训练参数：学习率 $10^{-4}$ 余弦退火至 $10^{-5}$。
- 下游任务在单个24 GB NVIDIA RTX 4090 GPU上完成。

## 5. 实验数量与充分性

- 论文进行了大量实验，涵盖10个以上的验证数据集，任务类型覆盖从像素级重建到临床级生存分析，层次完整（细胞、邻居、组织、患者）。
- 对每个任务均采用线性探测（固定主干），对比多个现有方法，并使用交叉验证（通常5折）或独立测试集。
- 进行了消隐性分析：不同掩码策略、不同分辨率、零样本/少样本设置。
- 实验设计较为充分：包括同模态和多模态任务，涵盖跨平台数据（CODEX、IMC、MIBI），并与SOTA模型在公平条件下对比。
- 不足：部分任务仅使用线性探测，未测试完全微调；对比的VirTues和KRONOS可能针对不同数据分布，但已尽量对齐设置。

## 6. 论文的主要结论与发现

- Eva在几乎所有下游任务上超越现有多重成像基础模型（平均AUC提高11.2%），且在H&E→MIF翻译中优于专门模型ROSIE和GigaTIME。
- Eva能够从H&E图像预测蛋白质组学染色，为低成本临床转化提供可能。
- 在自动细胞标注、微环境分类、生存分析、患者分层等任务上，Eva均取得最佳或顶尖性能，且能通过零样本/少样本泛化至新数据集。
- 将Eva的MIF嵌入与UNI/Prov-GigaPath的H&E嵌入进行后期融合，可进一步提升患者分层和生存建模性能。
- Eva学习到的注意力权重与生物学上合理的组织结构一致（如肿瘤区域与基质区域不同激活模式）。

## 7. 优点

- **新颖架构**：两阶段层次化Transformer支持任意通道组合，并利用语言模型生物先验，灵活高效。
- **大规模预训练**：>4,000组织区域，>40M单通道图像，覆盖多种组织和平台。
- **多尺度统一表征**：从像素到患者级别使用同一嵌入空间

## 8. 缺点与局限性

- **预训练数据偏向癌症组织**：96%的训练区域来自癌症样本，可能限制模型在正常组织或罕见病上的泛化能力，导致对良性样本的特征表示不够鲁棒。
- **线性探测评估的局限**：下游任务主要采用线性探测（固定编码器权重），未进行全模型微调的比较，可能未能充分展示Eva在特定任务上的潜力（但线性探测更公平地评估了表示质量）。
- **跨平台数据覆盖不均衡**：MIBI和IMC数据比例极低（合计12%），模型在这些平台的性能可能不如CODEX/Phenocycler（88%），且未在完整IMC或MIBI数据集上独立验证零样本能力。
- **计算资源需求较高**：预训练需要8×H200 GPU（141GB显存），对一般实验室或资源受限机构不友好，难以直接复现。
- **未明确处理批次效应**：多重成像数据常因实验批次产生通道强度偏移，论文未讨论是否在预训练或微调中引入归一化或对抗性批次消除技术。

## 9. 创新点

- **两阶段层次化Transformer架构**：首次将通道轴独立嵌入与空间MAE结合，支持任意通道组合，不依赖固定通道顺序或数量。
- **生物标记语义先验**：引入GenePT生成的标记名描述嵌入，使模型理解生物学含义而非仅像素统计，有助于跨标记泛化。
- **统一的多尺度表示框架**：同一模型编码器输出可直接用于细胞、邻居、组织、患者级任务，避免为不同粒度设计专用模型。
- **跨模态H&E→MIF翻译**：将空间蛋白质组学预测转化为H&E图像的辅助任务，拓展了临床转化路径（低成本H&E替代昂贵多重染色）。
- **大规模公开数据集建立**：收集并处理超过40M单通道图像块，为后续社区研究提供了基准训练资源。

## 10. 对相关行业/应用的启发

- **病理学基础模型开发**：启发社区关注多重成像数据的特有挑战（通道多样、标记不一致、跨平台异质），以及解决此类问题的模块化设计（如独立通道编码）。
- **临床诊断辅助**：通过H&E预测MIF，可减少对昂贵多重成像设备的需求，帮助基层医院获得空间蛋白质组学洞察，推动精准医疗公平化。
- **药物研发**：Eva可快速分析临床试验中的组织微环境（免疫细胞、结构变化），辅助疗效预测和患者分层。例如，在免疫治疗响应预测任务中，Eva隐式捕获了肿瘤-免疫的交互模式。
- **多模态融合**：论文展示的后期融合策略（MIF+TMA嵌入）优于单一模态，提示未来可在模型架构层面设计更紧密的跨模态交互。

## 11. 建议阅读人群与论文价值总结

- **建议阅读人群**：
  - 计算病理学、空间组学研究者（学习如何构建多通道成像基础模型）。
  - 临床转化科学家（关注H&E→MIF翻译及预后分层）。
  - 机器学习工程师（MAE适配多通道数据的技巧与消融实验设计）。

- **论文价值总结**：
  本篇论文提出了目前最全面的多重组织成像基础模型Eva，在细胞、微环境、组织、患者级别任务上均显著超越现有模型，并展示出强大的跨平台、跨数据集泛化能力。两阶段Transformer架构与生物标记语义嵌入的设计为后续研究提供了新范式。论文实验详实、对比充分，是计算病理学领域的重要贡献。

## 12. 关键术语与解释

- **MAE（Masked Autoencoder）**：自监督学习方法，随机遮盖输入图像的一部分，让模型通过剩余部分学习重建被遮盖内容，从而学习有效表示。
- **ViT（Vision Transformer）**：将图像分割成固定大小的块（令牌），用Transformer处理这些令牌的模型。
- **GenePT**：使用GPT模型处理基因/蛋白质标记名自然语言描述，得到嵌入向量，用于增强生物先验。
- **CODEX/MIBI/IMC**：三种常见的多重成像技术，通过标记多个蛋白质（性标记）在同一组织切片上获取高维空间信息。
- **线性探测**：固定预训练模型权重，仅训练一个线性分类器评估表示质量，用以验证模型所学特征的可分离性。
- **C-index（一致性指数）**：生存分析常用指标，衡量模型预测风险排序的准确度，0.5为随机，1为完全正确。
- **Biological Marker Embedding**：映射标记名称（如"CD3+"）到稠密向量的编码，可利用语言模型预训练知识。

## 13. 可能的后续研究方向

- **全模型微调评估**：在下游任务中全模型微调Eva，探究是否进一步提升性能，并设计参数高效微调（LoRA等）方法。
- **扩展到更多平台和标记方案**：当前预训练主要覆盖CODEX/Phenocycler，未来可加入MIBI、IMC、CyTOF等平台数据，并支持自定义标记列表。
- **基于Eva的生成模型**：结合扩散模型，利用Eva表示生成高保真多重成像图像，用于数据增强或反事实推理。
- **跨模态统一预训练**：将Eva与H&E基础模型（UNI等）联合训练，实现一码多用（即同一模型处理H&E和MIF）。
- **临床前瞻性验证**：在独立前瞻性队列中测试Eva的患者分层和生存预测能力，评估泛化性和临床应用价值。
- **可解释性增强**：利用注意力图、重建残差分析，为病理学家提供可视化解释，辅助生物标志物发现。

（完）
