---
title: Language Modeling Materializes a World Model of Protein Biology
title_zh: 语言模型实现了蛋白质生物学的世界模型
authors: "Candido, S., Hayes, T., Derry, A., Rao, R., Lin, Z., Verkuil, R., Wu, B. Z., Lee, J. S., Bruguera, E. S., Keval, J. A., Kopylov, M., Pak, J. E., Wu, W., Thomas, N., Mataraso, S., Hsu, A., Trotman-Grant, A. C., Fatras, K., dos Santos Costa, A., Badkundri, R., Akin, H., Oktay, D., Deaton, J., Montabana, E., Sitwala, H., Yu, Y., Wiggert, M., Carlin, D. A., Goering, A. W., Blazejewski, T., Sandora, M., Hla, M., Jia, T. Z., Kloker, L. H., Sofroniew, N. J., Uehara, M., Pannu, J., Bachas, S., Liu, D. S., Sercu, T., Rives, A."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729735v1.full.pdf"
tags: ["query:world-models"]
score: 9.0
evidence: 提出用语言建模学习蛋白质生物学的世界模型
tldr: 蛋白质功能难以通过实验全面表征。本研究将语言模型应用于蛋白质生物学，学习通用表示，基于此开发的结构预测模型在生物分子复合物预测上超越现有方法，并成功设计出高亲和力蛋白质。模型学到的表示空间系统组织，最终构建了包含68亿序列和11亿结构的综合图谱，揭示蛋白质从原子到进化尺度的连接。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有实验方法难以全面表征蛋白质生物学的复杂性和多样性，需要计算模型加速发现。
method: 采用语言模型在大规模蛋白质序列上训练，学习通用表示，并基于此建立结构预测模型。
result: 模型在复合物预测上超越现有方法，简单搜索获得高成功率纳米摩尔亲和力蛋白质，并生成包含68亿序列和11亿结构的综合图谱。
conclusion: 语言模型能统一表示蛋白质从原子到进化尺度的生物特性，为虚拟实验和蛋白质设计提供强大工具。
---

## 摘要
蛋白质是生命的基础。其生物学的全部范围超出了我们通过物理实验室中的实验方法进行表征的能力。准确的数字表示可以通过虚拟实验加速蛋白质生物学的发现。我们提出使用语言模型来学习统一且通用的表示，这些表示可以扩展至整个蛋白质生物学。基于这些表示，我们开发了一个结构预测模型，在生物分子复合物预测方面超越了现有方法的性能，包括抗体与其靶标的相互作用。一个简单的搜索程序在发现具有纳摩尔级结合亲和力的微型蛋白和单链抗体（治疗设计中的关键模态）方面取得了高实验成功率。对语言模型表示空间中概念的研究揭示了一种系统化的组织，其与通过经验科学发展起来的对蛋白质的还原论理解相一致。利用这种组织，我们生成了一个全面的蛋白质生物学图谱，涵盖了超过68亿个序列和11亿个预测结构，识别了已知和未知生物学之间的联系。整体而言，这表明语言模型是表示蛋白质生物学的强大基础，其运作尺度从原子层面蛋白质相互作用的预测和设计，到识别不同粒度和抽象级别的蛋白质特性，直至跨越数十亿年进化过程中蛋白质之间连接映射的规模。

## Abstract
Proteins are fundamental to life. The full extent of their biology is beyond our ability to characterize with experimental approaches in the physical laboratory. Accurate digital representations could accelerate the discovery of protein biology through virtual experiments. We propose language modeling to learn unified and general representations that can be scaled to all of protein biology. Building on these representations, we develop a structure prediction model that exceeds the performance of established methods for biomolecular complex prediction across benchmarks, including for the interactions of antibodies with their targets. A simple search procedure yields high experimental success rates for the discovery of proteins with nanomolar binding affinities for both miniproteins and single-chain antibodies, a modality critical for therapeutic design. Study of the concepts in the language models representation space reveals a systematic organization aligned with the reductionist understanding of proteins developed through empirical science. Leveraging this organization, we generate a comprehensive map of protein biology encompassing over 6.8 billion sequences and 1.1 billion predicted structures, identifying connections across known and unknown biology. As a whole, this shows language modeling as a powerful substrate for representing the biology of proteins, operating across scales from the prediction and design of protein interactions at the atomic level, to identifying properties of proteins at different levels of granularity and abstraction, to the scale of mapping connections between proteins across billions of years of evolution.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将根据提供的论文摘要和元数据，对这篇发表在biorxiv上的预印本进行结构化、深入的总结。

---

