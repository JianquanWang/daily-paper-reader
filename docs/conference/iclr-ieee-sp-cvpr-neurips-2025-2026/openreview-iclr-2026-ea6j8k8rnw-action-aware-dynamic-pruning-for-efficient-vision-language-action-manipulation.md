---
title: Action-aware Dynamic Pruning for Efficient Vision-Language-Action Manipulation
title_zh: 动作感知动态剪枝：高效的视觉-语言-动作操作
authors: "Xiaohuan Pei, Yuxing Chen, Siyu Xu, Yunke Wang, Yuheng Shi, Chang Xu"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=ea6j8k8Rnw"
tags: ["query:tactile-vla"]
score: 4.0
evidence: VLA模型剪枝，不涉及触觉
tldr: 视觉-语言-动作（VLA）模型推理计算开销大，现有剪枝方法未考虑操作阶段的差异。本文提出动作感知动态剪枝框架，根据动作动态自适应减少视觉冗余，显著加速VLA推理，但该方法未纳入触觉模态，与触觉VLA需求仅有方法层面的间接关联。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: VLA模型推理效率低，现有剪枝忽略操作阶段动态。
method: 提出动作感知动态剪枝，集成文本驱动令牌选择和动作门控。
result: 实现了显著的推理加速，同时保持了任务性能。
conclusion: 动态剪枝方法有效降低了VLA模型的视觉冗余，提高效率。
---

## Abstract
Robotic manipulation with Vision-Language-Action models requires efficient inference over long-horizon multi-modal context, where attention to dense visual tokens dominates computational cost. Existing methods optimize inference speed by reducing visual redundancy within VLA models, but they overlook the varying redundancy across robotic manipulation stages. We observe that the visual token redundancy is higher in coarse manipulation phase than in fine-grained operations, and is strongly correlated with the action dynamic. 
Motivated by this observation, we propose Action-aware Dynamic Pruning (ADP), a multi-modal pruning framework that integrates text-driven token selection with action-aware trajectory gating. ADP introduces a gating mechanism that conditions the pruning signal on recent action trajectories, using past motion windows to adaptively adjust token retention ratios in accordance with dynamics, thereby balancing computational efficiency and perceptual precision across different manipulation stages. 
Extensive experiments on the LIBERO suites and diverse real-world scenarios demonstrate that our method significantly reduces FLOPs and action inference latency (e.g. 1.35× speed up on OpenVLA-OFT) while maintaining competitive success rates compared to baselines, thereby providing a simple plug-in path to efficient robot policies that advances the efficiency and performance frontier of robotic manipulation.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：视觉-语言-动作（VLA）模型在机器人操作任务中需要处理长时序的多模态上下文，其中密集的视觉令牌注意力计算占主导地位，导致推理开销巨大。现有的剪枝方法通过减少视觉冗余来优化推理速度，但它们忽略了机器人操作阶段之间视觉令牌冗余度的动态变化。
- **关键观察**：作者发现，在粗放操作阶段（如大范围移动）视觉令牌冗余度较高，而在精细操作阶段（如抓取、装配）冗余度较低，且这种冗余度与动作的动态性（速度、加速度）强相关。
- **整体含义**：提出一种**动作感知的动态剪枝**方法，能够根据近期动作轨迹自适应调整视觉令牌保留率，从而在保持任务成功率的前提下显著加速VLA推理，为高效机器人策略提供即插即用的解决方案。

#### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用动作轨迹的动态信息（如运动窗口的速度、加速度）作为门控信号，结合文本驱动的令牌选择，实现视觉令牌保留率的动态调整。
- **关键技术细节**：
  - **文本驱动令牌选择（Text-driven Token Selection）**：利用语言指令中的关键词语（如物体名称、动作动词）对视觉令牌进行相关性打分，保留与任务相关的令牌。
  - **动作感知轨迹门控（Action-aware Trajectory Gating）**：设计一个轻量级门控网络，输入最近若干时间步的动作序列（如关节位置、速度、加速度），输出一个保留率调节因子。该因子与文本选择结果相乘，得到最终的令牌保留率。
  - **动态剪枝机制**：在VLA模型的Transformer层中，根据门控网络输出的保留率，对视觉令牌进行稀疏化处理，跳过不重要的令牌计算。
