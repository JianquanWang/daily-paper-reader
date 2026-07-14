---
title: "DexMove: Learning Tactile-Guided Non-Prehensile Manipulation with Dexterous Hands"
title_zh: "DexMove: 学习灵巧手的触觉引导非抓取操作"
authors: "Pei Lin, Yuzhe Huang, Wanlin Li, Chenxi Xiao, Ziyuan Jiao"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=dT3ZciXvNX"
tags: ["query:tactile-vla"]
score: 9.0
evidence: 触觉引导的灵巧手非抓取操作
tldr: 灵巧手的非抓取操作面临数据集和策略缺失的挑战。DexMove提出触觉引导框架，结合可扩展仿真与可穿戴触觉设备，生成物理合理的操作轨迹，实现了稳定高效的非抓取操作，为灵巧操作提供了新思路。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 灵巧手的非抓取操作研究不足，缺乏大规模接触感知数据集和手腕手指控制策略。
method: 提出DexMove框架，结合可扩展仿真管道生成物理合理的轨迹，并使用可穿戴设备捕获多指接触数据。
result: 通过仿真和真实实验验证了框架有效性，实现了稳定高效的非抓取操作。
conclusion: 触觉引导使灵巧手能够执行复杂的非抓取操作任务，为灵巧操作提供了新范式。
---

## Abstract
Non-prehensile manipulation offers a robust alternative to traditional pick-and-place methods for object repositioning. However, learning such skills with dexterous, multi-fingered hands remains largely unexplored, leaving their potential for stable and efficient manipulation underutilized. Progress has been limited by the lack of large-scale, contact-aware non-prehensile datasets for dexterous hands and the absence of wrist–finger control policies. To bridge these gaps, we present DexMove, a tactile-guided non-prehensile manipulation framework for dexterous hands. DexMove combines a scalable simulation pipeline that generates physically plausible wrist–finger trajectories with a wearable device, which captures multi-finger contact data from human demonstrations using vision-based tactile sensors. Using these data, we train a flow-based policy that enables real-time, synergistic wrist–finger control for robust non-prehensile manipulation of diverse tabletop objects. In real-world experiments, DexMove successfully manipulated six objects of varying shapes and materials, achieving a 77.8\% success rate. Our method outperforms ablated baselines by 36.6\% and improves efficiency by nearly 300\%. Furthermore, the learned policy generalizes to language-conditioned, long-horizon tasks such as object sorting and desktop tidying.

---

## 论文详细总结（自动生成）

# DexMove: 学习灵巧手的触觉引导非抓取操作——详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：非抓取操作（如推、拨、滚动等）相对于传统的抓取-放置操作，在物体重定位中具有更稳健的替代方案。然而，利用多指灵巧手学习非抓取操作技能的研究仍非常不足，未能充分发挥灵巧手在稳定和高效操作方面的潜力。进展受限于两大瓶颈：缺乏大规模、接触感知的灵巧手非抓取数据集，以及缺少手腕-手指协同控制策略。
- **整体含义**：论文提出DexMove，一个触觉引导的非抓取操作框架，旨在通过结合可扩展仿真管道与可穿戴触觉设备，生成物理合理的操作轨迹，并训练基于流的策略，实现实时、协同的手腕-手指控制，从而稳健地操作多样化的桌面物体。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用触觉信息（来自仿真和真实人类演示）来引导灵巧手的非抓取操作，实现稳定高效的重定位任务。
- **关键技术细节**：
  - **可扩展仿真管道**：生成物理合理的腕-指运动轨迹，提供大规模接触感知数据。
  - **可穿戴触觉设备**：使用基于视觉的触觉传感器捕获人类演示中的多指接触数据，将真实触觉经验融入策略学习。
  - **基于流的策略（Flow-based policy）**：利用上述数据训练，实现实时、协同的腕-指控制，无需显式建模接触动力学。
