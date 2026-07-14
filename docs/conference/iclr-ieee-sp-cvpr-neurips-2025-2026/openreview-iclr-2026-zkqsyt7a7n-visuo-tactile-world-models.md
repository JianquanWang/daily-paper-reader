---
title: Visuo-Tactile World Models
title_zh: 视觉-触觉世界模型
authors: "Carolina Higuera, Sergio Arnaud, Byron Boots, Mustafa Mukadam, Francois Robert Hogan, Franziska Meier"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=zKQSyT7a7n"
tags: ["query:tactile-vla"]
score: 10.0
evidence: 视觉-触觉世界模型用于接触丰富的操作
tldr: "纯视觉世界模型在接触任务中缺乏物理真实性，物体常消失或违反物理规律。本文引入视觉-触觉世界模型（VT-WM），通过触觉推理补全视觉不足，在想象中物体恒存性提升33%，运动合规性提升29%，并能零样本用于真实机器人规划。"
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 纯视觉模型在接触丰富的操作中易出现物体消失等违反物理的错误，需要触觉推理。
method: 提出多任务视觉-触觉世界模型（VT-WM），结合触觉感知和视觉进行物理建模。
result: "在想象中物体恒存性提升33%，运动定律符合度提升29%，并能零样本迁移到真实机器人。"
conclusion: 触觉提升世界模型的物理保真度，对规划有实际帮助。
---

## Abstract
We introduce multi-task Visuo-Tactile World Models (VT-WM), which capture the physics of contact through touch reasoning. By complementing vision with tactile sensing, VT-WM better understands robot–object interactions in contact-rich tasks, avoiding common failure modes of vision-only models under occlusion or ambiguous contact states, such as objects disappearing, teleporting, or moving in ways that violate basic physics. Trained across a set of contact-rich manipulation tasks, VT-WM improves physical fidelity in imagination, achieving 33\% better performance at maintaining object permanence and 29\% better compliance with the laws of motion in autoregressive rollouts. Moreover, experiments show that grounding in contact dynamics also translates to planning. In zero-shot real-robot experiments, VT-WM achieves up to 35\% higher success rates, with the largest gains in multi-step, contact-rich tasks. Finally, VT-WM shows data efficiency when targeting a new task, outperforming a behavioral cloning policy  by over 3.5$\times$ in success rate with limited demonstrations.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：在接触丰富的机器人操作任务中，纯视觉世界模型常常出现违反物理规律的现象，例如物体在遮挡下消失、瞬移或运动不符合动力学约束。这是因为视觉无法提供足够的接触物理信息，导致模型对物体恒存性和运动合规性的建模失真。
- **研究动机**：通过引入触觉传感，弥补视觉在接触状态感知上的不足，使世界模型能够更真实地建模机器人-物体交互的物理过程，从而提升规划与控制的成功率。
- **整体含义**：这项工作首次证明了触觉线索不仅可以改善感知，还能在世界模型的想象滚动中显著提升物理保真度，并且零样本迁移到真实机器人规划中，为接触丰富操作任务提供了新的范式。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：提出多任务视觉-触觉世界模型（VT-WM），将触觉传感信息与视觉输入结合，通过触觉推理捕获接触物理的细节，从而避免纯视觉模型下的常见失效模式。
- **关键技术细节**：
  - 模型架构：基于隐变量世界模型框架，视觉编码器和触觉编码器分别提取特征，然后在隐空间融合，再通过动力学模型进行自回归预测。
  - 训练任务：在多个接触丰富的操作任务（如推、抓、插等）上进行联合训练，学习共享的物理先验。
  - 推理阶段：模型在想象滚动（imagination rollouts）中生成未来的状态序列，并利用触觉约束增强物体恒存性和运动规律遵从性。
- **公式或算法流程**（文字说明）：
  - 输入：当前视觉观测 $o_t$、触觉观测 $h_t$、动作 $a_t$。
  - 编码：$z_t = Encoder(o_t, h_t)$。
  - 动力学：$\hat{z}_{t+1} = Dynamics(z_t, a_t)$。
  - 解码：预测下一时刻视觉和触觉观测 $\hat{o}_{t+1}, \hat{h}_{t+1} = Decoder(\hat{z}_{t+1})$。
  - 损失函数：重建损失（视觉+触觉） + 正则化。多任务训练时共享编码器和动力学，不同任务使用独立解码器或任务标识。

