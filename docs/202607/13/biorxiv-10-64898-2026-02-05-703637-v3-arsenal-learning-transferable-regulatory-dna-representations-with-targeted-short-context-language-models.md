---
title: "ARSENAL: Learning Transferable Regulatory DNA Representations with Targeted Short-Context Language Models"
title_zh: ARSENAL：利用靶向短上下文语言模型学习可迁移的调控DNA表示
authors: "Patel, A., Kundaje, A."
date: 2026-07-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.05.703637v3.full.pdf"
tags: ["query:ssl"]
score: 8.0
evidence: 基于调控元件的掩码DNA语言模型预训练
tldr: 调控DNA区域功能元件稀疏且依赖短转录因子基序语法，现有全基因组长上下文DNA语言模型难以有效捕获这些特征。ARSENAL是一种短上下文掩码语言模型，仅在ENCODE候选顺式调控元件上预训练，避免了大规模全基因组训练。该模型能从头恢复多种转录因子基序，在零样本调控变异效应预测中超越其他基础模型，并提升染色质可及性和调控变异评分的监督模型性能。此外，ARSENAL可作为高效生成先验，实现多目标调控序列设计。结果表明，针对调控区域的靶向自监督预训练足以学习可迁移的生物学表示，无需长上下文或任务标签。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1436, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1437, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 670, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 672, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1056, \"height\": 803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 893, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1570, \"height\": 1198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1593, \"height\": 455, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-02-05-703637-v3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 741, \"label\": \"Table\"}]"
motivation: 调控DNA功能元件稀疏且依赖短基序语法，现有全基因组长上下文语言模型难以捕获其表示。
method: 在ENCODE候选顺式调控元件上预训练短上下文掩码DNA语言模型，学习局部调控模式。
result: 模型恢复多种转录因子基序，零样本调控变异预测优于其他基础模型，并改善下游监督任务性能。
conclusion: 靶向自监督预训练可学习生物有意义的可迁移调控表示，无需全基因组规模训练或长上下文。
---

## 摘要
DNA语言模型旨在学习基因组序列的表示，用于变异解读、调控预测和序列设计。大多数DNA语言模型是在全基因组和长上下文上训练的，但调控DNA提出了一个独特的挑战：功能元件稀疏、依赖于上下文，并由嵌入在大段背景序列中的短转录因子基序语法编码。我们引入了ARSENAL，一个在ENCODE候选顺式调控元件上预训练的短上下文掩码DNA语言模型。ARSENAL能够从头恢复多种转录因子基序，并相对于其他DNA语言模型基础模型改进了零样本调控变异效应预测。ARSENAL嵌入还改进了监督调控序列模型在预测染色质可及性和调控变异评分方面的性能。最后，ARSENAL作为一种高效的生成先验，能够通过监督预言机实现多目标调控序列设计。ARSENAL表明，在调控区域上进行靶向自监督预训练可以在没有基因组规模训练、长上下文或任务特定标签的情况下学习到具有生物学意义且可迁移的调控表示。

## Abstract
DNA language models (DNALMs) aim to learn representations of genomic sequence for variant interpretation, regulatory prediction, and sequence design. Most DNALMs are trained on whole genomes and long contexts, but regulatory DNA poses a distinct challenge: functional elements are sparse, context dependent, and encoded by short transcription factor motif syntax embedded in extensive background sequence. We introduce ARSENAL, a short-context masked DNA language model pretrained on ENCODE candidate cis-regulatory elements. ARSENAL recovers diverse transcription factor motifs de novo and improves zero-shot regulatory variant effect prediction relative to other DNALM foundation models. ARSENAL embeddings also improve supervised regulatory sequence models at predicting chromatin accessibility and regulatory variant scoring. Finally, ARSENAL serves as an efficient generative prior, enabling multi-objective regulatory sequence design with supervised oracles. ARSENAL shows that targeted self-supervised pretraining on regulatory regions can learn biologically meaningful and transferable regulatory representations without genome-scale training, long contexts or task-specific labels.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：调控DNA的功能元件（如增强子、启动子）由短转录因子结合基序（motif）编码，这些基序稀疏、依赖于上下文且嵌入大量背景序列。现有大多数DNA语言模型（如Nucleotide Transformer、HyenaDNA、DNABERT-2等）采用全基因组预训练和长上下文（如2k bp以上），但这类范式难以有效捕获局部调控语法——因为基因组中绝大多数序列是非调控的背景DNA，自监督损失可能被重复序列和组成性特征所主导，从而稀释了调控基序的信息。
- **整体含义**：作者提出一个简单但有效的假设——将自监督预训练限定在功能富集的调控区域（而非整个基因组），可以更高效地学习调控DNA的局部语法，无需长上下文或大规模模型。通过构建ARSENAL（靶向调控序列的短上下文掩码语言模型），在ENCODE候选顺式调控元件（cCREs）上预训练，证明了靶向预训练策略在零样本变异效应预测、监督任务迁移和序列生成中均优于或匹敌全基因组模型，为DNA语言模型的设计提供了新思路。

