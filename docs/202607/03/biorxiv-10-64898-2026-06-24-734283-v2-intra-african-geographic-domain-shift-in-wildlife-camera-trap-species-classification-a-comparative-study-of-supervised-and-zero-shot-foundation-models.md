---
title: "Intra-African Geographic Domain Shift in Wildlife Camera Trap Species Classification: A Comparative Study of Supervised and Zero-Shot Foundation Models"
title_zh: 非洲内部地理领域迁移对野生动物相机陷阱物种分类的影响：有监督与零样本基础模型的比较研究
authors: "Nanduri, N., Ogundare, J., Anderson, G."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.24.734283v2.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 评估自监督模型BEiTV2用于野生动物分类
tldr: 针对非洲不同地区野生动物图像的地理域迁移问题，本研究比较了监督微调模型BEiTV2、特征检索模型DINOv2+FAISS和零样本模型BioCLIP在南部非洲测试集上的表现。八项实验表明，监督模型在域内表现优异但跨域后性能严重下降，而零样本模型BioCLIP在跨域场景下保持较高鲁棒性。该工作首次系统刻画非洲内部域迁移，为缺乏标注数据的保护项目提供了实用模型选择指南。
source: biorxiv
selection_source: fresh_fetch
motivation: 监督模型在非洲不同区域部署时因地理域迁移导致性能下降，但缺乏系统性评估。
method: 采用BEiTV2微调、DINOv2+FAISS检索和BioCLIP零样本三种架构，在南部非洲数据集上开展八项对比实验。
result: 零样本模型BioCLIP在跨域场景下表现优于监督模型，域迁移导致监督模型准确率显著下降。
conclusion: 首次实证刻画非洲内部域迁移，建议在无新标注数据时优先使用零样本基础模型。
---

## 摘要
诸如Snapshot Safari之类的相机陷阱网络已在非洲各地生成了数百万张标记的野生动物图像，使得能够训练深度学习模型进行自动化物种分类。然而，将在非洲一个地区训练的模型部署到另一个地区的情况仍然知之甚少。据我们所知，本研究首次系统评估了非洲大陆内野生动物相机陷阱物种分类的地理领域迁移问题，采用了人工智能的机器学习子领域。我们使用了三种模型架构，每种架构以不同方式与Snapshot Serengeti交互：BEiTV2在Serengeti图像上微调作为有监督基线；带有FAISS的DINOv2使用Serengeti图像作为检索索引，不更新任何权重；而BioCLIP是一个真正的零样本基础模型，完全没有接收Serengeti训练数据。然后，我们在两个南部非洲测试集——Snapshot Kgalagadi和Snapshot Kruger——以及博茨瓦纳当地收集的野生动物照片上评估了这三个模型。我们进行了八项实验，涵盖域内基线、跨数据集迁移、数据缩放、MegaDetector预处理、灰度与彩色图像条件以及逐物种迁移分析。这项工作首次通过有监督和零样本架构对非洲内部域迁移进行了实证特征描述，并为需要在不收集新标记数据的情况下将模型部署到南部非洲多样化生态系统的保护人工智能从业者提供了实用指导。

## Abstract
Camera trap networks such as Snapshot Safari have generated millions of labelled wildlife images across Africa, enabling the training of deep learning models for automated species classification. However, deploying models trained in one African region to another remains poorly understood. To the best of our knowledge, this study presents the first systematic evaluation of geographic domain shift within the African continent for wildlife camera trap species classification, using the Machine Learning sub-field of Artificial Intelligence. We use three model architectures, each interacting with Snapshot Serengeti in a different way: BEiTV2 is fine-tuned on Serengeti images as a supervised baseline; DINOv2 with FAISS uses Serengeti images as a retrieval index without any weight updates; and BioCLIP is a true zero-shot foundation model that receives no Serengeti training data at all. All three are then evaluated on two Southern African test sets--Snapshot Kgalagadi and Snapshot Kruger --as well as on locally collected wildlife photographs from Botswana. We conduct eight experiments covering in-domain baselines, cross-dataset transfer, data scaling, MegaDetector preprocessing, grayscale vs. colour image conditions, and per-species transfer analysis. This work provides the first empirical characterisation of intra-African domain shift across both supervised and zero-shot architectures, and offers practical guidance for conservation AI practitioners who need to deploy models across the diverse ecosystems of Southern Africa without collecting new labelled data.