---
title: An atlas-scale generative model for unified representation learning of bulk RNA-seq data
title_zh: 一种图谱规模的大规模RNA-seq数据统一表示学习的生成模型
authors: "Pande, A., Uyar, B., Akalin, A."
date: 2026-06-24
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.18.733198v1.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 有监督变分自编码器用于批量RNA-seq表征学习
tldr: "公共批量RNA-seq数据整合困难，缺乏预训练基础模型。本文收集118,263个样本并映射到42种组织，训练监督变分自编码器。模型以94.9%平衡准确率分类组织来源，将16,115个基因压缩至121维潜空间，组织身份是主要组织轴。独立验证集达到84.6%一致性，数据规模增大带来边际收益。该模型为批量RNA-seq提供了统一的表示学习工具，代码和Web应用已公开。"
source: biorxiv
selection_source: fresh_fetch
motivation: 公共批量RNA-seq数据整合困难，缺乏统一的预训练基础模型进行表示学习。
method: "构建118,263样本复合数据集，映射42组织类别，训练监督VAE将16,115基因压缩至121维潜空间。"
result: "组织分类平衡准确率94.9%，潜空间以组织身份为主轴；独立队列一致性84.6%，数据规模增大效果递减。"
conclusion: 实现了批量RNA-seq的统一表示学习，促进跨研究整合；模型与代码已公开。
---

## 摘要
公共大规模RNA-seq数据库包含数十万个样本，为大规模表示学习创造了机会，但由于异质性注释、实验方案和技术差异，跨研究整合仍具有挑战性。虽然单细胞RNA-seq的预训练基础模型现已广泛可用，但大规模RNA-seq的类似资源仍然稀缺，这促使我们开发一个直接从批量数据中学习统一、组织感知表示的模型。我们在一个包含118,263个批量RNA-seq样本的汇编数据集上训练了监督变分自编码器（VAE），这些样本来自TCGA、GTEx和ARCHS4，并映射到42个组织类别。该模型以94.9%的平衡准确率（加权F1为96.2%）对组织来源进行分类，并将16,115个基因压缩到121维的潜在空间中。组织身份是潜在空间的主要组织轴，而来源效应仍然是次要的。为了评估数据量的影响，我们构建了三种不同规模（38K、75K和118K样本）的训练集。结果表明，随着数据集的每次扩展，重建保真度逐步提高，但收益递减。我们在一组来自TARGET的734个儿科肿瘤样本独立队列上验证了该模型，与预期组织来源的一致性达到84.6%。训练好的模型和代码可在GitHub（https://github.com/BIMSBbioinfo/flexynesis_tissue_vae_manuscript）上获取，并附带一个交互式网络应用程序。

## Abstract
Public bulk RNA-seq repositories contain hundreds of thousands of samples, creating opportunities for large-scale representation learning, but integration across studies remains challenging because of heterogeneous annotations, experimental protocols, and technical variation. While pre-trained foundation models are now widely available for single-cell RNA-seq, comparable resources for bulk RNA-seq remain scarce, motivating a model that learns a unified, tissue-aware representation directly from bulk data. We trained a supervised variational autoencoder (VAE) on a compendium of 118,263 bulk RNA-seq samples that we assembled from TCGA, GTEx, and ARCHS4 and mapped to 42 tissue categories. The model classifies tissue of origin at 94.9% balanced accuracy (weighted F1 96.2%) and compresses 16,115 genes into a 121-dimensional latent space. Tissue identity is the primary organizing axis of the latent space, while source effects remain secondary. To assess the impact of data volume, we constructed training sets at three different scales (38K, 75K, and 118K samples). Our results demonstrated that reconstruction fidelity improved incrementally with each expansion of the dataset, but with diminishing returns. We validated the model on an independent cohort of 734 paediatric tumour samples from TARGET, achieving 84.6% agreement with the expected tissue of origin. The trained model and code are available at GitHub (https://github.com/BIMSBbioinfo/flexynesis_tissue_vae_manuscript) with an interactive web application.