## 2. 论文提出的方法论

- **核心思想**：在功能富集的调控区域（cCREs）上训练短上下文（350 bp）掩码语言模型，使模型专注于学习基序级别的语法，避免背景序列的稀释。
- **关键技术细节**：
  - **模型架构**：8层Transformer编码器，嵌入维度768，8头注意力，前馈维度3072；使用RoPE位置编码；语言模型头为线性层+GeLU+LayerNorm+输出层。
  - **输入与掩码策略**：序列长度固定为350 bp（cCRE最大长度）；采用标准MLM目标：15%的token被处理（80%掩码、10%随机替换、10%保持不变）；额外策略：对≥30 bp的重复区域（由参考基因组小写字母定义）不计算损失，防止模型过度学习重复特征。
  - **数据增强**：以0.5概率随机反转互补；随机偏移-50到+50 bp。
  - **训练**：Adam优化器，学习率1e-4，训练150个epoch。数据按染色体分训练/验证/测试集。
- **公式/算法流程**（文字说明）：
  - 零样本变异评分：对变异位置进行掩码，计算模型输出中参考等位基因和替代等位基因的对数似然比：$s = \log p_\theta(n_{\text{alt}}) / p_\theta(n_{\text{ref}})$。
  - 核苷酸依赖度量：借鉴[32]中的方法，计算位置$i$对位置$j$的依赖程度：$e_{i,j} = \max_{k \in \{A,C,G,T\}} \log_2 \left( \frac{\text{odds}(n_j=k | n_i \neq k_{\text{ref}})}{\text{odds}(n_j=k | n_i = k_{\text{ref}})} \right)$。

## 3. 实验设计

- **数据集与场景**：
  - **预训练数据**：ENCODE cCREs（约230万个候选顺式调控元件，包括启动子、增强子、CTCF结合位点等）。
  - **零样本基序发现**：使用DART-EVAL基准中的motif识别任务；在K562 PRO-cap峰和HepG2 DNase-seq峰上运行TF-MoDISco。
  - **零样本变异效应预测**：DART-EVAL中的Yoruban LCL dsQTL和African caQTL数据集（测量DNase-seq和ATAC-seq染色质可及性QTL）。
  - **监督预测**：五个细胞系（GM12878、HepG2、K562、IMR90、H1-hESC）的DNase-seq数据，采用ChromBPNet架构，将输入从one-hot替换为ARSENAL嵌入。
  - **调控序列生成**：使用ChromBPNet预测的染色质可及性作为目标函数，进行束搜索式生成。
- **基准对比方法**：
  - 零样基准：HyenaDNA、Caduceus（DART-EVAL中报告的结果）。
  - 监督基准：标准ChromBPNet（one-hot输入）。
- **评估指标**：Pearson相关系数、Spearman相关系数、AUROC（用于变异效应分类）。

## 4. 资源与算力

- **明确说明**：论文未公开GPU型号、数量及训练时长。仅提到训练150个epoch，学习率1e-4，模型规模约8层Transformer（参数量未给出）。未提及其他硬件细节（如显存、训练时间等）。因此，算力信息不透明。

## 5. 实验数量与充分性

