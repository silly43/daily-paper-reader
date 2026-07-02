---
title: "NeuroVLM: A generative vision-language framework for human neuroimaging"
title_zh: NeuroVLM：一种用于人类神经影像的生成式视觉-语言框架
authors: "Hammonds, R., Aguirre-Chavez, J., Omoma-Edosa, B., Patel, A., Voytek, B."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.06.704508v3.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 在神经影像-文本对上使用对比和生成目标进行自监督学习
tldr: "神经影像学领域积累了大量配对文本与激活坐标数据，但缺乏统一的跨模态模型。本文提出NeuroVLM，一种基于视觉-语言模型的生成式框架，利用30,826个神经影像-文本对进行对比和生成训练。模型支持文本生成影像、影像生成文本及相似度检索等多种任务。实验表明，该方法能有效生成图谱、解释影像、标注网络等，为神经影像分析提供了新工具。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有神经影像分析缺乏同时处理文本和图像的统一模型，难以充分利用大量配对数据。
method: 提出NeuroVLM架构，使用对比学习和生成式目标从3万多个神经影像-文本对中训练。
result: 模型在多种数据集上实现文本生成影像、影像生成文本、检索等任务，性能良好。
conclusion: NeuroVLM为神经影像与自然语言的跨模态理解提供了有效框架，拓展了应用场景。
---

## 摘要
神经影像研究已经产生了数万篇将自然语言与激活坐标表格配对的文章。视觉-语言模型（VLM）的最新进展提供了同时建模文本和图像的方法。在这项工作中，我们提出了NeuroVLM，这是一种用于从30,826个人类神经影像-文本对中学习到的模型架构。该架构支持对比性和生成性目标。对比性模型对神经影像与文本之间的相似性进行排序。生成性模型包括文本到神经影像和神经影像到文本。这些模型在各种图谱的网络图像、不同出版物的统计图以及由坐标表格创建的图像上进行评估。这些模型能够根据给定的文本语料库生成图谱或统计图，生成神经影像的文本解释，标注网络，找到与神经影像查询最相关的出版物，或找到与文本查询最相关的神经影像。

## Abstract
Neuroimaging research has produced tens-of-thousands of articles that pair natural language and activation coordinate tables. Recent advances in vision-language models (VLMs) have provided methods to model text and images simultaneously. In this work, we present NeuroVLM, a model architecture for learning from 30,826 human neuroimage-text pairs. The architecture supports contrastive and generative objectives. The contrastive model ranks similarity between neuroimages and text. The generative models include text-to-neuroimage and neuroimage-to-text. These models are evaluated on network images from a variety of atlases, statistical maps from diverse publications, and images created from coordinate tables. These models are capable of generating atlases or maps given a text corpus, generating text interpretations of neuroimages, labeling networks, finding publications most related to a neuroimage query, or finding neuroimages most related to a text query.