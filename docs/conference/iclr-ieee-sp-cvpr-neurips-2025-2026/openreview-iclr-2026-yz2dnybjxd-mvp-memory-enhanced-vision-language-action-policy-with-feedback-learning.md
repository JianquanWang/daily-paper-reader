---
title: "MVP: Memory-enhanced Vision-Language-Action Policy with Feedback Learning"
title_zh: MVP：具有反馈学习的记忆增强视觉-语言-动作策略
authors: "Chubin Zhang, Yansong Tang, Wenkai Guo, Guanxing Lu, Yi Su, Haoji Zhang, Xiuwei Xu, Linqing Zhao, Ziwei Wang, Jiwen Lu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Yz2DnYBJXd"
tags: ["query:tactile-vla"]
score: 4.0
evidence: 具有记忆和反馈的VLA模型，与复合需求相关
tldr: 现有VLA模型遵循马尔可夫假设，难以处理时间上延续的任务和从反馈中学习。本文提出非马尔可夫VLA模型MVP，利用情景记忆存储历史动作和视觉观察，并设计紧凑记忆表示，支持从反馈中学习，提升了长时任务性能，但未涉及触觉，仅从VLA框架上与复合主题间接关联。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有VLA模型缺乏对历史信息的利用，无法从反馈中学习。
method: 提出非马尔可夫VLA模型，引入情景记忆和紧凑表示，支持反馈学习。
result: 在时间扩展任务上表现优于马尔可夫基线，能从反馈中改进动作。
conclusion: 记忆增强和反馈学习显著提升了VLA模型在长时任务中的表现。
---

## Abstract
Recent advances in Vision-Language-Action (VLA) models have enabled robots to perform a wide range of manipulation tasks conditioned on language instructions, offering strong generalization across tasks, objects, and environments. However, most existing VLAs operate under a Markov assumption, limiting their ability to handle temporally extended tasks and learn from feedback. To address these limitations, we propose MVP, a non-Markovian VLA model that leverages episodic memory composed of historical actions and visual observations. To mitigate the computational cost of storing high-dimensional histories, we introduce a compact memory representation inspired by video understanding techniques. Additionally, to prevent the model from disregarding historical inputs during training, we design a novel feedback learning strategy based on SO(3) trajectory perturbation. This approach encourages the model to associate actions with their environmental consequences through observation-action-observation sequences. Experimental results on both simulated and real-world benchmarks demonstrate that MVP outperforms existing models, particularly on tasks that require temporal reasoning and history-dependent decision-making. Our findings highlight the importance of memory and feedback in advancing the capabilities of general-purpose robotic manipulation systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
现有的大多数视觉-语言-动作（VLA）模型都基于**马尔可夫假设**（即当前状态仅依赖上一时刻），这限制了模型处理**时间上延续的任务**（如长时序列操作）的能力，并且无法从**反馈**（如操作后的结果）中学习。为了突破这一局限，论文提出 MVP（Memory-enhanced Vision-Language-Action Policy with Feedback Learning），一种**非马尔可夫**的 VLA 模型，通过引入**情景记忆**和**反馈学习机制**，使机器人能够利用历史信息，并在长时任务中不断改进动作决策。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：打破马尔可夫假设，让模型能够回顾并利用历史动作和视觉观测（episodic memory），从而处理需要时间推理和历史依赖的任务；同时设计反馈学习策略，使模型学会将动作与其环境后果关联。
- **关键技术细节**：
  - **情景记忆（Episodic Memory）**：存储历史动作和视觉观察序列，作为模型输入的额外上下文。
  - **紧凑记忆表示（Compact Memory Representation）**：受视频理解技术启发，对高维历史数据进行降维，以缓解存储和计算开销。
  - **反馈学习策略（Feedback Learning）**：基于 **SO(3) 轨迹扰动**（SO(3) trajectory perturbation）的方法，在训练中向动作序列施加扰动，迫使模型通过“观察-动作-观察”序列理解动作对环境的改变，从而避免训练时模型忽略历史输入。
- **算法流程（文字说明）**：  
  模型接收语言指令、当前视觉观察，以及存储在情景记忆中的过去动作和观察的紧凑表示，输出当前动作。训练时，对真实轨迹施加 SO(3) 扰动产生负样本，强化模型对动作后果的预测能力。

## 3. 实验设计：数据集/场景、基准、对比方法
- **数据集/场景**：在**模拟环境**和**真实世界**的机器人操作任务上进行评估。论文摘要未具体列出数据集名称（例如是否使用 RLBench、CALVIN 等），仅说明“时间扩展任务”和“历史依赖决策任务”。
- **基准（Benchmark）**：使用标准模拟和真实操作基准（未明确标注）。
- **对比方法**：与**现有的马尔可夫 VLA 模型**（基线）进行对比，具体方法名称未在摘要中列出（可能正文中有详述）。

## 4. 资源与算力
论文摘要及元数据中**未明确说明**使用的算力（GPU 型号、数量、训练时长等）。需要查看完整论文才能得知。

## 5. 实验数量与充分性
- 由于仅提供摘要，**实验的具体组数、消融实验细节**未知。元数据提到“在时间扩展任务上表现优于马尔可夫基线，能从反馈中改进动作”，暗示可能进行了多组对比和消融。
- **充分性评估**：初步结论积极，但**信息披露不足**——缺少对记忆规模、紧凑表示维度、反馈学习扰动幅度的敏感性分析等。若仅依赖摘要，无法判断实验是否覆盖了所有关键变量及统计显著性。

## 6. 论文的主要结论与发现
- MVP 在需要**时间推理和历史依赖决策**的任务上显著优于现有马尔可夫 VLA 模型。
- **记忆增强**和**反馈学习**是提升长时任务性能的核心因素。
- 紧凑记忆表示有效缓解了高维历史数据带来的计算负担。
- SO(3) 轨迹扰动反馈策略帮助模型更好地理解动作与后果的因果关系。

## 7. 优点：方法或实验设计上的亮点
- 创新性地将**非马尔可夫框架**引入 VLA，解决了长期被忽视的时序依赖问题。
- 紧凑记忆表示借鉴视频理解，是处理高维观测的实用工程技巧。
- 反馈学习策略设计巧妙（利用 SO(3) 扰动生成负样本），有理论新意。
- 实验同时覆盖**模拟和真实场景**，增加了结论的可信度。

## 8. 不足与局限
- **触觉缺失**：论文未涉及触觉模态（元数据也指出“未涉及触觉”），限制了在精细操作任务中的应用。
- **细节不足**：来自摘要和元数据的信息有限，方法的具体数学形式、数据集名称、超参数、计算资源等均未公开，难以复现或全面评估。
- **可能存在偏差风险**：仅与“马尔可夫基线”对比，若基线选择不够强或代表性不足，优势可能被夸大。
- **应用限制**：反馈学习依赖轨迹扰动，可能不适用于任务规划层级或离散动作空间；记忆模块的引入增加了模型复杂度和推理延迟。

（完）
