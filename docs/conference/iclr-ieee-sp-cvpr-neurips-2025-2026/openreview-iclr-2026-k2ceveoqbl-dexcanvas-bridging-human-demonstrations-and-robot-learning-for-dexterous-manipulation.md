---
title: "DexCanvas: Bridging Human Demonstrations and Robot Learning for Dexterous Manipulation"
title_zh: "DexCanvas: 连接人类演示与机器人学习的灵巧操作数据集"
authors: "Xinyue Xu, Jieqiang Sun, Jing Dai, Siyuan Chen, Lanjie Ma, Ke Sun, Bin Zhao, Jianbo Yuan, Yiwen Lu"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=K2ceVeoqbL"
tags: ["query:tactile-vla"]
score: 4.0
evidence: 接触力数据集，与触觉学习相关
tldr: 灵巧操作数据集缺少物理一致的接触力信息。DexCanvas构建了包含7000小时交互数据的数据集，整合多视角RGB-D、动作捕捉和接触力，并通过真实到仿真强化学习发现接触力，为触觉相关操作研究提供资源。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有的灵巧操作数据集缺乏物理一致的接触力信息。
method: 构建大规模混合真实合成数据集，包含多视角RGB-D、动作捕捉和每帧接触力。
result: 通过真实到仿真的强化学习训练策略，重现人类演示并发现接触力。
conclusion: 该数据集为灵巧操作中的接触力学习提供了基础。
---

## Abstract
We present DexCanvas, a large-scale hybrid real-synthetic human manipulation dataset containing 7,000 hours of dexterous hand-object interactions seeded from 70 hours of real human demonstrations, organized across 21 fundamental manipulation types based on the Cutkosky taxonomy. Each entry combines synchronized multi-view RGB-D, high-precision mocap with MANO hand parameters, and per-frame contact points with physically consistent force profiles. Our real-to-sim pipeline uses reinforcement learning to train policies that control an actuated MANO hand in physics simulation, reproducing human demonstrations while discovering the underlying contact forces that generate the observed object motion. DexCanvas is the first manipulation dataset to combine large-scale real demonstrations, systematic skill coverage based on established taxonomies, and physics-validated contact annotations. The dataset can facilitate research in robotic manipulation learning, contact-rich control, and skill transfer across different hand morphologies.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：现有灵巧操作数据集普遍缺乏**物理一致的接触力信息**；人类演示数据中虽包含丰富的接触交互，但直接测量每帧接触力成本高、噪声大，且难以扩展到大规模数据。
- **整体含义**：接触力是灵巧操作中实现稳定抓握、精细调节和技能迁移的关键物理量，其缺失限制了触觉感知、接触力建模以及不同手型间的技能迁移研究。DexCanvas旨在通过真实仿真混合范式，提供首个大规模、物理验证的接触力标注数据集。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：结合大规模真实人类演示与物理仿真强化学习，由真实动作驱动仿真策略，从而“逆向发现”产生观测物体运动所需的接触力。
- **关键技术细节**：
  - **数据采集**：70小时真实人类演示，多视角RGB-D、高精度动作捕捉（MoCap）配合MANO手部参数，记录每帧接触点。
  - **数据集规模**：通过数据增强和仿真扩展至**7000小时**交互数据，涵盖基于Cutkosky分类法的21种基础操作类型。
  - **真实到仿真管线**：使用强化学习训练策略，控制物理仿真中的**驱动式MANO手**，重现人类演示的运动轨迹，并输出每帧物理一致的接触力剖面。
  - **接触力标注**：仿真中通过物理引擎自动获取接触力，确保与物体运动一致，无需人工标注。
- **公式/算法流程（文字描述）**：
  1. 真实演示 → 提取手部运动（MANO参数）和物体轨迹。
  2. 构建仿真环境（含MANO手和物体）。
  3. RL策略以手部运动为目标，学习关节力矩控制，最小化仿真手与演示手的运动误差。
  4. 训练完成后，从仿真中直接导出每帧接触点力向量。

## 3. 实验设计
- **数据集**：DexCanvas自身（70小时真实 + 7000小时仿真扩展），包含21种操作技能。
- **Benchmark**：未明确提及，但可预期与其他灵巧操作数据集（如DexYCB、TACO、HO-3D等）在接触力质量、技能覆盖、物理一致性方面进行对比。
- **对比方法**：无直接对比实验描述。论文主要贡献是数据集构建与验证，未涉及下游任务对比。

## 4. 资源与算力
- **文中未明确说明**使用了多少GPU、型号、训练时长等算力信息。仅提及“7,000小时交互数据”和“70小时真实演示”，但仿真扩展和RL训练所需算力未报告。可能由于该论文尚处于投稿阶段（ICLR-2026-Public），细节尚未完全公开。

## 5. 实验数量与充分性
- **实验数量**：论文未详细列出组别，主要围绕数据集本身特性进行说明（技能覆盖、接触力物理一致性）。未见消融实验或定量对比试验。
- **充分性**：作为数据集论文，其充分性体现在：
  - 技能分类覆盖21种基础操作（基于成熟分类法），具有系统性。
  - 物理验证通过RL策略重现演示，证明接触力可驱动真实物体运动。
  - 但缺乏与其他数据集的量化比较（如接触力误差、重放成功率、跨手迁移效果），实验设计不够充分。

## 6. 主要结论与发现
- DexCanvas是首个将**大规模真实演示**、**系统化技能分类**和**物理验证接触标注**三者结合的数据集。
- 通过真实到仿真强化学习，能够在不依赖传感器的情况下**逆向发现**接触力，且这些力与物体运动物理一致。
- 数据集有望推动灵巧操作中的**接触力学习**、**接触丰富控制**及**跨手型技能迁移**研究。

## 7. 优点
- **混合数据范式**：结合真实演示的真实性（多样、自然）与仿真的可标注性（自动获得接触力），避免昂贵传感器。
- **技能分类系统性**：基于Cutkosky分类法覆盖21种操作，使得数据集可用于泛化性学习。
- **物理一致性保证**：通过RL重新驱动仿真验证，确保接触力不是简单人工标注，而是物理可行。

## 8. 不足与局限
- **实验覆盖不足**：缺乏与现有数据集的定量对比，未展示在下游任务（如触觉控制、力反馈学习）上的具体效果。
- **偏差风险**：仅使用MANO手模型，未涉及其他手型（如Shadow Hand、Allegro），跨手迁移能力未评估。
- **应用限制**：仿真中获取的接触力可能无法完全反映真实物理接触（如摩擦、变形），真实世界泛化性有待验证。
- **算力资源未公开**：影响可复现性和资源需求评估。

（完）
