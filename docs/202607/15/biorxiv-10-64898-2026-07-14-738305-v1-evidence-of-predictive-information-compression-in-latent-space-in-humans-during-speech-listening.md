---
title: Evidence of predictive information compression in latent space in humans during speech listening
title_zh: 人类言语感知过程中潜在空间中预测信息压缩的证据
authors: "Corsini, A., Schneider, S., Tomassini, A., Pedani, L., Fadiga, L., D'Ausilio, A."
date: 2026-07-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.14.738305v1.full.pdf"
tags: ["query:world-models"]
score: 8.0
evidence: 利用预测自编码器在听觉中实现潜在空间预测
tldr: 语音感知的计算原理存在争议，经典高效编码主张压缩输入，而预测编码理论强调预测信息。本文通过对比三种模型（深度自编码器、预测自编码器、对比学习预测信息）的语音潜在表征与EEG数据，发现预测信息表征最好地解释了神经活动，并且只有压缩预测信息的表征能预测行为。这表明人脑语音处理更倾向于编码潜在空间中的预测信息而非简单压缩。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1761, \"height\": 1488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1755, \"height\": 1174, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1737, \"height\": 1225, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1741, \"height\": 1639, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1726, \"height\": 1316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1745, \"height\": 1713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1752, \"height\": 1089, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1753, \"height\": 805, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-14-738305-v1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1749, \"height\": 1569, \"label\": \"Figure\"}]"
motivation: 探究语音感知的神经计算原理是压缩还是预测信息编码。
method: 比较三种模型（最优压缩、预测重建、潜在空间预测）的语音表征与EEG数据。
result: 预测信息表征最优匹配神经活动，且选择性压缩预测信息的表征预测行为。
conclusion: 人脑语音表征编码的是潜在空间中的预测信息，而非最大化压缩输入。
---

## 摘要
言语感知需要将听觉输入转化为支持语言理解的神经表征，但其潜在的计算原理仍不清楚。经典的高效编码理论主张对感官输入进行最优压缩，而另一种观点则认为神经系统的编码优先支持预测。一个关键未解决的问题是，这种预测编码是基于固定输入还是灵活的内部表征。我们实例化了三种言语处理假设模型：(i) 基于深度自动编码器的最优压缩，(ii) 基于预测自动编码器的预测重构，以及(iii) 通过对比学习利用潜在空间预测实现预测信息表征。我们将产生的言语潜在表征与言语聆听期间的脑电图（EEG）活动进行比较。在预测信息目标下学习的表征最好地解释了神经潜在活动。关键在于，只有选择性地压缩预测信息的表征能够预测行为表现，这表明神经言语表征的结构是为了在潜在空间中编码预测信息，而不是为了最大化压缩或输入预测。

## Abstract
Speech perception requires transforming acoustic input into neural representations that support linguistic understanding, yet its underlying computational principles remain unclear. Classical efficient coding theories posit optimal compression of sensory input, whereas alternative accounts propose that neural systems preferentially encode information that supports prediction. A key open question is whether such predictive encoding operates on fixed inputs or on flexible internal representations. We instantiated three hypothesis models of speech processing: (i) optimal compression with deep autoencoders, (ii) predictive reconstruction with predictive autoencoders, and (iii) predictive information representation via latent-space prediction using contrastive learning. We compared resulting speech latent representations to electroencephalographic (EEG) activity during speech listening. Representations learned under the predictive information objective best explained neural latents. Crucially, only representations that selectively compressed predictive information predicted behavioral performance, suggesting that neural speech representations are structured to encode predictive information in latent space rather than to maximize compression or input prediction.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：言语感知的神经计算原理是遵循“经典高效编码”理论（对感官输入进行最优压缩），还是遵循“预测编码”理论（优先编码对预测有用的信息）？此外，如果预测编码成立，其操作对象是固定输入还是灵活的内部表征（潜在空间）？
- **研究背景**：经典理论（Barlow, Attneave）认为神经系统在信道容量约束下最大化输入信息；预测编码理论（Bialek, Friston等）认为神经系统应编码预测性信息。言语感知中，M/EEG研究常依赖先验特征（如包络、频谱图、音素），但无法揭示大脑如何自动提取相关信息。近期深度学习模型（如wav2vec 2.0、GPT-2）可生成丰富表征，但未明确测试神经系统的计算原则。
- **整体含义**：本文旨在直接比较三种计算假设（最优压缩、预测重构、潜在空间预测信息）与人类EEG活动和行为表现的关系，从而揭示言语感知的神经计算原则。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 基于同一高维言语特征（wav2vec 2.0 768维输出），通过改变深度学习模型的架构和目标函数，实例化三种不同假设，然后将模型学到的潜在言语表征与EEG神经活动进行互信息比较，并检验与行为表现的相关性。

