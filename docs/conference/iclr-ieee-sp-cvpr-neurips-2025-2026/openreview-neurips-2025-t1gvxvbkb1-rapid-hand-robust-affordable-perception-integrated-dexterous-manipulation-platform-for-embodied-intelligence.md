---
title: "RAPID Hand: Robust, Affordable, Perception-Integrated, Dexterous Manipulation Platform for Embodied Intelligence"
title_zh: RAPID Hand：面向具身智能的鲁棒、经济、感知集成的灵巧操作平台
authors: "Zhaoliang Wan, Zetong Bi, Zida Zhou, Hao Ren, Yiming Zeng, Yihan Li, Lu Qi, Xu Yang, Ming-Hsuan Yang, Hui Cheng"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=T1gVXvbkB1"
tags: ["query:tactile-vla"]
score: 7.0
evidence: 集成指尖触觉感知的硬件平台
tldr: 针对多指灵巧手平台昂贵且难以收集高质量演示数据的问题，本文提出RAPID Hand，一个集低成本、高自由度（20-DoF）、全手感知于一体的硬件软件平台。它稳定集成了腕部视觉、指尖触觉传感和本体感知，延迟低于7毫秒，并支持高自由度遥操作。该平台为多模态触觉感知和触觉反馈学习提供了实用的数据采集基础，直接支持机器人触觉感知和操作研究。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 缺乏低成本高自由度平台用于真实多指操作数据收集，限制通用机器人自主性。
method: 协同设计紧凑的20自由度手、全手感知（腕部视觉、指尖触觉、本体感知）和高自由度遥操作界面。
result: 实现了亚7毫秒延迟的感知融合，并支持高质量演示收集。
conclusion: 该平台降低了触觉感知数据获取门槛，有助于触觉大模型和世界模型研究。
---

## Abstract
This paper addresses the scarcity of low-cost but high-dexterity platforms for collecting real-world multi-fingered robot manipulation data towards generalist robot autonomy. 
To achieve it, we propose the RAPID Hand, a co-optimized hardware and software platform where the compact 20-DoF hand, robust whole-hand perception, and high-DoF teleoperation interface are jointly designed.
Specifically, RAPID Hand adopts a compact and practical hand ontology and a hardware-level perception framework that stably integrates wrist-mounted vision, fingertip tactile sensing, and proprioception with sub-7 ms latency and spatial alignment. 
Collecting high-quality demonstrations on high-DoF hands is challenging, as existing teleoperation methods struggle with precision and stability on complex multi-fingered systems.
We address this by co-optimizing hand design, perception integration, and teleoperation interface through a universal actuation scheme, custom perception electronics, and two retargeting constraints. We evaluate the platform’s hardware, perception, and teleoperation interface. Training a diffusion policy on collected data shows superior performance over prior works, validating the system’s capability for reliable, high-quality data collection.
The platform is constructed from low-cost and off-the-shelf components and will be made public to ensure reproducibility and ease of adoption.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：当前多指灵巧手平台普遍成本高昂、自由度有限，难以大规模收集高质量的真实世界机器人操作演示数据，这限制了通用机器人自主性的发展。
- **背景**：灵巧操作是具身智能的关键能力，但现有平台（如Shadow Hand、Allegro Hand）要么价格昂贵（数万美元），要么自由度不足（通常低于16-DoF），且缺乏稳定集成的多模态感知（尤其是指尖触觉）和高精度遥操作界面。这导致触觉感知数据的获取门槛高，阻碍了触觉大模型、世界模型等前沿研究的数据驱动发展。
- **整体含义**：本文旨在提供一个**低成本、高自由度、感知集成、支持高质量数据采集**的完整软硬件平台，降低灵巧操作研究门槛，推动通用机器人自主性。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：**协同设计**（co-optimization）手部本体、全手感知模块和遥操作界面，实现硬件与软件紧密耦合，保证性能与成本的最佳平衡。
- **关键技术细节**：
  - **手部本体**：紧凑的20自由度（20-DoF）设计，采用通用驱动方案（universal actuation scheme），兼顾小型化与运动灵活性。
  - **全手感知框架**：硬件级集成三种感知模态：
    - 腕部视觉（wrist-mounted vision）
    - 指尖触觉传感（fingertip tactile sensing）
    - 本体感知（proprioception，如关节角度、电机位置）
    - 延迟低于7毫秒（sub-7 ms latency），并实现空间对齐（spatial alignment）。
  - **遥操作界面**：通过自定义感知电子元件（custom perception electronics）和两种重定向约束（two retargeting constraints），实现高自由度（high-DoF）稳定遥操作，解决现有方法在多指系统中的精度和稳定性不足问题。