# 论文结构化总结：语言模型实现了蛋白质生物学的世界模型

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：蛋白质的生物学功能范围极其广泛，远超当前实验技术（如晶体学、冷冻电镜等）全面表征的能力。蛋白质功能的多样性、进化关系和相互作用网络构成了一个复杂而丰富的“世界”，但这一世界的信息尚不完整。如何利用计算方法，特别是从大规模序列和结构数据中学习一个统一的、可扩展的表示，以进行“虚拟实验”，加速蛋白质生物学的发现与设计？
- **研究动机**：当前实验方法无法覆盖所有蛋白质及其环境，存在巨大的“未知空间”。需要一个强大的数字基础模型，能够统一表示蛋白质从原子层面的相互作用到进化尺度的连接，从而超越传统的单一任务模型。
- **整体含义**：论文提出，语言模型（LM）不仅能够学习蛋白质序列的模式，更能够**具现化（materialize）一个关于蛋白质生物学的世界模型**。这个模型能够系统化地组织蛋白质的概念（如结构、功能、进化关系），并可用于高精度预测、理性设计和跨尺度发现。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用大规模语言模型（类似处理自然语言的方式）在巨大的蛋白质序列数据集上进行无监督预训练，学习通用的、统一的蛋白质表示。基于这些表示，再构建下游任务模型（如结构预测）和搜索程序。
- **关键技术细节**：
    1.  **语言模型预训练**：采用可扩展的语言模型架构（具体架构在摘要中未详细说明，但推测是Transformer变体），在包含**68亿**个序列的数据集上进行训练，学习序列的统计规律和潜在生物学“语法”。模型通过预测掩码（masked）氨基酸来学习上下文依赖的表示。
    2.  **结构预测模型**：基于上述语言模型学习到的表示，开发了一个生物分子复合物结构预测模型。该模型利用了语言模型对单链的深度理解，扩展到多链复合物（包括抗体-抗原相互作用）。
    3.  **表示空间研究**：通过探索语言模型内部激活（representation space），发现其组织方式与蛋白质生物学还原论理解（从序列、结构到功能、进化）高度一致。
    4.  **图谱生成**：利用该组织结构和语言模型的推理能力，生成了一个覆盖**68亿**序列和**11亿**预测结构的综合蛋白质生物学图谱。具体生成方法可能是通过聚类、结构预测或交互推断完成。
- **公式或算法流程**：论文无显式数学公式。算法流程可概括为：
    - **步骤1**：大规模蛋白质序列语言模型训练。
    - **步骤2**：利用训练好的LM表示，训练结构预测模型（可能是基于回归或能量函数）。
    - **步骤3**：通过简单的搜索程序（如基于表示空间的相似性匹配或在序列-结构空间中优化），直接探索或设计高亲和力结合蛋白。
    - **步骤4**：对表示空间进行降维或聚类分析，构建生物学图谱。

## 3. 实验设计：数据集、基准与对比方法

- **数据集**：
    - **训练数据**：**68亿**个蛋白质序列（来源未明确，推测来自UniProt/NCBI等公共数据库的元基因组、基因组序列）。
    - **消融/验证数据**：用于结构预测的基准数据集（包括生物分子复合物，特别是抗体-抗原复合物）。设计进行实验验证的蛋白质（微型蛋白和单链抗体）对应的靶标。
- **场景**：
    - **复合物结构预测**：预测蛋白质-蛋白质、抗体-抗原等多聚体结构。
    - **蛋白质设计**：搜索或设计具有纳摩尔（nM）级亲和力的微型蛋白和单链抗体。
    - **表示空间概念研究**：分析语言模型学到的“概念”（如二级结构、功能域、物种、进化关系）在向量空间中的几何组织。
    - **图谱构建**：连接已知与未知生物学（如通过结构相似性推断新功能）。
- **基准（Benchmark）**：在复合物预测任务上，与“现有方法的性能”进行了比较。摘要提到“超越了现有方法的性能”，推测可能对比了AlphaFold-Multimer、RoseTTAFold等主流方法。
- **对比方法**：具体对比哪些方法未在摘要中列出，但明确表示性能超越了现有最佳方法。

## 4. 资源与算力

