---
title: Dynamic cognitive representations in the dorsal pallium of adult zebrafish
title_zh: 成年斑马鱼背侧皮层中的动态认知表征
authors: "Palacios-Flores, K., Eckhardt, J., Huang, K.-H., Narayanan, S., Friedrich, R. W."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.19.726250v3.full.pdf"
tags: ["query:world-models"]
score: 9.0
evidence: 研究斑马鱼背侧大脑皮层中的内在世界模型
tldr: 大脑依赖内部模型解释感知并预测未来。本研究利用双光子成像记录头部固定的成年斑马鱼探索虚拟现实时背侧端脑Dc区神经元活动，发现神经元对特定位置精细调谐且具有对视觉地标的向量编码。群体活动随探索逐步优化，移除地标后部分活动持续并产生预测误差，表明存在内部表征。结果揭示了硬骨鱼大脑通过经验优化预结构化网络形成动态认知地图，为理解非哺乳动物认知机制提供了新证据。
source: biorxiv
selection_source: fresh_fetch
motivation: 探明非哺乳动物（成年斑马鱼）是否通过内部模型形成认知表征，并揭示其神经元编码机制。
method: 在头部固定成年斑马鱼探索结构化虚拟现实时，利用双光子成像记录端脑Dc区神经元活动，分析空间调谐及地标响应。
result: 发现神经元具有位置和向量调谐；群体活动随经验优化；移除地标后部分活动持续并出现预测误差信号。
conclusion: 硬骨鱼大脑通过经验优化预结构化网络形成认知地图，支持认知推断和预测。
---

## 摘要
大脑依赖内部世界模型来解释感官输入并模拟未来。在哺乳动物的海马-内嗅网络中，环境由包含空间选择性神经元（如位置细胞、网格细胞、头方向细胞和物体向量细胞）的认知地图表示。最近在非哺乳动物（包括斑马鱼幼体）中也发现了具有异中心空间调谐的神经元，但这些神经元建立内部认知表征的程度仍不清楚。我们记录了探索新颖且结构丰富的虚拟现实的头部固定成年斑马鱼端脑区Dc的神经元活动。神经元对单个或多个位置有锐利调谐，并共同表征环境空间。活动场表现出神经元特异性的视觉地标关联，表明空间表征中存在显著的向量成分。随着鱼类探索环境，群体活动演变并变得越来越有信息量。当熟悉后移除视觉地标时，与地标相关的活动部分持续存在，且神经元子集报告预测误差，表明活动部分由内部表征驱动。神经元集群间的强功能耦合和胜者全取动力学表明，表征通过预结构化网络的优化而演变。因此，硬骨鱼大脑生成结构化环境的内部模型，这些模型通过经验优化并实现认知推理和预测。

## Abstract
Brains rely on internal models of the world to interpret sensory input and to simulate the future. In the mammalian hippocampal-entorhinal network, environments are represented by cognitive maps that contain spatially selective neurons such as place, grid, head direction and object-vector cells. Neurons with allocentric spatial tuning have recently been discovered also in non-mammalian organisms including larval zebrafish but it remains unclear to what extent these neurons establish internal cognitive representations. We measured neuronal activity in telencephalic area Dc of head-fixed adult zebrafish exploring a novel, richly structured virtual reality. Neurons were sharply tuned to one or multiple locations and collectively represented environmental space. Activity fields exhibited neuron-specific associations to visual landmarks, indicating a prominent vectorial component in spatial representations. Population activity evolved and became increasingly informative as fish explored the environment. When landmarks were removed after familiarization, landmark-associated activity partially persisted and subsets of neurons reported prediction errors, implying that activity was in part driven by an internal representation. Strong functional coupling among neuronal ensembles and winner-take-all dynamics suggest that representations evolve by refinements of pre-structured networks. The teleost brain therefore generates internal models of structured environments that are optimized by experience and enable cognitive inference and prediction.

---

## 论文详细总结（自动生成）

