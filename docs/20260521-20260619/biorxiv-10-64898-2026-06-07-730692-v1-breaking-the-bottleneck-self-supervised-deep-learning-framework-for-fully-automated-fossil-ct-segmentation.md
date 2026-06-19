---
title: "Breaking the bottleneck: self-supervised deep learning framework for fully automated fossil CT segmentation"
title_zh: 打破瓶颈：用于全自动化石CT分割的自监督深度学习框架
authors: "Roy, A., Ghosh, P., Weston, F., Hartley, B., Salili-James, A., Poon, S. T. S., Maidment, S. C. R., Butler, R. J."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.07.730692v1.full.pdf"
tags: ["query:ssl"]
score: 9.0
evidence: 自监督SimCLR对比预训练用于化石CT分割
tldr: "古生物CT图像标注耗时且主观，成为大规模分析瓶颈。提出自监督框架，结合SimCLR对比预训练与U-Net，无需人工标注即可自动分割化石。在跨物种数据集上达到93.66% Dice系数，处理时间从100小时降至6小时+数分钟。该方法消除了标注依赖，可实现批量处理，推动古生物学定量分析。"
source: biorxiv
selection_source: fresh_fetch
motivation: "化石CT分割标注成本高（>100小时/数据集），且主观性强，阻碍大规模分析。"
method: 结合SimCLR v1对比预训练、确定性伪标签生成与U-Net细化的自监督端到端框架。
result: "在50626张CT图像上达93.66% Dice和82.42% IoU，跨分类群验证亚体素精度。"
conclusion: 无需人工标注即可全自动分割化石，显著降低处理时间，支持大规模比较分析。
---

## 摘要
在标注训练样本稀缺且前景-背景对比度低的特定领域成像数据的语义分割，仍然是深度学习应用于科学领域的一个开放性挑战。古生物计算机断层扫描（CT）就是这一问题的典型例子：从周围岩石基质中数字化分离化石骨骼劳动强度大（每个数据集≥100小时）、主观性强，且通常依赖昂贵的专有软件，形成了阻碍CT数据大规模快速处理的“分割瓶颈”。在此，我们提出了一种自监督、端到端的框架，结合SimCLR v1对比预训练、确定性伪标签生成和U-Net细化，实现无需人工标注的全自动化石CT分割。利用来自中侏罗世Kilmaluag组（涵盖两栖动物、爬行动物、恐龙和早期哺乳动物）的50,626张CT图像，该框架在训练期间未见过的保留标本上实现了93.66%的Dice系数和82.42%的IoU，与近期基于深度学习的化石CT分割研究报道的最高Dice和IoU值相当。跨类群泛化能力在六个完全外部标本上通过几何方法验证，实现了与手动阈值参考的亚体素网格一致性。通过消除此前限制古生物学深度学习方法的标注需求，该框架将每个标本的处理时间从约100人/小时减少到6小时（一次性UNet训练）加上每个标本1-3分钟（网格生成），这是迈向批量处理和分析CT数据以进行大规模比较和定量分析的关键第一步。

## Abstract
Semantic segmentation of domain-specific imaging data where labelled training examples are scarce and foreground-background contrast is low remains an open challenge in deep learning applied to science. Palaeontological computed tomography (CT) exemplifies this problem: digitally isolating fossilised bone from surrounding rock matrix is labour-intensive ([&ge;]100 hrs/dataset), subjective, and often reliant on expensive proprietary software, creating a "segmentation bottleneck" that prevents large-scale and rapid processing of CT data collections. Here we present a self-supervised, end-to-end framework combining SimCLR v1 contrastive pretraining with deterministic pseudo-label generation and U-Net refinement to fully automate fossil CT segmentation without manual annotation. Using 50,626 CT images from the Middle Jurassic Kilmaluag Formation spanning amphibians, reptiles, dinosaurs, and early mammals, the framework achieved a Dice coefficient of 93.66% and IoU of 82.42% on a held-out specimen not seen during training, comparable to the highest Dice and IoU values reported in recent Deep Learning-based fossil CT segmentation studies. Cross-taxon generalisation was validated geometrically on six fully external specimens, achieving sub-voxel mesh agreement with manually thresholded references. By eliminating the annotation requirement that has limited prior deep learning approaches in palaeontology, this framework reduces per-specimen processing from [~]100 person-hours to 6 hrs (one-time UNet training) +1-3 minutes (mesh generation per specimen), an essential first step towards batch processing and analysis of CT data for large-scale comparative and quantitative analyses.