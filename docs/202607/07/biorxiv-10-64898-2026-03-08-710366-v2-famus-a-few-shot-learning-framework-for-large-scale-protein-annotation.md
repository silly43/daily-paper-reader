---
title: "FAMUS: A Few-Shot Learning Framework for Large-Scale Protein Annotation"
title_zh: FAMUS：一种用于大规模蛋白质注释的小样本学习框架
authors: "Shur, G., Burstein, D."
date: 2026-07-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.08.710366v2.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 用于蛋白质注释的有监督对比学习
tldr: 蛋白质功能注释面临依赖单一最佳匹配和阈值设置困难的问题，尤其对低丰度家族。FAMUS提出基于监督对比学习的框架，将查询序列与所有profile HMMs的相似度转化为紧凑向量表示，利用未注释序列作为负例，无需阈值即可检测数据库外蛋白。在KEGG KO和PANTHER注释上优于KofamScan和InterProScan，提供四个预训练模型。该框架首个基于对比学习的模块化注释工具，支持自定义数据库，易于集成到大规模基因组分析流程。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有自动注释工具依赖单一最佳匹配，难以处理低丰度家族且阈值设置不鲁棒。
method: 使用监督对比学习，将查询序列与所有profile HMMs的相似度向量作为特征，并利用未注释序列作为负例进行训练。
result: 在KEGG KO和PANTHER注释上，FAMUS性能优于KofamScan和InterProScan，并生成了四个高质量注释模型。
conclusion: 首个基于对比学习的通用注释框架，支持自定义数据库，可无缝集成于基因组和宏基因组分析流程。
---

## 摘要
预测基因功能是基因组和宏基因组数据分析中关键且具有挑战性的步骤。当前的自动注释工具通常依赖查询数据库中单一最相似的序列，并且难以稳健地设置注释的命中阈值。每个注释的蛋白质稀疏性使得对代表性不足的家族进行可靠的功能分配变得困难。在此，我们提出了一种用于功能注释的对比学习框架。FAMUS（使用监督对比学习的功能注释方法）将查询序列与一系列谱隐马尔可夫模型进行比较，并将相似性分数转换到一个压缩向量空间中，该空间最小化同一家族蛋白质之间的距离。查询对所有谱的相似性分数被用于其表示，而不是仅考虑排名最高的命中。未注释的序列在训练过程中被作为负例纳入，从而能够在无需用户定义阈值的情况下稳健检测参考数据库范围之外的蛋白质。通过这种方法，FAMUS在KEGG直系同源注释上优于KEGG原生的KofamScan，在PANTHER家族注释上优于InterPro的InterProScan。因此，我们使用来自KEGG直系同源、InterPro家族、OrthoDB和EggNOG数据库的蛋白质家族创建了四个蛋白质注释模型。这四个模型均可通过conda包和我们友好的Web服务器获得，允许用户注释大规模数据集。FAMUS是第一个基于对比学习的全面且模块化的注释框架。它支持预定义数据库和用户自定义数据库以实现定制化注释，并且可以轻松集成到任何基因组和宏基因组分析流程中，以促进准确的大规模功能注释。

## Abstract
Predicting gene function is a pivotal and challenging step in genomic and metagenomic data analysis. Current automatic annotation tools typically rely on the single most similar sequence from the query database and struggle to robustly set hit thresholds for annotation. The sparsity of proteins per annotation makes it challenging to confidently assign gene function for underrepresented families. Here, we present a contrastive learning framework for functional annotation. FAMUS (Functional Annotation Method Using Supervised contrastive learning) compares query sequences to a full array of profile Hidden Markov Models and transforms the similarity scores into a condensed vector space that minimizes the distance of proteins from the same family. The similarity scores of a query to all profiles are used for its representation instead of considering only the top-ranking hit. Unannotated sequences are incorporated as negative examples during training, enabling robust detection of proteins that fall outside the scope of the reference database without requiring a user-defined threshold. Using this approach, FAMUS outperformed KEGGs native KofamScan for KEGG Orthology annotation and InterPros InterProScan for PANTHER family annotation. We thus created four protein annotation models using protein families from the KEGG Orthology, InterPro family, OrthoDB, and EggNOG databases. All four models are available as a conda package and via our user-friendly web server, allowing users to annotate large-scale datasets. FAMUS is the first comprehensive and modular annotation framework based on contrastive learning. It supports both pre-defined and user-specific databases for tailored annotation, and can be easily integrated into any genomic and metagenomic analysis pipeline to facilitate accurate, large-scale functional annotation.