### 关键技术细节

#### 特征提取
- 使用预训练模型 **wav2vec 2.0**（BASE_960H）提取每句语音的最终上下文表征（第12层，768维，采样率约50 Hz）。

#### 三种假设模型
1. **深度自动编码器（deep-AE）**：学习最优非线性压缩，解码器用重构损失（MSE）重建当前输入。
2. **深度预测自动编码器（deep-pAE）**：学习最优非线性压缩，解码器最小化对未来输入（正样本，20 ms后）的预测误差。
3. **对比学习模型（CL）**：基于联合嵌入架构，使用 **InfoNCE 损失**在潜在空间进行预测，不进行显式重构。损失函数：
   $$L_n = \mathbb{E}_{x, y^+, y_i}\left[ -\psi(x, y^+) + \log \sum_{i=1}^n e^{\psi(x, y_i)} \right]$$
   其中 $\psi(x,y)=\varphi(f(x), f(y))/\tau$，$f$ 为MLP编码器，$\varphi$为余弦相似度，$\tau=1$。正样本为下一个时间步（20 ms偏移），负样本随机抽取4096个。

#### 互信息计算
- 使用 **高斯Copula互信息（GCMI）** 估计器计算EEG与模型潜在表征之间的互信息（MI），时间滞后范围 -0.6 s 到 0.8 s，步长20 ms。
- 统计显著性通过圆形移位生成100个替代数据，并进行单侧聚类置换检验。

#### 行为任务
- 押韵任务（rhyming task）：听句子后判断屏幕上出现的单词是否与句中某词押韵，作为语音识别能力的代理指标。
- 转录任务：在单独的 behavioral 会话中，被试听半数句子并尽可能准确转录，用 OpenAI text-embedding-ada-002 计算余弦相似度作为转录准确率。

## 3. 实验设计

### 数据集
- **刺激材料**：USC-TIMIT 数据集的100个英语短句（时长2.9–4.5秒），由同一男性母语者发音。音频采样率22.05 kHz，实验时重采样到16 kHz输入wav2vec 2.0。
- **被试**：26名健康意大利母语者（英语为第二语言），自报英语水平保证变异。

### 实验流程
- 行为 session（EEG前两天）：50句朗读 + 50句转录。
- EEG session（押韵任务）：每句播放三次，共300试次，分三个block。每次听句后，视觉呈现一个单词，被试按键判断是否押韵。
- 数据同步：音频同时发送到扬声器和EEG设备，确保时间对齐。

### 对比方法
- **基线模型**：
  - 原始wav2vec 2.0特征（768维）直接与EEG比较。
  - PCA降维（top/bottom方差子空间）：解释方差比从0.1%到99.99%的多种子空间。
- **三种假设模型**：deep-AE, deep-pAE, CL（维度从2到128，重点分析3、7、16、32、64、128）。
- **行为相关性分析**：计算每个被试的MI与押韵任务准确率的皮尔逊相关系数。

### 额外分析
- 句子ID解码（kNN分类器）评估不同模型保持句子特定信息的能力。
- 线性预测/重构任务（R²）评估模型能力。
- 时间序列分析：按预测信息高低（ΔI）将样本分为LΔI和HΔI类，比较EEG编码模式。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长。
- 仅提及CL模型训练在CUDA enabled GPU上进行，训练步数10000步，batch size=4096，学习率0.0001，使用Adam优化器。
- deep-AE和deep-pAE训练参数相同（除损失函数为MSE外）。
- 不同维度模型（2–128）各训练一次，时间偏移模型（1–10步）单独训练。

## 5. 实验数量与充分性

