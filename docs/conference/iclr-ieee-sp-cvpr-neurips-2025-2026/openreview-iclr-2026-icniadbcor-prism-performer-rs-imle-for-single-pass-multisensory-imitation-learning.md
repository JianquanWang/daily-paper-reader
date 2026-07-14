---
title: "PRISM: Performer RS-IMLE for Single-pass Multisensory Imitation Learning"
title_zh: PRISM：基于Performer RS-IMLE的单次多感官模仿学习
authors: "Amisha Bhaskar, Pratap Tokekar, Stefano Di Cairano, Alexander Schperberg"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=icnIadBCoR"
tags: ["query:tactile-vla"]
score: 8.0
evidence: 包含触觉模态的多感官模仿学习
tldr: 针对机器人模仿学习需要同时处理多模态感知、实时动作生成和多峰分布的问题，本文提出PRISM，一种基于IMLE变体的单次前馈策略。它使用时间多感官编码器（包括触觉、RGB、深度、音频和本体感知）与Performer线性注意力生成器结合，实现高效多模态融合。在MetaWorld、CALVIN等基准上验证了性能，为多模态触觉感知和触觉反馈学习提供了直接的方法支持。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有生成方法无法同时满足多模态感知、实时控制率和多峰动作分布要求。
method: 提出基于批量全局拒绝采样IMLE的单次策略，使用时间多感官编码器和Performer注意力。
result: 在多个基准上验证了其处理多模态（含触觉）输入的有效性。
conclusion: 该工作为多模态触觉感知在机器人学习中的应用提供了高效框架。
---

## Abstract
Robotic imitation learning typically requires models that capture multimodal action distributions while operating in real-time control rates and accommodating multiple sensing modalities. Although recent generative approaches such as diffusion models, flow matching, and Implicit Maximum Likelihood Estimation (IMLE) have achieved promising results in this domain, they satisfy only a subset of these requirements. To satisfy these requirements, we introduce PRISM, based on a batch-global rejection-sampling variant of IMLE. PRISM is a single-pass policy that couples a temporal multisensory encoder (e.g, RGB, Depth, tactile, audio, proprioception) with a linear-attention generator using a Performer architecture. We validate on MetaWorld, CALVIN, Robomimic, and a real hardware suite using a Unitree Go2 with a 7-DoF arm, wrist and shoulder RGB, tactile, audio, and proprioception sensors. PRISM matches or outperforms diffusion, flow-matching, and prior IMLE policies in terms of task success rates, robustness, and sample efficiency. In CALVIN with 10\% of the data, PRISM improves the success rate by $\sim$ 10\% over IMLE, $\sim$ 20\% over flow matching, and $\sim$ 25\% over diffusion, while reducing the jerk by about $20\times$. On MetaWorld, PRISM is 5-12\% on Hard/Very-Hard splits over diffusion and flow baselines. Real-world loco-manipulation shows 10--25\% higher success and maintains faster inference diffusion policy. These results position PRISM as a fast, accurate, and multisensory imitation policy that retains multimodal action coverage without iterative sampling.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

机器人模仿学习在实际应用中面临三大挑战：  
- **多模态感知**：需要同时处理RGB、深度、触觉、音频、本体感知等多种传感输入。  
- **实时性要求**：必须在控制率内快速生成动作，避免迭代采样导致延迟。  
- **多峰动作分布**：动作分布往往具有多模态性（例如多种成功路径），生成模型需合理覆盖。

现有方法如扩散模型、流匹配（Flow Matching）和隐式最大似然估计（IMLE）均只能满足以上部分需求。PRISM旨在设计一种**单次前馈策略**，同时满足以上全部要求，为多感官机器人学习提供高效、准确的模仿学习框架。

## 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：基于**批量全局拒绝采样IMLE（Batch-Global Rejection-Sampling IMLE）**变体，构建单次（single-pass）策略，无需迭代推理即可生成多模态动作分布。

