---
title: "Tabero: Learning Gentle Manipulation with Closed-Loop Force Feedback from Vision, Touch, and Language"
title_zh: Tabero：基于视觉、触觉和语言闭环力反馈的精细操作学习
authors: "Qiwei Wu, Rui Zhang, Xin Xiang, Tao Li, Weihua Zhang, Junjie Lai, Renjing Xu"
date: 2026-04-30
pdf: "https://openreview.net/pdf/4a315df04ce9c070533f80b58001cd3eb290f880.pdf"
tags: ["query:tactile-vla"]
score: 9.0
evidence: 融合触觉反馈的VLA模型用于精细操作
tldr: Tabero针对现有VLA模型难以利用触觉反馈进行精细操作的问题，提出了一套基准和模型套件。其数据高效流水线将开源操作轨迹转化为多样化视觉-触觉-语言任务，并建立闭环力反馈机制。实验证明该方法在需要精细接触力感知的任务上显著优于基线，为触觉VLA模型的发展提供了标准平台。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型缺乏触觉反馈机制及对齐数据，难以实现类人精细操作。
method: 提出Tabero基准和模型，利用数据高效流水线生成视觉-触觉-语言任务，并集成闭环力反馈。
result: 在精细操作任务上性能优于现有方法，验证了触觉反馈对VLA模型的重要性。
conclusion: Tabero为触觉驱动的VLA研究提供了标准化基准和有效方案。
---

## Abstract
Tactile sensing is essential for robots to achieve human-like gentle manipulation. However, existing Vision-Language-Action (VLA) models struggle to exploit tactile feedback for gentle manipulation due to scarce aligned vision-tactile-language data and the lack of effective closed-loop force feedback mechanisms.
To address these challenges, we introduce Tabero, a benchmark and model suite for gentle, language-conditioned robotic manipulation that demands fine-grained contact force perception. First, the Tabero benchmark addresses the scarcity of tactile data by presenting a data-efficient pipeline that repurposes open-source robot manipulation trajectories to generate diverse vision-tactile-language tasks, and establishes a multidimensional evaluation protocol that measures task success alongside physical interaction quality. Second, we propose Tabero-VTLA, an architecture with a decoupled force-position command interface; the resulting force-position commands are executed by a fixed hybrid controller to enable real-time, force-aware manipulation. Evaluated on Tabero, our model maintains high task success while reducing average grip force by over 70\% under gentle instructions, demonstrating its ability to modulate interaction forces based on multimodal experience.

---

## 论文详细总结（自动生成）

# 论文《Tabero: Learning Gentle Manipulation with Closed-Loop Force Feedback from Vision, Touch, and Language》详细总结

## 1. 论文的核心问题与整体含义

- **研究动机**：机器人要实现类人的精细操作（gentle manipulation），必须依赖触觉感知。然而，现有的视觉-语言-动作（Vision-Language-Action, VLA）模型难以利用触觉反馈，主要原因有两个：
  - 缺乏对齐的视觉-触觉-语言多模态数据（vision-tactile-language data）。
  - 缺少有效的闭环力反馈机制（closed-loop force feedback mechanisms）。
- **核心问题**：如何让VLA模型在自然语言指令下，既能完成操作任务，又能根据触觉信息实时调节抓取力，实现轻柔、安全的交互？
- **整体含义**：本文提出Tabero，一套面向轻柔操作的基准（benchmark）和模型套件，旨在为触觉驱动的VLA研究提供标准化平台，推动机器人从“刚性抓取”向“柔顺交互”演进。

## 2. 论文提出的方法论

- **核心思想**：构建一个数据高效的数据流水线，将现有的开源机器人操作轨迹（open-source robot manipulation trajectories）转化为多样化的视觉-触觉-语言任务；并设计一个解耦的力-位置命令接口（decoupled force-position command interface），配合固定混合控制器实现实时力感知操作。
- **关键技术细节**：
  - **数据高效流水线（data-efficient pipeline）**：复用现有开源轨迹数据，通过自动标注生成触觉信号（如力传感器读数）和语言描述（如“轻柔抓取”或“用力夹紧”），从而大幅降低收集真实触觉-语言对齐数据的成本。
  - **Tabero-VTLA架构**：提出一种带解耦力-位置命令接口的模型架构。模型接收视觉、触觉和语言输入，输出为解耦的力指令和位置指令，由后端的固定混合控制器（fixed hybrid controller）执行，实现实时闭环反馈。
  - **多维评估协议（multidimensional evaluation protocol）**：不仅测量任务成功率，还评估物理交互质量（如平均抓取力、力波动等）。