- **实验数量**：较为充分。
  - 行为转录与押韵任务相关性验证（n=26，r=0.93，p<7e-12），证明押韵任务可靠。
  - wav2vec 2.0特征与EEG的MI显著性检验（置换检验）。
  - PCA 8个子空间（4个top+4个bottom）逐维度与EEG比较。
  - 三种模型在6种输出维度（3,7,16,32,64,128）下的MI比较，每维度均做群组统计检验（Bonferroni校正）。
  - 时间序列分析（-0.6到0.8s）覆盖不同滞后。
  - ΔI分类分析（LΔI vs HΔI）的EEG编码比较。
  - 不同时间偏移（20–200 ms）的CL模型对比。
  - 句子ID解码（kNN）、线性预测/重构R²评估。
- **充分性与客观性**：
  - 使用替代数据（n=100）进行置换检验，控制错误发现率。
  - 聚类置换检验用于时间序列，避免多重比较问题。
  - 所有比较均在相同训练/测试设置下进行（相同编码器架构、训练步数、数据量）。
  - 缺点：未进行跨被试交叉验证，被试内重复较少（每句仅3次重复）。未报告不同随机种子的复现性。对比模型（deep-AE, deep-pAE）未使用超参数搜索，可能未达最优。

## 6. 论文的主要结论与发现

1. **wav2vec 2.0特征显著编码于EEG**，但其编码强度与行为表现不相关（r=0.09, p=0.64）。说明高级ASR特征虽包含言语信息，但未捕捉行为相关的计算。
2. **线性降维（PCA）** 无法分离行为相关信息：高方差和低方差子空间均被EEG显著编码，但均不预测行为。
3. **对比学习（CL）模型**学到的预测信息表征**最强烈地被EEG编码**，显著优于两种自动编码器（每个维度均p<0.05，Bonferroni校正）。
4. **只有低维CL表征**（维度3和7）的EEG编码强度与押韵任务准确率**正相关**（dim3: r=0.45, p=0.019; dim7: r=0.43, p=0.026）。高维或强重构模型不满足此条件。
5. **预测信息累积的时间模式**：EEG对高ΔI（高频预测信息积累）样本的编码在早期阶段（约-200~0 ms）高于低ΔI样本，且仅高ΔI样本的早期编码与行为相关。这表明行为相关的神经活动与早期非冗余预测信息的提取一致。
6. **结论**：人脑在言语感知中**压缩预测信息**而非最大化输入信息，这一过程发生在**潜在空间**中通过预测实现，而非通过输入空间预测误差最小化。该结果符合Craik（1943）提出的“内在模型”假说。

## 7. 优点

- **清晰的理论驱动**：直接实例化三种竞争性计算假设，在相同特征基础上进行比较，避免了架构差异带来的混淆。
- **组合神经和行为测量**：不仅比较模型与EEG的匹配度，还检验与行为表现的相关性，从而区分“神经编码”与“行为相关编码”。
- **精细的时间分析**：时间滞后和ΔI分类揭示预测信息积累的动态过程，与言语节律（~200 ms音节）吻合。
- **使用InfoNCE估计预测信息**：理论解释了CL模型倾向于最小充分统计量的原因，提供了计算机制的解释。
- **控制冗余与压缩**：验证了低维压缩预测信息才能预测行为，而冗余高维表征虽也在神经活动中编码但不驱动行为，符合神经系统的效率假说。

## 8. 不足与局限

- **实验覆盖**：仅使用英语刺激，被试为意大利语母语者（第二语言），结论推广性有限。未测试母语情况或不同语言类型。
- **时域分辨率**：EEG时间分辨率有限（重采样至50 Hz），可能丢失快速语音特征（如音素过渡）。
- **模型简化**：实际听觉系统存在多层反馈和双向处理，本文使用静态前馈模型，未模拟自上而下预测。训练目标为单步预测（20 ms），未考虑更长窗口。
- **算力与复现性**：未报告GPU型号、训练复现性（不同随机种子）、超参数敏感性分析，可能影响结果稳健性。
- **对比公平性**：deep-AE和deep-pAE使用MSE损失，而CL使用InfoNCE；架构虽相似但损失函数差异大，可能引入偏差。此外，未尝试其他预测编码模型（如显式预测编码网络）。
- **相关性而非因果性**：行为与MI的相关性不能证明因果性；未进行因果干预（如TMS）或解码重构验证。
- **替代数据方法**：圆形移位保持自相关，但可能破坏非平稳特征，需谨慎解释。

（完）
