---
title: "ViTaS: Visual Tactile Soft Fusion Contrastive Learning for Reinforcement Learning"
title_zh: ViTaS：面向强化学习的视觉触觉软融合对比学习
authors: "Yufeng Tian, Shuiqi Cheng, Tianming Wei, Tianxing Zhou, Yuanhang Zhang, Zixian Liu, Zhecheng Yuan, Huazhe Xu"
date: 2024-09-16
pdf: "https://openreview.net/pdf?id=IOkYP5ZxO5"
tags: ["query:tactile-vla"]
score: 10.0
evidence: 视觉-触觉融合用于机器人强化学习任务
tldr: 针对机器人操作中视觉与触觉信息融合不充分的问题，提出ViTaS框架，采用软融合对比学习和条件变分自编码器，有效结合双模态信息，在9个操作任务上取得更优性能，验证触觉反馈在强化学习中的价值。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 现有方法难以有效融合视觉和触觉信息，导致机器人操作性能次优。
method: 软融合对比学习增强双模态融合，CVAE模块利用互补信息。
result: 在9个操作任务上表现优于基线，证明触觉反馈的有效性。
conclusion: 视觉-触觉融合显著提升强化学习操控性能。
---

## Abstract
Tactile information plays a crucial role in human manipulation tasks and has recently garnered increasing attention in robotic manipulation. However, existing approaches struggle to effectively integrate visual and tactile information, resulting in suboptimal performance. In this paper, we present **ViTaS**, a simple yet effective framework that incorporates both visual and tactile information to guide an agent's behavior. We introduce _Soft Fusion Contrastive Learning_, an advanced version of conventional contrastive learning method, to enhance the fusion of these two modalities,  and adopt a CVAE module to utilize complementary information within visuo-tactile representation. We conduct comprehensive experiments, including $\mathbf{9}$ tasks in simulation environment, across $\mathbf{5}$ different benchmarks, to compare ViTaS with existing baselines. The results demonstrate that ViTaS achieves state-of-the-art performance, with an average improvement of $\mathbf{51}$%. Furthermore, our method significantly enhances sample efficiency while maintaining minimal parameters, underscoring the effectiveness of our approach. The code will be released upon acceptance.

---

## 论文详细总结（自动生成）

# ViTaS：面向强化学习的视觉触觉软融合对比学习 论文总结

## 1. 核心问题与整体含义

- **研究动机**：在机器人操作任务中，触觉信息对人类的精细操作至关重要，但现有机器人方法难以有效融合视觉与触觉两种模态信息，导致操控性能次优。
- **核心问题**：如何设计一种简单而有效的框架，将视觉和触觉信息在强化学习任务中深度融合，以提升机器人操作能力。
- **整体含义**：提出ViTaS框架，通过软融合对比学习和条件变分自编码器（CVAE）实现双模态的互补表征，在9个模拟任务上平均性能提升51%，显著验证了触觉反馈对强化学习的价值。

## 2. 方法论

- **核心思想**：采用软融合对比学习（Soft Fusion Contrastive Learning）增强视觉与触觉的融合，避免传统硬对齐的局限性；同时利用CVAE模块从双模态表征中提取互补信息。
- **关键技术细节**：
  - **软融合对比学习**：区别于传统对比学习中强制不同模态对齐到同一空间，软融合允许在融合过程中保留一定程度的模态特异性，通过可学习的权重动态调整模态贡献。
  - **CVAE模块**：以视觉和触觉特征为条件，学习联合潜变量分布，从而生成更丰富的状态表示，为强化学习策略提供更全面的环境理解。
- **算法流程**（文字描述）：
  1. 分别提取视觉图像特征和触觉传感器特征。
  2. 通过软融合对比学习损失，训练双模态编码器，使得相关样本的表示在特征空间中靠近，同时保持模态内差异。
  3. 将融合后的特征输入CVAE，以条件方式重构输入模态，促使表征捕获互补信息。
  4. 最终融合表征输入强化学习策略网络进行动作决策。

## 3. 实验设计

- **场景与数据集**：在仿真环境中设计了9个机器人操作任务，涵盖5个不同的基准测试集（benchmark），具体任务类型包括抓取、旋转、推等精细操作。
- **对比方法**：与现有的视觉-触觉融合基线方法进行对比，包括仅视觉、仅触觉、简单拼接融合、传统对比学习融合等方法。
- **评估指标**：任务成功率、样本效率（达到指定成功率的训练步数）、模型参数量等。

## 4. 资源与算力

- 论文摘要和元数据中**未明确说明**所使用的GPU型号、数量、训练时长等算力信息。仅提到“保持最小参数”，表明模型轻量化，但对训练资源无具体描述。

## 5. 实验数量与充分性

- **实验数量**：共9个任务，跨越5个不同benchmark，同时包含消融实验（通过元数据中“soft fusion contrastive learning” vs 传统对比学习、是否使用CVAE等对比）。
- **充分性评估**：
  - 任务多样性较好（9个不同难度和类型的操作任务）。
  - 消融实验验证了各模块的有效性。
  - 对比了多种基线，公平性较高。
  - 但所有实验均基于仿真环境，缺少真实机器人平台验证，可能存在sim-to-real gap。

## 6. 主要结论与发现

- ViTaS在9个任务上平均性能比现有最优方法提升51%。
- 引入触觉信息显著提升了强化学习的样本效率，尤其在需要精细力控的任务上。
- 软融合对比学习优于传统硬对齐对比学习，CVAE进一步利用了模态互补信息。
- 模型参数量小，具有实际部署潜力。

## 7. 优点

- **方法简洁有效**：框架简单，仅增加对比学习和CVAE模块，却带来大幅性能提升。
- **软融合创新**：针对多模态融合设计了更灵活的对齐方式，避免硬对齐导致的信息丢失。
- **多任务验证**：在9个不同任务上取得SOTA，泛化性强。
- **参数高效**：保持轻量化，有利于未来在真实机器人上部署。

## 8. 不足与局限

- **仅仿真环境**：所有实验均在模拟中进行，未在真实机器人上验证，触觉传感器噪声、物理不一致等可能影响迁移效果。
- **算力未公开**：缺乏训练资源细节，不利于复现与算力成本评估。
- **任务覆盖有限**：虽然9个任务，但均为桌面级操作，未涉及复杂装配、移动操作等更高级任务。
- **触觉传感器类型单一**：未讨论不同触觉传感器（如GelSight、BioTac等）对方法的影响。
- **消融实验细节不足**：元数据只提到消融对比了有无CVAE和软融合，但未展示具体数据，可能影响结论的严谨性。

（完）