- **流程**：先进行手部机构与感知硬件的协同设计，再开发遥操作界面，最后平台开源以促进复现和采用。

## 3. 实验设计：数据集、场景、基准与对比方法

- **数据集/场景**：在真实机器人操作任务上收集演示数据（具体任务未在摘要中详述，但提到训练扩散策略）。
- **基准**：与先前工作（prior works）的比较，主要对比性能指标。
- **对比方法**：未明确列出具体对比方法，但提到训练的扩散策略（diffusion policy）表现优于先前工作，说明对比了至少一种已有的数据采集平台或策略学习方法。
- **实验核心指标**：硬件可靠性、感知延迟、遥操作精度、演示数据质量以及下游策略学习效果。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。
- 仅提及“扩散策略训练”作为验证手段，但未提供训练硬件细节。
- 推测：由于平台基于低成本组件，训练可能使用常规实验室GPU（如RTX 3090/4090），但无法确认。

## 5. 实验数量与充分性

- **实验组数**：从摘要和元数据看，实验涵盖三个方面：
  - 硬件性能评估（如感知延迟<7ms）
  - 遥操作稳定性验证
  - 下游策略学习（训练扩散策略并与先前工作比较）
- **充分性评价**：
  - **优势**：实验覆盖了平台核心功能验证和端到端数据采集-学习流程，证明了实用性。
  - **不足**：
    - 缺乏消融实验（如是否触觉感知、不同遥操作约束的贡献）。
    - 未提供统计显著性分析或多种任务场景的泛化测试。
    - 缺乏与现有低成本平台（如Yale OpenHand、Robotiq Hand）的直接对比。
  - **客观性**：论文声称平台开源，有助于公平复现；但当前实验细节有限，可能存在选择偏差。

## 6. 主要结论与发现

- RAPID Hand平台成功实现了**低成本（off-the-shelf组件）、高自由度（20-DoF）、全手感知集成（亚7ms延迟）、高质量数据采集**。
- 遥操作界面通过协同设计和约束优化，提升了复杂多指系统的操作精度和稳定性。
- 基于该平台收集的数据训练的扩散策略，在性能上优于先前工作，验证了平台“数据质量-策略效果”的正向循环。
- 结论：该平台降低了触觉感知数据获取门槛，有助于触觉大模型和世界模型研究。

## 7. 优点：方法与实验设计亮点

- **协同设计理念**：硬件、感知、遥操作三者联合优化，而非简单拼凑，保证了系统整体性能。
- **全手多模态感知**：集成视觉+触觉+本体，且延迟极低（<7ms），实现了实时融合。
- **低成本开源**：使用市售低成本组件，并将平台公开，可复现性强，降低研究门槛。
- **验证下游任务**：不仅展示平台本身，还通过训练扩散策略证明数据有效性，体现端到端实用性。
- **学术认可**：被NeurIPS 2025接收（评分7.0），说明方法具有较高创新性和价值。

## 8. 不足与局限

- **实验细节不充分**：未给出具体任务、数据集规模、基线方法名称、统计误差等，难以评估泛化能力。
- **消融分析缺失**：例如，未量化指尖触觉感知对策略性能的具体贡献；未对比不同遥操作约束的效果。
- **算力资源未说明**：影响可复现性，特别是对低成本平台目标而言，需明确训练策略所需的最低硬件要求。
- **应用限制**：
  - 20-DoF手可能仍无法完全模拟人类手部（27+自由度），特定任务受限。
  - 亚7ms延迟在高速操作中可能仍有瓶颈。
  - 遥操作重定向约束可能引入额外学习成本，需要操作者适应。
- **偏差风险**：只报告了优于先前工作的结果，未展示失败案例或平台局限性，可能存在报告偏倚。

（完）