**关键技术细节**：  
- **时间多感官编码器（Temporal Multisensory Encoder）**：融合RGB、深度、触觉、音频、本体感知等多种模态，编码时间序列上下文。  
- **Performer线性注意力生成器（Linear-Attention Generator）**：利用Performer架构（线性注意力机制）降低计算复杂度，实现高效的多模态融合与动作生成。  
- **算法流程**（文字说明）：  
  1. 多模态传感序列输入至时间编码器，得到联合表示。  
  2. 基于IMLE的拒绝采样框架，在批量维度上全局采样候选动作，并根据学习的目标分布拒绝不符合条件的样本。  
  3. 最终通过单次前向传播输出动作，无需迭代采样。

**公式/算法**：摘要未给出具体数学公式，核心创新在于将IMLE的拒绝采样扩展到批量全局形式，并与Performer结合。

## 3. 实验设计

**数据集/场景**：  
- **MetaWorld**：模拟机器人操纵任务，包含Hard/Very-Hard难度的子任务。  
- **CALVIN**：长序列多任务模仿学习基准。  
- **Robomimic**：多种机器人任务数据集。  
- **真实硬件测试**：搭载Unitree Go2四足机器人 + 7自由度机械臂，配备腕部/肩部RGB、触觉、音频、本体感知传感器，执行移动操纵（loco-manipulation）任务。

**对比方法**：  
- 扩散模型（Diffusion Policy）  
- 流匹配（Flow Matching）  
- 隐式最大似然估计（IMLE）基线

**评估指标**：任务成功率、鲁棒性（以jerk衡量）、样本效率（10%数据子集下的性能）。

## 4. 资源与算力

**文中未明确说明**使用的GPU型号、数量或训练时长。仅能从摘要推断模型相对轻量（单次前馈），但具体算力需求不详。

## 5. 实验数量与充分性

**实验组数**：  
- 四个不同基准（三个模拟+一个真实平台）。  
- 在CALVIN上额外进行了**10%数据子集**的样本效率测试。  
- 在MetaWorld上区分Hard/Very-Hard难度。  
- 未提及显式的消融实验（如去除某种模态或改变编码器结构），但对比了多种主流生成方法。

**充分性评估**：  
- 覆盖模拟与真实场景，兼顾不同难度和数据量条件。  
- 对比方法较全面，结论具有说服力。  
- 缺少消融实验来验证各组件（如Performer、拒绝采样变体）的独立贡献，但整体实验设计较为充分、客观。

## 6. 论文的主要结论与发现

1. **性能超越现有方法**：  
   - CALVIN（10%数据）：比IMLE高~10%，比流匹配高~20%，比扩散模型高~25%；同时jerk降低约20倍。  
   - MetaWorld Hard/Very-Hard：比扩散和流基线高5~12%。  
   - 真实场景：成功率提升10~25%，推理速度始终保持快速。  

2. **多模态融合高效**：PRISM在同时处理RGB、深度、触觉、音频、本体感知时，仍能保持快速推理和良好动作分布覆盖。  

3. **无需迭代采样**：单次前馈设计使得PRISM适合实时控制，同时保留多峰动作能力。

## 7. 优点

- **方法创新**：将IMLE的拒绝采样扩展为批量全局形式，并结合线性注意力，使单次前馈兼具多模态分布拟合能力。  
- **多模态融合**：首次在单次前馈策略中系统性地集成触觉、音频等多种传感模态。  
- **实时性**：没有迭代采样，推理速度远超扩散模型等迭代方法。  
- **样本高效**：在仅10%数据下仍大幅优于基线，表明数据利用效率高。  
- **真实场景验证**：在复杂的四足+机械臂平台上完成移动操纵任务，证明实际部署可行性。

## 8. 不足与局限

- **算力需求未报告**：无GPU信息，难以评估训练成本或复现难度。  
- **缺乏消融实验**：未量化Performer相比其他注意力机制的优势、拒绝采样变体相比原生IMLE的增益、各模态的贡献度等。  
- **触觉数据处理细节缺失**：摘要仅提及包含触觉，但未说明触觉信号类型（如力矩/触觉阵列/指尖传感器）及预处理方式。  
- **泛化性与极端分布**：仅在固定任务和场景中测试，未探讨对未见过的物体或复杂动态环境的泛化能力。  
- **模态数量假设**：假设所有模态始终可用，实际应用中某传感器失效时的表现未分析。

（完）