# 论文结构化总结：Dynamic cognitive representations in the dorsal pallium of adult zebrafish

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：非哺乳动物（硬骨鱼）的大脑是否能够建立内部的世界模型（认知地图），并基于此模型进行认知推理和预测？
- **背景**：哺乳动物海马-内嗅网络中的认知地图已得到广泛研究，包含位置细胞、网格细胞、头方向细胞、物体向量细胞等。最近在非哺乳动物（如幼年斑马鱼）中也发现了具有异中心空间调谐的神经元，但尚不清楚这些神经元是否真正建立了内部认知表征，是否能支持记忆检索、预测等高级认知功能。
- **整体含义**：该研究旨在探索成年斑马鱼端脑Dc区的神经元是否形成动态的、经验可塑的认知地图，并验证其能否在没有直接感觉输入时维持内部表征并生成预测误差信号，从而证明认知功能的进化保守性。

## 2. 论文提出的方法论

### 核心思想
利用头部固定的成年斑马鱼在封闭环路虚拟现实（VR）中探索具有自然纹理和视觉地标的走廊，通过双光子钙成像记录端脑Dc区（cDc）神经元活动，分析其空间调谐特性、与地标的关系、随时间演变的动态，以及在地标移除后是否表现出持续活动和预测误差。

### 关键技术细节
- **动物模型**：成年（6–18月龄）转基因斑马鱼Tg(neuroD:GCaMP6f)，nacre背景。
- **头部固定**：通过手术将定制不锈钢头钉固定在颅骨上，置于透明半六边形水箱中。
- **虚拟现实系统**：三个投影仪在鱼缸三面投影45°×60°视场（共45°×180°），使用Panda3D游戏引擎更新VR场景，基于鱼尾运动（50Hz追踪）推断前进速度并实时更新VR位置，限制只向前运动，每次遍历后重置到起点（一个trial）。
- **钙成像**：2光子显微镜（8kHz共振扫描，30fps），激发波长920nm，使用时间门控避免VR光污染。记录15–30分钟成像session。
- **cDc区域定位**：基于解剖标志（ypsilonformis沟和parvalbumin表达边界）可靠识别。
- **神经元ROI检测**：训练STARDIST模型预测细胞体，手动校对。
- **活动分析**：ΔF/F₀计算，空间分箱（10 VR units/bin），低通滤波，峰值检测，使用空间特异性（s = I/λ̄）筛选，其中空间信息：
  $$I = \sum_x \lambda(x) \log_2 \frac{\lambda(x)}{\bar{\lambda}} P(x)$$
  其中$\lambda(x)$为空间bin x的平均活动，$\bar{\lambda}$为平均活动，$P(x)$为鱼在该bin的概率。显著性通过circular shuffle（100次）判定（z-score≥3）。
- **活动场定义**：峰值标准化幅度≥5，且在≥20% trial中峰值幅度≥7，半高宽内。
- **多session匹配**：通过弹性配准（bUnwarpJ）映射相同神经元。

### 算法流程（文字描述）
1. 原始时间序列 → ΔF/F₀ → 按trial分箱 → 空间活动图（trial×空间bin）
2. 空间平滑 → 检测所有候选峰 → 计算空间特异性 → 筛选显著神经元
3. 每峰：确定半高宽、峰值幅度 → 跨trial检验（≥20% trial含有显著峰） → 定义为活动场
4. 解码：4层前馈神经网络（输入层：神经元数；隐藏层：64、24；输出层：1），训练60% trial，测试40%，使用皮尔逊相关和绝对误差评估。
5. 噪声相关：每个trial中每场活动的信号幅度，计算两两trial间相关（Pearson），保留空间bin内活动。
6. 地标删除分析：将删除前后活动分别平均，检测持续活动段（≥5连续bin，标准化≥12）和误差信号（删除期间平均活动/删除前≥2）。

## 3. 实验设计

- **数据集/场景**：
  - 四种虚拟走廊：
    - 7Reg：7个规则间隔地标（2条鱼）
    - 5Reg：5个规则间隔地标（4条鱼）
    - 5Irr：5个不规则间隔地标（6条鱼）
    - 0Lm：无地标（2条鱼）
  - 地标删除实验：2条鱼，先熟悉20分钟（~20 trials），然后在后续session中临时删除地标5个连续trial，共7次删除事件。
  - 演变实验：4条鱼记录两个成像session（间隔40–147分钟，32–174 trials）。
- **Benchmark**：自身对照：shuffle活动（circular permutation）用于空间信息显著性检验和噪声相关；mock deletion（无地标删除）用于比较地标删除效应。
- **对比方法**：未与其他模型或方法进行系统对比，主要依赖于统计检验和对照。

