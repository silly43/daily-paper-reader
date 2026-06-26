---
title: Unsupervised Representation Learning Reveals Individualized Neurophysiological Profiles
title_zh: 无监督表示学习揭示个体化神经生理特征
authors: "Lapatrie, M., da Silva Castanheira, J., Aydin, I., Baillet, S."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.10.705127v2.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 无监督自编码器用于神经生理剖面的自监督表示学习
tldr: "现有监督学习方法难以区分神经生理特征的稳定性与数据中的特殊性能。本文提出参与者无关的自编码器框架，仅使用重建目标从短暂静息态MEG中学习特征。在session内识别准确率达93.3%，记录短至14秒即有效，且跨session泛化高于随机。该方法预测年龄更准确，并支持可解释的敏感性分析，为个体化脑特征提取提供了可扩展且无需标签的方案。"
source: biorxiv
selection_source: fresh_fetch
motivation: 监督式神经生理特征建模难以区分稳定生物学信号与数据中的特殊性能，需参与者无关的方法。
method: 采用自编码器框架，仅以MEG片段重建为训练目标，从潜在空间中提取个体特征。
result: "session内识别准确率93.3%（120s），短至14s有效；跨session准确率49.5%；年龄预测r²=0.318。"
conclusion: 参与者无关表示学习可高效提取可解释、泛化的个体神经生理特征，具有可扩展性。
---

## 摘要
人类大脑活动包含稳定且个体化的特征，这些特征可持续数月甚至数年，形成神经生理特征。大多数基于模型的特征提取方法使用参与者标签或有监督目标，因此难以判断成功的区分是源于稳定的生物学特性还是可利用的个体特异性。我们引入了一种参与者无关的自编码器框架，仅以重建为训练目标，从短暂的静息态脑磁图（MEG）片段中提取特征。在没有参与者标签的情况下，从学习到的潜在空间中涌现出了判别性特征。在同一会话内，自编码器在120秒时达到了93.3%的准确率，当在源重建中省略参与者特定的解剖信息时，仅需14秒的记录就能超越功能连接、频谱和对比基线方法。该特征在跨会话中也能泛化至高于随机水平（预训练自编码器的跨会话准确率为49.5%）。此外，这些特征比基线方法更准确地预测年龄（r²=0.318），并且解码器支持在频谱和连接空间中进行基于扰动的敏感性分析。这确立了参与者无关的表示学习作为一种可扩展且可解释的特征提取方法。

## Abstract
Human brain activity contains stable, individual-specific features that persist over months to years, forming neurophysiological profiles. Most model-based profiling approaches use participant labels or supervised objectives, making it difficult to determine whether successful differentiation reflects stable biology or exploitable idiosyncrasies. We introduce a participant-agnostic autoencoder framework that derives profiles from brief resting-state magnetoencephalography (MEG) segments using reconstruction as sole training objective. Discriminative profiles emerged from the learned latent space without participant labels. Within-session, autoencoder profiles reached 93.3% accuracy at 120 s, exceeding functional-connectivity, spectral, and contrastive baselines with recordings as short as 14 s when participant-specific anatomy was withheld from source reconstruction. Differentiation generalized above chance across recording sessions (between-session accuracy 49.5% for the pretrained autoencoder). Profiles also predicted age more accurately than baselines (r^2=0.318), and the decoder enabled perturbation-based sensitivity analyses in spectral and connectivity spaces. This establishes participant-agnostic representation learning as a scalable and interpretable profiling.