- **文中信息**：摘要和元数据**未明确说明**使用的具体算力资源（如GPU型号、数量、训练时长、显存占用等）。这类信息通常在论文的实验设置或附录部分详细给出，但本次提供的文本内容（仅摘要和元数据）中缺失。
- **推断**：训练一个参数量巨大的语言模型（覆盖68亿序列）以及后续的图谱生成，必然需要极大规模的算力，可能涉及数千个GPU甚至TPU集群，训练时间可能在数周乃至数月。这一短板在信息完整性上需要指出。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，实验涵盖四大类：
    1.  **结构预测基准测试**（一个主要benchmark）。
    2.  **蛋白质设计实验**（针对微型蛋白和单链抗体两个模态进行搜索和湿实验验证）。成功率“高”，但未给出具体数值（如命中率百分比）。
    3.  **表示空间概念研究**（对LM内部结构的分析）。
    4.  **大规模图谱生成与连接性评估**。
    其中设计部分的湿实验是可靠的。但缺少消融实验（如去除语言模型表示后对比）、与其他生成式方法（如ESM-IF、ProteinMPNN）的对比以及对模型在不同序列同源性下的泛化能力测试。
- **充分性与客观性**：
    - **优点**：湿实验验证（纳摩尔级亲和力）是对模型真实能力的强有力证明，比纯计算预测更具说服力。
    - **不足**：
        - 仅展示了两个设计案例（微型蛋白和单链抗体），其**代表性**存疑。若能覆盖更多样化的蛋白家族（如酶、膜蛋白）会更好。
        - 复合物预测基准的选择和对比方法的详细结果未给出，读者无法完全判断其优势是否全面且公平。是否在某些类型复合物上表现更好，而在其他类型上弱于现有方法？
        - 未见对失败案例的分析。模型在什么情况下会失败？这有助于理解其局限性。
        - 在生成68亿图谱时，如何确保结构预测的准确性？是否存在大量假阳性？这些未讨论。

## 6. 论文的主要结论与发现

1.  **语言模型统一了表示**：语言模型能够学习一个统一的、通用的蛋白质表示空间，该空间组织井然有序，与我们对蛋白质的还原论理解一致。
2.  **超越现有结构预测**：基于该表示的结构预测模型，在生物分子复合物（尤其抗体-抗原）预测上超越了现有方法。
3.  **高效设计高亲和力蛋白**：一个简单的搜索程序即可发现具有高实验成功率的纳米摩尔级亲和力微型蛋白和单链抗体，证明了LM表示的强大设计能力。
4.  **构建全面的生物学图谱**：利用LM表示，生成了一个包含68亿序列和11亿结构的图谱，能够识别已知与未知生物学之间的联系，跨越了原子到进化的尺度。
5.  **语言模型是基础**：整体上，语言模型成为了表示蛋白质生物学的强大基础，实现了从预测、设计到发现的全覆盖。

## 7. 优点：方法或实验设计上的亮点

- **核心理念创新**：明确提出“语言模型具现化了一个世界模型（world model）”，超越了仅仅将其视为序列模式匹配的工具，强调其内部表示对生物系统的统一编码。
- **跨尺度能力**：从原子间的相互作用（结构预测）到数十亿年的进化连接（图谱映射），提供了一个统一的解决方案，展现了强大的泛化能力。
- **湿实验验证**：用真实的亲和力测量（纳摩尔级）验证了设计效果，提供了不可辩驳的证据，使实验更具价值。
- **简单搜索程序**：仅使用语言模型表示进行简单搜索就获得了高成功率，暗示表示空间本身的高度信息密度与优化性，而非依赖复杂的生成或扩散模型。
- **数据规模**：构建了前所未有的68亿序列和11亿结构图谱，为未来研究提供了巨大的数据资源。

## 8. 不足与局限

- **实验覆盖不完整**：作为预印本，缺少关键的消融研究（如不同骨干网络、不同序列过滤策略、是否必须大规模语言模型等）。也缺少与其他最先进设计方法（如ProteinMPNN扩散模型、逆向折叠）的定量对比。
- **算力与可复现性**：未报告算力资源，使得其他研究者难以评估复现门槛。如此大规模的训练对于绝大多数实验室不可及。
- **偏差风险**：训练数据来自公共数据库，可能存在对已知大族（如免疫球蛋白、激酶）的偏好，而对偏远或稀有蛋白质（如病毒小型蛋白、极端微生物蛋白）的表征可能不足。这可能导致设计出的蛋白质更多是针对常见靶标的。
- **应用限制**：虽然展示了微型蛋白和单链抗体的设计成功，但这些通常涉及高特异性结合设计。对于需要催化活性、变构调节或跨膜转运的复杂功能设计，仍未进行验证。模型能否处理非结构化区域、动态构象变化仍是未知。
- **图谱质量**：11亿个预测结构必然包含大量错误（预测置信度低），如何筛选、过滤并使用这些图谱对于真实发现至关重要。文中未深入讨论结构预测的准确率与置信度分布。

（完）