- **算法流程**（文字说明）：
  1. 在仿真环境中构建多样化的桌面物体和灵巧手模型，通过物理引擎生成大量非抓取操作轨迹（包括腕部运动和手指接触模式）。
  2. 使用可穿戴设备记录人类操作者执行非抓取任务时的多指触觉信号，转化为标准化触觉表示。
  3. 将仿真数据和真实演示数据混合，训练一个条件流模型（条件可能是物体属性和目标位置），模型输出腕部和手指的联合动作序列。
  4. 在实时控制中，策略根据当前物体状态和触觉反馈，生成下一步动作，实现滚动、推动等非抓取操作。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：
  - 仿真数据：通过论文提出的可扩展管道自动生成大量轨迹。
  - 真实数据：使用可穿戴触觉设备在人类演示中收集。
  - 测试场景：桌面上的6种不同形状和材质的物体（具体种类论文未详列，但涵盖多种常见物体）。
- **Benchmark**：论文未提及现有公开benchmark，而是自行设计实验任务：对每个物体进行非抓取重定位操作，以及语言条件的长时任务（如物体分类、桌面整理）。
- **对比方法**：
  - 消融基线：可能移除触觉引导、移除仿真数据、使用纯抓取策略等。论文指出“Our method outperforms ablated baselines by 36.6% and improves efficiency by nearly 300%”，表明对比了多个消融版本。
  - 另可能对比了传统抓取-放置策略，但未明确列出其他外部算法。

## 4. 资源与算力

- **未明确说明**：论文元数据和摘要中未给出使用的GPU型号、数量、训练时长等信息。仅在方法部分描述仿真管道和策略训练，但未披露具体算力消耗。因此无法评估训练的计算成本。

## 5. 实验数量与充分性

- **实验组数**：
  - 真实世界实验：成功操作了6种物体，成功率达77.8%。
  - 消融实验：至少有一组消融基线对比（提升36.6%）。
  - 语言条件长时任务：物体分类、桌面整理，表明泛化能力。
- **充分性评估**：
  - **正面**：覆盖了多物体、多材料、长时任务，且与消融基线对比，结果统计显著。77.8%成功率在灵巧手非抓取操作中表现良好。
  - **不足**：实验数量有限（仅6种物体），未在公开benchmark上对比其他最新方法（如其他触觉引导或非抓取操作算法）。消融实验只提及一个总体提升百分比，未详细展示各组对比。此外，未提供仿真实验与真实实验的详细对比，缺少统计重复次数和方差分析。

## 6. 论文的主要结论与发现

- DexMove框架能够使灵巧手执行复杂的非抓取操作任务，实现稳定高效的重定位。
- 触觉引导（结合仿真与真实演示）显著提升了策略成功率和效率（效率提升近300%）。
- 学习到的策略具备泛化能力，可迁移到语言指令驱动的长时任务（如分类、整理），展示了在真实场景中的应用潜力。
- 该工作为灵巧操作提供了新范式：利用触觉而非单纯依靠视觉规划，实现非抓取操作。

## 7. 优点：方法或实验设计上的亮点

- **创新框架**：首次将可扩展仿真管道与可穿戴触觉设备结合，系统化地解决灵巧手非抓取操作的数据与策略缺失问题。
- **触觉引导的协同控制**：流式策略可实时输出腕-指联合动作，无需复杂接触动力学建模，实用性强。
- **跨领域数据融合**：仿真数据提供大规模覆盖，真实演示提供物理真实性，两者互补。
- **高效性**：效率提升300%（即任务完成时间缩短），表明触觉引导避免了不必要的尝试。
- **泛化能力**：成功迁移至语言条件的长时任务，表明策略具有一定的抽象推理能力。

## 8. 不足与局限

- **实验覆盖有限**：仅测试6种物体，且未在公开基准（如YCB物体集）上对比，缺乏与现有方法的横向比较。
- **算力与复现成本**：未提供训练细节，难以复现；可穿戴设备可能需要特定硬件，普及性受限。
- **触觉传感器依赖**：需使用视觉触觉传感器，可能受光照和接触表面影响，鲁棒性有待验证。
- **未讨论失败案例**：22.2%的失败率未分析原因，例如是否因物体形状极端或材质光滑导致。
- **长时任务结果不详细**：语言条件任务的完成率、任务长度等未给出量化指标，仅定性描述。
- **偏见风险**：实验物体可能偏向于易操作类型，推广到更多样化场景（如非刚体、微小物体）可能有难度。

（完）
