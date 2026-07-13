---
title: Tokenizing single-cell transcriptomes as a native language for large language models
title_zh: 将单细胞转录组标记为大型语言模型的母语
authors: "Xiao, C., Ding, Y., Bian, H., Chen, Y., Wei, L., Zhang, X."
date: 2026-07-11
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.22.684047v2.full.pdf"
tags: ["query:ssl"]
score: 6.0
evidence: 将转录组转化为token并融入LLM，支持多模态自监督学习
tldr: 大型语言模型(LLM)难以处理连续高维的单细胞转录组数据。本文提出CellTok，将转录组转化为紧凑的细胞token序列，融入预训练LLM的词汇表，使细胞测量、文本指令、生物背景和多细胞群体能在同一自回归框架下联合处理。实验表明，LLM能识别个体细胞、解释细胞群体、推断疾病状态、预测细胞通讯、模拟发育轨迹并生成细胞状态，且提供适当生物上下文可提升性能。该方法将单细胞转录组从外来分子模态转变为LLM的本土语言，为细胞数据与生物知识的统一建模建立了接口。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1509, \"height\": 1404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1503, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1500, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1174, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1499, \"height\": 565, \"label\": \"Figure\"}]"
motivation: 单细胞转录组是连续高维分子图谱，与LLM的离散符号空间不兼容，导致LLM难以直接处理这一模态。
method: CellTok将单细胞转录组编码为紧凑的细胞token序列，并将其加入预训练LLM的词汇表，实现多模态联合自回归建模。
result: CellTok使LLM能执行细胞识别、群体解释、疾病推断、通讯预测、轨迹模拟和状态生成等任务，且上下文提示可提升性能。
conclusion: 单细胞转录组可转变为LLM的本土语言，为细胞、群体和生物学知识在统一token空间中建模提供新范式。
---

## 摘要
大型语言模型（LLMs）一旦将不同形式的信息表示为共享序列空间中的标记，就能处理这些信息。然而，单细胞转录组对LLMs而言仍是一种外源性模态，因为它们是连续的、高维的分子图谱，而非离散的语言单元。在此，我们提出CellTok，一种标记化单细胞语言建模方法，它将转录组图谱转换为紧凑的细胞标记序列，并将其整合到预训练LLM的词汇表中。通过将细胞表示为原生标记，CellTok使得细胞测量、文本指令、生物学背景以及多细胞群体能够在同一自回归建模框架内联合处理。在多项任务中，CellTok使LLMs能够识别单个细胞、解读同质和异质细胞群体、推断疾病相关细胞状态、预测细胞间通讯、模拟发育轨迹以及生成细胞状态。此外，基于提示的实验表明，提供适当的生物学背景可提升性能，表明CellTok能够利用LLM的知识和上下文推理来支持细胞数据解读。这些结果证明，单细胞转录组可以从一种外源性分子模态转化为LLMs的母语，从而在共享标记空间中建立用于建模细胞、群体和生物学知识的统一接口。

## Abstract
Large language models (LLMs) can process diverse forms of information once they are represented as tokens in a shared sequence space. However, single-cell transcriptomes remain a foreign modality to LLMs because they are continuous, high-dimensional molecular profiles rather than discrete linguistic units. Here, we propose CellTok, a tokenized single-cell language modeling approach that converts transcriptomic profiles into compact cellular token sequences and incorporates them into the vocabulary of a pretrained LLM. By representing cells as native tokens, CellTok enables cellular measurements, textual instructions, biological context, and multi-cell populations to be jointly processed within the same autoregressive modeling framework. Across diverse tasks, CellTok enable LLMs to recognize individual cells, interpret homogeneous and heterogeneous cell populations, infer disease-associated cellular states, predict cell-cell communication, model developmental trajectories, and generate cellular states. Moreover, prompt-based experiments show that providing appropriate biological context improves performance, indicating that CellTok can leverage LLM knowledge and contextual reasoning to support cellular data interpretation. These results demonstrate that single-cell transcriptomes can be transformed from a foreign molecular modality into a native language for LLMs, establishing a unified interface for modeling cells, populations, and biological knowledge in a shared token space.