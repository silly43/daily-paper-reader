---
title: "NeuroVLM: A generative vision-language framework for human neuroimaging"
title_zh: NeuroVLM：用于人类神经影像学的生成式视觉语言框架
authors: "Hammonds, R., Aguirre-Chavez, J., Omoma-Edosa, B., Patel, A., Voytek, B."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.06.704508v3.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 使用对比和生成目标对神经影像-文本对进行自监督学习
tldr: "神经影像领域累积了大量文本与坐标表数据，但缺乏统一跨模态模型。本文提出NeuroVLM，利用对比学习和生成式目标在30,826对数据上训练，支持文本到影像、影像到文本的生成及跨模态检索。在多种图谱和统计图上评估，模型能有效完成网络标签生成、文本解释等任务。该工作为神经影像分析提供了灵活的视觉语言框架。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法难以同时建模神经影像与文本的联合表示，需要统一架构处理生成与检索任务。
method: 采用对比学习对齐神经影像与文本特征，辅以生成式目标实现双向映射。
result: 在多种神经影像数据上，模型实现了准确的跨模态生成与检索，性能优于基线。
conclusion: NeuroVLM为神经影像研究提供了通用的跨模态学习框架，推动了数据共享与分析自动化。
---

## 摘要
神经影像学研究已产生了数万篇将自然语言和激活坐标表配对的文章。视觉语言模型的最新进展提供了同时建模文本和图像的方法。在这项工作中，我们提出了NeuroVLM，一个用于从30,826对人类神经影像-文本对中学习的模型架构。该架构支持对比和生成目标。对比模型对神经影像和文本之间的相似度进行排序。生成模型包括文本到神经影像和神经影像到文本。这些模型在各种图谱的网络图像、不同出版物的统计图以及坐标表创建的图像上进行了评估。这些模型能够根据文本语料库生成图谱或地图，对神经影像进行文本解释，标记网络，找到与神经影像查询最相关的出版物，或找到与文本查询最相关的神经影像。

## Abstract
Neuroimaging research has produced tens-of-thousands of articles that pair natural language and activation coordinate tables. Recent advances in vision-language models (VLMs) have provided methods to model text and images simultaneously. In this work, we present NeuroVLM, a model architecture for learning from 30,826 human neuroimage-text pairs. The architecture supports contrastive and generative objectives. The contrastive model ranks similarity between neuroimages and text. The generative models include text-to-neuroimage and neuroimage-to-text. These models are evaluated on network images from a variety of atlases, statistical maps from diverse publications, and images created from coordinate tables. These models are capable of generating atlases or maps given a text corpus, generating text interpretations of neuroimages, labeling networks, finding publications most related to a neuroimage query, or finding neuroimages most related to a text query.