## 4. 资源与算力

文中未明确说明使用的GPU型号、数量或训练时长。仅提及使用Python PyTorch训练4层前馈神经网络进行位置解码，训练200 epochs。未提及具体计算资源（如GPU小时数）。因此，**未提供详细算力信息**。

## 5. 实验数量与充分性

- **实验数量**：
  - 空间调谐分析：10条鱼（有地标），2条鱼（无地标）。
  - 演变实验：4条鱼，每鱼2个session。
  - 地标删除实验：2条鱼，共7次删除事件，643个神经元（删除组），2438个神经元（mock组）。
  - 每个鱼平均320±53个神经元，总计3311个神经元（有地标）。
- **统计充分性**：
  - 使用Wilcoxon秩和检验、Kolmogorov-Smirnov检验、卡方检验等，检验水平合适。
  - 控制条件（shuffle、mock deletion、spatial randomization）充分。
  - 解码使用subsampling平衡神经元数量，重复100次。
  - 但样本量较小（每环境类型仅2–6条鱼），地标删除仅2条鱼，可能引入个体差异。不过考虑到成年斑马鱼头部固定实验的技术难度，仍属合理范围；实验设计客观，结果统计显著。

## 6. 论文的主要结论与发现

1. **cDc神经元具有空间选择性**：14%的神经元表现出稳定的空间活动场（单场或多场），显著高于无地标环境（3%）。空间特异性显著高于时间特异性。
2. **地标向量编码**：活动场与地标距离一致且在不同场之间稳定性高，表明神经元编码绝对距离（而非相位），类似于哺乳动物内嗅皮层的物体向量细胞。
3. **群体覆盖均匀**：多神经元的活动场几乎均匀分布整个走廊，呈现随机覆盖模式。
4. **表征动态优化**：随经验（分钟到小时），神经元选择性提高（多场减少，单场增加），去编码精度提升。部分神经元场出现或消失，显示预结构化网络经验依赖加固。
5. **内部模型与预测误差**：地标删除后，部分空间活动持续存在（18% vs. 随机8%），且有2.7%的删除事件触发高强度广泛活动（误差信号），表明神经元依赖内部模型进行预测和比较。
6. **功能集群与胜者全取动力学**：神经元间存在强正/负噪声相关，形成功能集群（同区或近区），且集群间活动互斥，暗示抑制性相互作用和预配置网络结构。

## 7. 优点

- **方法创新**：首次在**成年斑马鱼**中使用高分辨率封闭环VR结合双光子成像，记录深层端脑区域（cDc）的空间表征。
- **多维度分析**：从单神经元调谐、群体覆盖、时间演变、地标操纵、噪声相关等多角度验证内部模型的存在。
- **严谨的检测流程**：多步空间场检测（空间信息筛选、trial-by-trial检验）降低了假阳性。
- **明确的地标操纵实验**：直接通过地标删除检验内部表征保留和预测误差，提供了因果证据。
- **生物学意义**：揭示了硬骨鱼大脑也存在与哺乳动物相似的认知地图，支持**认知功能的进化保守性**，为理解脊椎动物认知的神经基础提供新视角。

## 8. 不足与局限

- **样本量较小**：每实验条件仅2–6条鱼，地标删除仅2条鱼，个体差异可能影响结论的推广性。
- **区域特异性**：仅记录cDc一个亚区，未探索其他端脑区域（如Dl、Dm）是否参与空间表征或不同功能。
- **运动限制**：鱼只能向前游泳，无法测试转身或二维导航，无法完全展示异中心空间调谐的复杂性。
- **时间分辨率**：钙成像（30 Hz）限制了捕捉快速神经活动的能力，可能遗漏场出现/消失的瞬时动态。
- **行为任务缺失**：未设计需要预测或记忆的行为任务，仅通过神经活动推断内部表征，缺乏直接的认知行为证据。
- **地标删除实验设计局限**：删除仅持续5 trial，且仅2条鱼，无法排除短期适应或非特异性突发活动；误差信号检测阈值相对主观（2倍基线）。
- **缺乏与哺乳动物的直接比较**：虽然与海马/内嗅网络相似，但未在同一实验框架下对比，系统发育关系仍需更多验证。

（完）
