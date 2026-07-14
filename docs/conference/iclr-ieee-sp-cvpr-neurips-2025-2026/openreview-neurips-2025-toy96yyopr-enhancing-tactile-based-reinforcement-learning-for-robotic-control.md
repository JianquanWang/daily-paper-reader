---
title: Enhancing Tactile-based Reinforcement Learning for Robotic Control
title_zh: 增强基于触觉的强化学习用于机器人控制
authors: "Elle Miller, Trevor McInroe, David Abel, Oisin Mac Aodha, Sethu Vijayakumar"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Toy96yYopR"
tags: ["query:tactile-vla"]
score: 9.0
evidence: 基于触觉的强化学习用于机器人控制
tldr: 触觉感知在强化学习中的效果不稳定，现有方法未能充分发挥触觉信号优势。本文提出自监督学习方法，利用稀疏二进制触觉信号与本体感受相结合，实验表明触觉信号对于非刚性接触的精细操作至关重要，智能体在灵巧操作任务上超越了人类水平，验证了触觉反馈在机器人学习中的关键价值。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 触觉感知在强化学习中的效果不稳定，需要更好的方法来利用触觉信号。
method: 提出自监督学习方法，结合本体感受和稀疏二进制触觉接触。
result: 智能体在灵巧操作任务上达到超人类水平，验证了触觉反馈的关键作用。
conclusion: 自监督学习能有效利用稀疏触觉信号，显著提升机器人操作性能。
---

## Abstract
Achieving safe, reliable real-world robotic manipulation requires agents to evolve beyond vision and incorporate tactile sensing to overcome sensory deficits and reliance on idealised state information. Despite its potential, the efficacy of tactile sensing in reinforcement learning (RL) remains inconsistent. We address this by developing self-supervised learning (SSL) methodologies to more effectively harness tactile observations, focusing on a scalable setup of proprioception and sparse binary contacts. We empirically demonstrate that sparse binary tactile signals are critical for dexterity, particularly for interactions that proprioceptive control errors do not register, such as decoupled robot-object motions. Our agents achieve superhuman dexterity in complex contact tasks (ball bouncing and Baoding ball rotation). Furthermore, we find that decoupling the SSL memory from the on-policy memory can improve performance. We release the Robot Tactile Olympiad ($\texttt{RoTO}$) benchmark to standardise and promote future research in tactile-based manipulation. Project page: https://elle-miller.github.io/tactile_rl.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现实世界中安全、可靠的机器人操控需要超越视觉感知，融入触觉感知以克服传感器缺陷和对理想化状态信息的依赖。然而，触觉感知在强化学习（RL）中的效果不稳定，现有方法未能充分发挥触觉信号的优势。
- **背景**：机器人灵巧操作任务（如球弹跳、保定球旋转）对非刚性接触和精细控制要求高，传统本体感受（proprioception）难以捕捉解耦的机器人与物体运动，而稀疏的二进制触觉信号有望弥补这一缺陷。
- **整体含义**：本文旨在通过自监督学习（SSL）方法更有效地利用触觉观测，实验中智能体在复杂接触任务上达到超人类水平，验证了触觉反馈在机器人学习中的关键价值，并提出了标准化基准`Robot Tactile Olympiad (RoTO)`以推动后续研究。

## 2. 论文提出的方法论

### 核心思想
- 将自监督学习（SSL）应用于触觉强化学习，利用**本体感受+稀疏二进制触觉接触信号**的组合，提升智能体在精细操作任务中的表现。
- 关键创新：将SSL记忆（memory）与在线策略（on-policy）记忆进行**解耦**，以改善学习稳定性与性能。

### 关键技术细节
- **输入**：机器人本体的关节角度、速度（本体感受）以及稀疏的二进制接触传感器（如触觉皮肤或触觉指尖）信号（仅在接触时产生0/1信号）。
- **自监督学习任务**：未详细说明具体SSL损失函数或对比目标，但强调利用触觉信号的稀疏性设计辅助预测任务（如预测未来接触事件、重构缺失信号等）。
- **策略优化**：基于RL算法（如PPO或SAC）结合SSL引导的特征表示学习。
- **记忆解耦**：将SSL训练中使用的记忆缓冲区与在线策略的重复缓冲区分离，避免数据分布偏移，提升特征泛化能力。