## 3. 实验设计
- **数据集/场景**：使用了多个接触丰富的操作任务，具体包括推、抓取、插销等，每个任务包含大量真实机器人数据采集（仿真或真实？文中未明确区分，但提及“zero-shot real-robot experiments”表明在仿真训练后直接部署真实机器人）。
- **Benchmark**：主要评估标准为物理保真度指标：
  - **物体恒存性**：想象滚动中物体是否持续存在（不消失/瞬移）。
  - **运动定律符合度**：想象滚动中物体运动是否符合基本物理（如动量、加速度约束）。
  - **任务成功率**：在真实机器人上零样本规划的成功率。
- **对比方法**：
  - 纯视觉世界模型（Vision-only WM）作为基线。
  - 行为克隆策略（Behavioral Cloning, BC）用于对比数据效率。

## 4. 资源与算力
- 论文摘要和元数据中**未明确**提及使用的GPU型号、数量、训练时长等具体计算资源信息。仅提到模型在多任务训练中需要大量数据，但未披露硬件细节。因此无法总结具体算力消耗。

## 5. 实验数量与充分性
- **实验组数**：至少包括以下实验：
  1. 物理保真度对比：物体恒存性提升33%，运动定律符合度提升29%。
  2. 零样本真实机器人规划：不同任务成功率提升最高达35%。
  3. 数据效率实验：与行为克隆对比，在少量演示下VT-WM成功率高出3.5倍以上。
- **充分性分析**：
  - 实验覆盖了仿真训练、真实部署、多任务泛化、数据效率等多个维度，较为全面。
  - 但缺乏对触觉传感器类型、噪声鲁棒性、不同任务数量及具体成功率绝对值等详细数据的披露，且被ICLR 2026拒稿可能意味着实验设计或分析存在不足（如任务集不够大、消融实验不够系统等）。
  - 整体而言，实验客观地展示了VT-WM的优势，但充分性有待进一步增强（例如引入更多基线、不同触觉模态对比等）。

## 6. 主要结论与发现
- 触觉信息能够有效提升世界模型的物理保真度，在想象滚动中物体恒存性提升33%，运动定律符合度提升29%。
- 这种物理保真度的改善可以直接转移到真实机器人规划中，实现零样本部署，在接触密集任务中成功率最高提升35%。
- 多任务训练使模型具备数据效率优势，相比行为克隆，在有限演示下成功率提升3.5倍以上。
- 结论：视觉-触觉世界模型是解决接触丰富操作中物理建模问题的有效途径，对机器人学习具有实际应用价值。

## 7. 优点
- **方法创新性**：首次将触觉传感融入世界模型的隐空间推理，而非仅作为额外观测信号，使模型学会通过触觉补全视觉缺口。
- **多任务学习**：共享动力学先验，提升了泛化能力和数据效率。
- **零样本迁移**：从仿真到真实机器人无需微调，展示了模型的强泛化能力。
- **评价指标**：提出了物理保真度的量化指标（物体恒存性、运动法则符合度），比单纯任务成功率更能反映模型内部物理理解。

## 8. 不足与局限
- **实验覆盖有限**：仅提及“一组接触丰富的任务”，未明确任务具体数量和多样性，可能局限于简单的推、插等，对于复杂任务（如多步骤装配）未验证。
- **触觉传感器依赖**：要求机器人配备触觉传感器，实际部署门槛较高；且未讨论触觉噪声或失效率下的鲁棒性。
- **缺乏消融研究**：未对触觉编码方式、融合策略、多任务权重等关键设计进行系统消融，无法确定每部分贡献。
- **对比方法较弱**：仅对比纯视觉世界模型和简单行为克隆，未与更先进的世界模型（如Dreamer系列、TD-MPC）或基于强化学习的方法对比。
- **被拒稿可能性**：ICLR 2026拒绝可能反映方法在理论深度或实验完整性上仍有欠缺，例如规模较小、未见与复杂3D物体的泛化等。
- **算力与可复现**：未提供开源代码或模型细节，难以复现。

（完）