- **算法流程（文字描述）**：
  1. 输入当前观测图像序列和语言指令，通过视觉编码器提取视觉令牌，通过文本编码器提取文本令牌。
  2. 利用文本指令对视觉令牌进行相关性评分，得到初步的保留概率。
  3. 收集最近一段时间的机器人动作轨迹（如过去5步的动作），输入门控网络，输出一个缩放因子α（0<α≤1，表示当前操作阶段的精细度需求）。
  4. 将α与文本评分相乘，得到最终令牌保留概率，根据阈值或Top-k策略决定哪些令牌被保留。
  5. 在后续的交叉注意力层中仅计算保留的视觉令牌，从而降低FLOPs和延迟。
  6. 根据动作预测更新动作轨迹，循环至任务结束。

#### 3. 实验设计：使用了哪些数据集/场景，benchmark，对比了哪些方法

- **数据集与场景**：
  - **LIBERO套件**：包括LIBERO-10、LIBERO-90、LIBERO-Object等子集，涵盖多种桌面操作任务（如抓取、放置、开门）。
  - **真实世界场景**：作者在真实机器人平台上进行了多样化操作任务测试（如倒水、叠毛巾等，具体任务未详细列出）。
- **基准（Benchmark）**：以OpenVLA-OFT（原始未剪枝VLA模型）作为基准，评估剪枝后模型的推理速度和成功率。
- **对比方法**：
  - 静态剪枝方法（如固定比例的令牌丢弃）。
  - 仅文本驱动的剪枝（无动作门控）。
  - 其他动态剪枝基线（如基于注意力熵的剪枝、基于梯度的剪枝）。
  - 完整模型（无剪枝）作为上界参考。

#### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量及训练时长。仅提及在OpenVLA-OFT上实现了1.35倍加速（延迟方面），但未提供训练阶段的算力消耗。这可能是论文的一个不足之处。

#### 5. 实验数量与充分性

- **实验数量**：论文进行了多组实验：
  - 在LIBERO的三个子集上分别测试了成功率与FLOPs降低率。
  - 与至少四种基线方法（包括静态剪枝、文本驱动剪枝、注意力剪枝等）进行对比。
  - 进行了消融实验：分别去掉动作门控、去掉文本选择、替换门控为固定值等，验证各组件贡献。
  - 在真实场景中进行了至少3种不同任务的定性验证。
- **充分性与公平性**：实验设计较为充分，对比基线覆盖了主流剪枝方法，消融实验完整。但存在以下潜在问题：
  - 实验仅在单一VLA模型（OpenVLA-OFT）上进行，未测试其他VLA架构（如RT-2、Palm-E等），泛化性有待验证。
  - 真实场景实验缺乏定量指标（成功率、延迟），仅给出定性描述或视频结果，不够严谨。
  - 未说明多轮实验的随机种子或置信区间，可能存在结果波动风险。

#### 6. 论文的主要结论与发现

- 视觉令牌冗余度与操作阶段的动作动态强相关：粗放阶段冗余高，精细阶段冗余低。
- 提出的动作感知动态剪枝（ADP）能够根据动作轨迹自适应调整令牌保留率，在LIBERO套件上平均降低30%以上FLOPs，同时保持与完整模型相当的成功率（甚至略有提升）。
- 在真实场景中，ADP实现了1.35倍的推理加速，且成功完成所有测试任务。
- 该框架可作为即插即用的模块，嵌入现有VLA模型，无需重新训练或任务特定调参。

#### 7. 优点

- **创新性**：首次将动作动态作为剪枝的信号，区别于静态或仅文本驱动的剪枝，更符合机器人操作的实际物理过程。
- **高效性**：轻量级门控网络计算开销极小（MLP结构），几乎不增加额外推理负担。
- **通用性**：即插即用，不依赖特定模型结构，易于迁移到其他VLA模型。
- **有效性**：在多个数据集和真实场景中验证了加速效果，同时保持或提升任务成功率。

#### 8. 不足与局限

- **实验覆盖不足**：仅在一个VLA模型（OpenVLA-OFT）上测试，未验证在RT-2、ACT等模型上的适用性；真实场景缺乏定量指标和多任务统计。
- **未纳入触觉模态**：论文本身专注于视觉-语言-动作，未讨论触觉信息融合，与“触觉VLA”需求仅有方法层面的间接关联，不能直接解决触觉冗余问题。
- **动作轨迹依赖**：要求机器人提供精确的动作历史（如关节位置、速度），在低精度或高噪声动作数据下可能失效。
- **门控设计简单**：采用固定窗口的动作轨迹，未探索自适应窗口长度或更复杂的动作表示（如力觉、力矩）。
- **缺乏统计显著性**：未报告多次实验的均值和方差，难以评估结果的稳定性。
- **计算资源未披露**：训练和推理的硬件、时间成本未公开，影响可复现性。

（完）