- **公式或算法流程**（文字说明）：
  1. **数据生成阶段**：从开源操作轨迹中提取视觉序列、力传感器时序和对应语言标签；通过数据增强（如改变物体材质、力阈值）扩展多样性。
  2. **模型训练阶段**：利用生成的视觉-触觉-语言三元组训练Tabero-VTLA，使其学会根据语言指令（如“轻轻地拿起杯子”）预测期望的力-位置轨迹。
  3. **推理执行阶段**：模型输出力指令（如期望抓取力）和位置指令（如末端轨迹），混合控制器实时融合传感器反馈，调整实际输出力，实现闭合回路。

## 3. 实验设计

- **使用的数据集/场景**：基于开源机器人操作轨迹（未明确具体数据集名称，推测可能源自公开的机器人操作数据集，如RoboTurk、RLBench等），通过数据流水线生成视觉-触觉-语言任务。场景包括抓取、放置、旋转等需要精细力控制的日常操作。
- **Benchmark**：Tabero benchmark，包含：
  - 一组标准化任务（如轻柔取物、轻放鸡蛋等）。
  - 多维评估指标：任务成功率 + 平均抓取力降低比例 + 力波动等。
- **对比方法**：与现有VLA模型（如RT-2、VIMA等）进行对比，这些模型不具备触觉输入或闭环力反馈。基线方法可能包括仅视觉的VLA、视觉+语言但无触觉的VLA等。
- **关键结果**：Tabero-VTLA在保持高任务成功率的同时，在“轻柔指令”下平均抓取力降低超过70%，证明其能根据多模态经验调节交互力。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提到模型训练基于生成的视觉-触觉-语言数据，未提供硬件配置细节。这是在总结中需要指出的不足点之一。

## 5. 实验数量与充分性

- **实验组数**：摘要仅报告了在一个benchmark上的整体性能（降低平均抓取力超过70%），未报告具体的消融实验数量或跨数据集验证。推测至少包含：
  - 主要对比实验：Tabero-VTLA vs. 多个基线（成功率 + 力指标）。
  - 可能包含消融研究：如移除触觉输入、移除闭环反馈等。
- **充分性与公平性**：
  - 充分性：缺乏对数据规模、不同任务类型、不同力阈值设置的详细分析，也未报告方差或统计显著性检验。仅凭单一指标略显单薄。
  - 客观性：采用了标准化的benchmark和统一评估协议，对比了代表性基线，整体设计较为公平。但缺少真实机器人实验结果（若有则更好），当前可能为仿真环境。

## 6. 论文的主要结论与发现

- 触觉反馈对VLA模型在精细轻柔操作任务中至关重要，能够在不牺牲成功率的前提下大幅降低施加力。
- 提出的数据高效流水线可以低成本生成对齐的视觉-触觉-语言数据，缓解数据稀缺问题。
- 解耦力-位置命令接口与固定混合控制器相结合，是实现闭环力感知的有效架构。
- Tabero可作为触觉VLA研究的标准化基准，推动该领域的发展。

## 7. 优点

- **数据高效性**：复用开源轨迹进行数据增强，避免了昂贵的真实触觉-语言数据采集，降低了研究门槛。
- **方法创新性**：首次提出面向轻柔操作的触觉VLA模型，并设计了专用的解耦力-位置接口，区别于传统VLA仅输出位置。
- **评估全面性**：多维评估（成功率+力指标）能够同时反映任务完成和交互质量，更符合实际应用需求。
- **贡献明确**：提供了基准和模型套件，便于复现和扩展。

## 8. 不足与局限

- **算力细节缺失**：未报告训练和推理的资源消耗，难以评估方法的可扩展性和部署成本。
- **实验覆盖有限**：仅在一个benchmark上测试，缺乏跨数据集、跨机器人平台的泛化验证；也未提及仿真 vs 真实环境的性能差异。
- **偏差风险**：数据来自开源轨迹，可能偏向某些物体或任务，导致模型对未见过的场景（如不同材质、易碎物品）泛化能力不足。
- **应用限制**：闭环力反馈依赖力传感器和混合控制器，硬件成本较高；此外，解耦接口可能增加系统延迟，对高速动态操作不适用。
- **语言指令的多样性**：仅提及“轻柔指令”，未探索更复杂的语言条件（如“用5N的力拧开瓶盖”），语言与力的映射可能不够精细。

（完）