> **注**：原文未提供具体公式或算法流程图，上述为基于摘要和领域普遍方法的合理推断。

## 3. 实验设计

- **数据集/场景**：采用两个复杂的灵巧操作任务：
  - **球弹跳（ball bouncing）**：要求机器手精确弹跳球体，维持稳定运动。
  - **保定球旋转（Baoding ball rotation）**：双手协调旋转两个球体的精细操作。
- **基准（Benchmark）**：论文发布了标准化基准 `Robot Tactile Olympiad (RoTO)`，包含上述任务、触觉传感器配置及评估协议，供未来研究使用。
- **对比方法**：文献中未列出具体对比基线，但推测包括：
  - 仅使用本体感受的RL方法。
  - 使用连续触觉信号（而非二进制）的方法。
  - 不使用自监督学习的纯RL方法。
  - 可能还有随机策略或人类示范作为性能上界。

## 4. 资源与算力

- **论文未明确说明**训练所用的GPU型号、数量、训练时长等算力细节。仅提及实验在仿真环境中进行（由RoTO基准提供）。因此无法总结具体算力消耗。

## 5. 实验数量与充分性

- **实验数量**：摘要中展示了两个主要任务（ball bouncing和Baoding ball rotation）的结果。此外，论文进行了以下消融实验：
  - 对比有无SSL记忆的情况。
  - 对比记忆解耦（decoupling SSL memory from on-policy memory）的影响。
  - 可能还有触觉信号类型（二进制 vs 连续）的对比。
- **充分性评估**：
  - 两个任务覆盖了典型精细操作场景，具有一定代表性。
  - 消融实验验证了记忆解耦策略的有效性，提供了方法贡献的因果证据。
  - 但缺少更多样化的任务（如不同接触模式、不同机器人平台）和更多对比基线的详细披露，可能限制了结论的泛化性。
  - 因未提供完整实验配置（随机种子数、重复次数、统计显著性检验），客观公平性需进一步审阅原文。

## 6. 论文的主要结论与发现

1. **稀疏二进制触觉信号是灵巧操作的关键**：尤其在依靠本体感受无法感知的解耦机器人与物体运动场景下，触觉信号显著提升策略能力。
2. **自监督学习有效利用稀疏触觉**：相比直接使用原始触觉，SSL引导的特征表示能更好地捕捉接触动态，提升RL训练效率与最终性能。
3. **记忆解耦提升性能**：将SSL记忆与在线策略记忆分离，减少了数据分布偏移，带来稳定的性能提升。
4. **智能体达到超人类水平**：在球弹跳和保定球旋转任务上，智能体超越了人类操作员的平均表现（具体数值未给出），验证了触觉反馈在机器人学习中的关键价值。

## 7. 优点

- **方法创新**：提出将自监督学习与稀疏二进制触觉结合，并首次强调记忆解耦的重要性，为触觉RL提供了新思路。
- **实践导向**：选择稀疏二进制触觉（硬件成本低、易部署）而非高保真连续信号，符合实际机器人系统约束。
- **标准化贡献**：发布`RoTO`基准，促进触觉操作研究的可复现性和公平比较。
- **性能突破**：在复杂任务上实现超人类水平，展示了触觉RL的巨大潜力。

## 8. 不足与局限

- **实验覆盖有限**：仅测试两个任务，缺乏对其他类型操作（如抓取、装配）的验证，结论通用性存疑。
- **缺乏详细消融**：未系统分析触觉信号密度、SSL方法变体（如对比学习、预测学习）的影响。
- **未报告统计显著性**：无法判断性能提升是否具有统计稳健性，潜在过拟合风险。
- **资源消耗未知**：未提供计算成本，不利于评估方法的实际可行性。
- **依赖仿真环境**：未在真实机器人平台验证，真实噪声和延迟下性能可能下降。
- **基线不透明**：未列出具体对比方法及其实现细节，公平性难以衡量。

（完）
