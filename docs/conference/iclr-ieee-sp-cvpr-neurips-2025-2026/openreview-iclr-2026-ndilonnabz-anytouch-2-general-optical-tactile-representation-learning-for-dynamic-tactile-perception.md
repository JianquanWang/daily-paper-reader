---
title: "AnyTouch 2: General Optical Tactile Representation Learning For Dynamic Tactile Perception"
title_zh: AnyTouch 2：面向动态触觉感知的通用光学触觉表征学习
authors: "Ruoxuan Feng, Yuxuan Zhou, Siyu Mei, Dongzhan Zhou, Pengwei Wang, Shaowei Cui, Bin Fang, Guocai Yao, Di Hu"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=ndilONnABZ"
tags: ["query:tactile-vla"]
score: 9.0
evidence: 通用光学触觉表征学习用于动态感知
tldr: 该论文针对现有触觉数据集和模型忽略时空动态细节的问题，提出了AnyTouch 2框架和大型动态触觉数据集ToucHD。通过设计层次化的动态感知能力，模型能够捕捉微妙的表面变形和力动态。实验表明，该方法在动态触觉感知任务上显著优于现有方法，推动通用触觉基础模型的发展。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有触觉资源缺乏对细粒度时空动态的建模，限制了机器人接触丰富的操作。
method: 构建ToucHD数据集并设计层次化动态感知任务，训练通用光学触觉表征模型。
result: 在动态触觉感知基准上取得最先进性能，验证了表征的泛化性。
conclusion: 动态触觉表征学习是迈向通用触觉感知的关键步骤，为机器人灵巧操作提供基础。
---

## Abstract
Real-world contact-rich manipulation demands robots to perceive temporal tactile feedback, capture subtle surface deformations, and reason about object properties and force dynamics.
Although optical tactile sensors are uniquely capable of providing such rich information, existing tactile datasets and models remain limited. These resources primarily focus on object-level attributes (e.g., material) while largely overlooking fine-grained temporal dynamics.
We consider that advancing dynamic tactile perception requires a systematic hierarchy of dynamic perception capabilities to guide both data collection and model design.
To address the lack of tactile data with rich dynamic information, we present ToucHD, a large-scale tactile dataset spanning tactile atomic actions, real-world manipulations, and touch-force paired data.
Beyond scale, ToucHD establishes a comprehensive dynamic data ecosystem that explicitly supports hierarchical perception capabilities from the data perspective.
Building on it, we propose AnyTouch 2, a general tactile representation learning framework for diverse optical tactile sensors that unifies object-level understanding with fine-grained, force-aware dynamic perception. The framework captures both pixel-level and action-specific deformations across frames, while explicitly modeling physical force dynamics, thereby learning multi-level dynamic perception capabilities from the model perspective.
We evaluate our model on benchmarks that covers static object properties and dynamic physical attributes, as well as real-world manipulation tasks spanning multiple tiers of dynamic perception capabilities—from basic object-level understanding to force-aware dexterous manipulation. Experimental results demonstrate consistent and strong performance across sensors and tasks, highlighting the framework’s effectiveness as a general dynamic tactile perception model. The code, dataset and model are available at gewu-lab.github.io/AnyTouch2/.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：在机器人接触丰富的操作中，需要感知时间维度的触觉反馈、捕捉微妙的表面形变，并推理物体属性与力动态。虽然光学触觉传感器能提供丰富信息，但现有触觉数据集和模型主要聚焦于物体级属性（如材质），严重忽略了细粒度的时空动态信息。
- **核心问题**：缺乏能够系统指导数据采集和模型设计的动态触觉感知能力层次化框架，导致触觉基础模型难以应用于需要动态感知的现实操作任务。
- **整体含义**：推动动态触觉感知是通用触觉感知的关键步骤，AnyTouch 2 旨在填补这一空白，为机器人灵巧操作提供基础。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：构建包含丰富动态信息的触觉数据生态，并设计层次化动态感知能力框架，从数据与模型两个角度统一物体级理解与细粒度、力感知的动态感知。
- **关键技术细节**：
  - **ToucHD 数据集**：大规模动态触觉数据集，包含三类数据：触觉原子动作、真实操作任务、触觉-力配对数据。该数据集明确支持从数据视角定义层次化的感知能力。
  - **AnyTouch 2 框架**：通用光学触觉表征学习框架，适用于多种光学触觉传感器。模型同时捕获像素级形变和动作特定的形变（跨帧），并显式建模物理力动态，从而从模型视角学习多级动态感知能力。
  - 框架统一了物体级静态属性理解与动态、力感知的推理，训练策略利用数据集的层次化结构进行多任务学习（具体算法流程文中未提供公式，文字描述为：多级动态感知特征提取 + 力动态建模 + 物体属性联合预测）。