- **实验组数**：
  - 零样本基序识别：在DART-EVAL基准上对比（1组主要结果） + TF-MoDISco在2个细胞系上的可视化（K562 PRO-cap、HepG2 DNase-seq）。
  - 零样本变异预测：2个QTL数据集（dsQTL、caQTL），每个报告Pearson、Spearman、AUROC。
  - 监督预测：5个细胞系（每个细胞系训练ChromBPNet + ARSENAL嵌入 vs one-hot），包含重复（论文提到“三个模型训练”，但实际表格显示标准误差）。
  - 消融实验：附录中比较了有无Fourier似然正则化（发现无显著差异），对基础模型进行了浮点精度校正对照。
  - 序列生成：针对HepG2单一目标和HepG2 vs H1-hESC双目标，可视化结果。
- **充分性与公平性**：
  - 优点：零样本对比使用了DART-EVAL官方数据，直接引用其他模型的结果，控制设置一致；监督任务中重新训练了同等架构的ChromBPNet作为基线，比较公平。
  - 不足：重复次数较少（例如监督预测未说明具体N次重复，仅给出置信区间，可能基于3次或5次）；零样本结果依赖于其他论文公布的值，可能存在实现差异；未与其他更先进的单核苷酸分辨率模型（如GPN-MSA、Evo2等）进行对比（仅与HyenaDNA、Caduceus比较）；未在更多物种或疾病相关变异上进行验证。

## 6. 论文的主要结论与发现

- 靶向调控元件的短上下文预训练（ARSENAL）能从头恢复多种TF基序，在DART-EVAL最基序识别基准上优于现有DNALMs。
- 零样本调控变异效应预测中，ARSENAL的似然比评分与真实效应量的相关性高于HyenaDNA和Caduceus，且仅需350 bp上下文（对比其他模型使用2114 bp）。
- ARSENAL嵌入作为迁移特征，在ChromBPNet监督架构下稳定提升五个细胞系的染色质可及性预测性能（图5），并在GM12878上提升QTL变异评分（表1）。
- ARSENAL可作为生成先验，结合监督预言机（如ChromBPNet）实现多目标调控序列设计，生成的序列在功能特异性上呈现合理的基序富集模式。
- 关键结论：**全基因组规模训练并非学习调控语法的必要条件；靶向自监督学习足以学到有生物学意义且可迁移的调控表示。**

## 7. 优点

- **方法创新**：首次系统验证了“仅在调控区域预训练”策略的有效性，为DNALM设计提供了一条低计算成本的替代路线。
- **实验全面**：覆盖零样本基序发现、零样本变异预测、监督迁移、序列生成四大任务，验证了表示的可迁移性。
- **分析深入**：通过核苷酸依赖图、TF-MoDISco等可视化工具，揭示了模型学到的基序语法结构。
- **公平比较**：零样本直接引用DART-EVAL中其他模型的结果；监督任务中重新训练ChromeBPNet基线。
- **开源可复现**：提供了代码、模型与数据（GitHub和Sage平台）。

## 8. 不足与局限

- **细胞类型无关性**：ARSENAL自身不建模细胞类型特异性，下游监督任务仍需细胞类型数据。
- **上下文长度限制**：350 bp无法捕获长程调控（如增强子-启动子距离>350 bp的情况）。
- **仅限人类**：预训练仅基于人类cCREs，未推广到其他物种（尽管作者指出跨物种cCREs的挑战）。
- **序列生成验证不足**：生成序列仅通过in silico预测评估，缺乏wet-lab实验验证（如MPRA或CRISPR扰动）。
- **重复序列处理简单**：仅通过软掩码丢弃长重复区域的损失，可能不够精细。
- **对比方法局限**：零样本只对比了HyenaDNA和Caduceus，未包括更新模型如Evo2、GPN-MSA、DNABERT-2等（尽管存在任务差异）。
- **Fourier正则化消融揭示风险**：最初误认为正则化有效，后来发现是浮点精度问题，反映了实验细节需更严谨。
- **结果统计**：监督任务表1中标准误差源于少次重复，未说明具体重复次数；未报告跨细胞系的方差分析。

（完）
