---
title: A hyperbolic topological atlas reveals polyamine steering of a shared developmental manifold in Arabidopsis
title_zh: 双曲拓扑图谱揭示拟南芥共享发育流形上的多胺引导
authors: "Zdrazil, J., Kong, L., Flores-Hernandez, E., Rodriguez Kessler, M., Klimes, P., Spichal, L., De Diego, N., Snasel, V."
date: 2026-06-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.23.733990v1.full.pdf"
tags: ["query:ssl"]
score: 7.0
evidence: 使用自监督视觉骨干进行植物表型分析
tldr: 高通量植物表型分析通常将图像简化为静态特征。本研究利用自监督视觉骨干和双曲流形方法，分析了13.8万张拟南芥莲座发育图像，发现所有处理共享一个单一连通发育流形。多胺身份按发育阶段分层：腐胺富集早期，亚精胺占据过渡走廊，精胺标记晚期紧凑莲座。突变体改变停留时间而非产生新拓扑，流形拉直量化出早期横向偏移和远端占用两个标量。该框架将大规模图像转化为可解释的发育几何。
source: biorxiv
selection_source: fresh_fetch
motivation: 理解营养和多胺如何沿共同或不同轨迹重塑拟南芥莲座发育的动态几何。
method: 采用自监督视觉骨干、Poincare嵌入和双曲Mapper构建发育流形，并用流形拉直量化早期偏转与远端占用。
result: 数据形成单一连通流形，多胺身份按发育阶段分层，基因型改变共享区域停留时间，营养调整远端占用。
conclusion: 提供了一个将大规模时序图像转化为发育几何的框架，揭示了多胺对共享流形的导向作用。
---

## 摘要
高通量植物表型分析实现了大规模发育监测，然而富含图像的筛选仍常被简化为静态性状汇总。我们测试了养分可用性、多胺引发、浓度及其转运是否通过产生不同形态或沿共同轨迹改变停留时间来重塑拟南芥莲座发育。利用自监督视觉骨干、庞加莱嵌入、双曲Mapper及流形拉直方法，分析了来自Col-0和五个参与多胺转运的突变体（put1-5）的138,223张时间分辨莲座图像，这些突变体经腐胺、亚精胺、精胺、剂量及养分处理。数据形成一个包含410个节点和746条边的单一连通发育流形，从早期低营养偏好的枢纽出发，经由高介数过渡走廊，通向两个晚期富营养的末端区域。多胺身份按发育阶段分层该流形：腐胺富集早期状态，亚精胺占据过渡走廊，而精胺标记晚期紧凑莲座。养分丰富度和剂量改变远端占用，而put基因型改变共享区域内的停留时间而非产生独立拓扑。流形拉直将这些效应解析为一个短暂的早期侧向偏转，随后收敛，产生两个标量读数——早期横向偏移和远端占用——从而在共同形态动力学尺度上总结处理作用。该框架将大规模图像筛选转化为基于图像的组学中可解释的发育几何。

## Abstract
High-throughput plant phenotyping captures development at scale, yet image-rich screens are still often reduced to static trait summaries. We tested whether nutrient availability, polyamine priming, concentration, and their transport reshape Arabidopsis rosette development by generating distinct morphologies or by changing residence along a common trajectory. We analyzed 138,223 time-resolved rosette images from Col-0 and five mutants involved in polyamine transport (put1-5) primed to putrescine, spermidine, spermine, dose, and nutrient regimes using a self-supervised vision backbone, Poincare embedding, hyperbolic Mapper, and manifold straightening. The data form a single connected developmental manifold with 410 nodes and 746 edges, organized from an early, low-nutrient-biased hub through high-betweenness transition corridors to two late, nutrient-enriched terminal regions. Polyamine identity stratifies this manifold by developmental phase: putrescine enriches early states, spermidine occupies transition corridors, and spermine marks late compact rosettes. Nutrient richness and dose change distal occupancy, whereas put genotypes alter dwell time within shared regions rather than producing separate topologies. Manifold straightening resolves these effects into a short early lateral deflection followed by convergence, yielding two scalar readouts, early transverse offset and distal occupancy, that summarize treatment action on a common morphodynamic scale. The framework converts large image screens into interpretable developmental geometry for image-based phenomics.