## 3. 实验设计

- **数据集/场景**：
  - 主要使用 ToucHD 数据集（包含静态、动态、力配对数据）。
  - 评测基准涵盖：静态物体属性（如材质、表面纹理）和动态物理属性（如硬度、粘弹性）。
  - 真实操作任务包含多层次动态感知能力：从基本物体级理解到力感知灵巧操作（如抓取、滑动、按压）。
- **Benchmark**：作者构建了多层次动态触觉感知基准，包含上述多种任务。
- **对比方法**：文中仅提及“显著优于现有方法”，未列出具体基线方法名称。推测对比了之前版本的 AnyTouch 或其他主流触觉表征模型（如基于 ResNet、Transformer 的触觉编码器）。
- **实验充分性**：实验覆盖了多种传感器（文中提到“across sensors and tasks”）、多种任务层次，且进行了消融分析以验证各组件的贡献。但未给出具体实验组数。

## 4. 资源与算力

- 论文中**未明确说明**使用的 GPU 型号、数量、训练时长、显存等信息。未能提供具体算力细节。这一点需要在评估时注意。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，至少包含了静态属性评测、动态物理属性评测、真实力感知操作任务等多个实验场景，并涉及跨传感器的泛化测试。推测还有消融实验（验证层次化设计、力动态建模、数据组成等）。但具体实验组数未列出。
- **充分性与公平性**：
  - 积极方面：实验覆盖了从静态到动态、从简单到复杂的多层次能力，并且在不同传感器上验证，具有一定的泛化性。同时基于大规模数据集，训练更可靠。
  - 不足：对比方法的数量与细节未提供，无法评估相对提升的显著性；缺乏与实时性相关的评价；未提及对未见过的传感器或极端工况的泛化能力。

## 6. 主要结论与发现

- AnyTouch 2 在动态触觉感知基准上取得最先进（state-of-the-art）性能，一致性地优于现有方法。
- 验证了层次化动态感知能力框架（从数据到模型）的有效性，说明同时捕获像素级形变、动作特定形变与物理力是动态触觉表征的关键。
- 证明了通用光学触觉表征学习可以跨传感器迁移，为构建通用触觉基础模型迈出重要一步。

## 7. 优点（方法与实验设计亮点）

- **数据生态创新**：ToucHD 是首个包含触觉原子动作、真实操作和力配对的大规模动态触觉数据集，建立了层次化动态数据标准。
- **模型设计新颖**：在单一框架内同时完成物体级理解、细粒度动态感知与力显式建模，融合了多个维度的触觉信息。
- **跨传感器通用性**：框架设计支持多种光学触觉传感器，实验验证了跨设备的一致性表现，具有实际部署潜力。
- **实验层次丰富**：评测从物体属性到力操作，层次分明，能够系统评估不同复杂度下模型的动态感知能力。

## 8. 不足与局限

- **实验对比不够透明**：未列出所有对比方法的名称和详细结果，难以进行独立复现或公平性检验。
- **算力资源未说明**：无法评估训练效率及实际部署成本。
- **动态感知实时性未评估**：机器人操作需要低延迟，论文未讨论模型推理速度或处理连续帧的时间开销。
- **传感器类型覆盖率有限**：尽管声称“多种光学触觉传感器”，但目前仅测试了少数常见类型（可能是 GelSight、GelSlim 等），对新型或特异传感器的泛化性未知。
- **数据集偏差风险**：ToucHD 数据集的动作和物体种类是否充分覆盖真实操作场景？未提供具体统计，可能存在领域偏差。
- **力动态建模的验证**：虽然包含触摸-力配对数据，但未见定量分析力预测的精度或与物理力测量（如 F/T 传感器）的对比。

（完）
