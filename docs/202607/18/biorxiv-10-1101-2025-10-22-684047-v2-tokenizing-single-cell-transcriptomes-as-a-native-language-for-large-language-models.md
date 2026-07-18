---
title: Tokenizing single-cell transcriptomes as a native language for large language models
title_zh: 将单细胞转录组标记化为大语言模型的母语
authors: "Xiao, C., Ding, Y., Bian, H., Chen, Y., Wei, L., Zhang, X."
date: 2026-07-11
pdf: "https://www.biorxiv.org/content/10.1101/2025.10.22.684047v2.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 单细胞转录组的自监督标记化方法用于语言模型训练
tldr: 单细胞转录组是连续高维分子谱，大语言模型(LLM)难以直接处理。CellTok将其转化为紧凑的细胞令牌序列，融入预训练LLM词汇表。LLM能识别细胞、解释群体、推断疾病状态、预测细胞通信、建模发育轨迹、生成细胞状态。提供生物上下文可提升性能，建立细胞与生物学知识的统一接口。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1509, \"height\": 1404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1503, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1500, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1174, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2025-10-22-684047-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1499, \"height\": 565, \"label\": \"Figure\"}]"
motivation: 使LLM能够理解并处理单细胞转录组这一非连续、高维的分子模态。
method: 将单细胞转录组转化为紧凑的细胞令牌序列，作为预训练LLM词汇表的一部分。
result: LLM能识别细胞、解释群体、推断疾病状态、预测通信、建模轨迹、生成细胞状态。
conclusion: 单细胞转录组可转化为LLM的本地语言，实现细胞数据与生物学知识的统一建模。
---

## 摘要
大语言模型（LLMs）能够处理多种形式的信息，只要这些信息在共享的序列空间中被表示为标记。然而，单细胞转录组对LLMs而言仍是一种陌生的模态，因为它们是连续的高维分子图谱，而非离散的语言单元。在此，我们提出CellTok——一种标记化单细胞语言建模方法，它将转录组图谱转换为紧凑的细胞标记序列，并将其纳入预训练LLM的词汇表中。通过将细胞表示为原生标记，CellTok使得细胞测量、文本指令、生物学背景以及多细胞群体能够在同一个自回归建模框架中被联合处理。在多项任务中，CellTok使LLM能够识别单个细胞、解读同质和异质细胞群体、推断疾病相关的细胞状态、预测细胞间通讯、模拟发育轨迹以及生成细胞状态。此外，基于提示的实验表明，提供适当的生物学背景可提升性能，说明CellTok能够利用LLM的知识和上下文推理来支持细胞数据解释。这些结果表明，单细胞转录组可以从一种陌生的分子模态转化为LLM的母语，从而在共享的标记空间中建立用于建模细胞、群体和生物学知识的统一接口。

## Abstract
Large language models (LLMs) can process diverse forms of information once they are represented as tokens in a shared sequence space. However, single-cell transcriptomes remain a foreign modality to LLMs because they are continuous, high-dimensional molecular profiles rather than discrete linguistic units. Here, we propose CellTok, a tokenized single-cell language modeling approach that converts transcriptomic profiles into compact cellular token sequences and incorporates them into the vocabulary of a pretrained LLM. By representing cells as native tokens, CellTok enables cellular measurements, textual instructions, biological context, and multi-cell populations to be jointly processed within the same autoregressive modeling framework. Across diverse tasks, CellTok enable LLMs to recognize individual cells, interpret homogeneous and heterogeneous cell populations, infer disease-associated cellular states, predict cell-cell communication, model developmental trajectories, and generate cellular states. Moreover, prompt-based experiments show that providing appropriate biological context improves performance, indicating that CellTok can leverage LLM knowledge and contextual reasoning to support cellular data interpretation. These results demonstrate that single-cell transcriptomes can be transformed from a foreign molecular modality into a native language for LLMs, establishing a unified interface for modeling cells, populations, and biological knowledge in a shared token space.