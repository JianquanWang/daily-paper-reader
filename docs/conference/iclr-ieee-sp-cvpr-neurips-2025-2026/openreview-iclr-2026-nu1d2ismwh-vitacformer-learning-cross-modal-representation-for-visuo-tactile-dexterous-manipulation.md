---
title: "ViTacFormer: Learning Cross-Modal Representation for Visuo-Tactile Dexterous Manipulation"
title_zh: ViTacFormer：学习视觉-触觉跨模态表示用于灵巧操作
authors: "Liang Heng, Haoran Geng, Kaifeng Zhang, Pieter Abbeel, Jitendra Malik"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Nu1D2IsmWH"
tags: ["query:tactile-vla"]
score: 8.0
evidence: 视觉-触觉跨模态表示学习用于灵巧操作
tldr: ViTacFormer提出跨注意力编码器融合高分辨率视觉与触觉，并结合自回归触觉预测头，通过易到难课程学习优化视觉-触觉潜在空间。在灵巧操作任务中显著提升了精度和鲁棒性，尤其适用于视觉遮挡场景，为触觉反馈的机器人学习提供了有效方法。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 灵巧操作需要触觉进行精细控制，但现有视觉方法在遮挡下性能下降。
method: 提出ViTacFormer，使用跨注意力编码器融合视觉触觉，并加入触觉预测头进行课程学习。
result: 在灵巧操作基准上达到SOTA，对遮挡和噪声具有强鲁棒性。
conclusion: 视觉-触觉联合表示显著提升灵巧操作性能，触觉预测作为辅助任务有效。
---

## Abstract
Dexterous manipulation is a cornerstone capability for robotic systems aiming to interact with the physical world in a human-like manner. Although vision-based methods have advanced rapidly, tactile sensing remains crucial for fine-grained control—particularly in unstructured or visually occluded settings. We present ViTacFormer, a representation-learning approach that couples a cross-attention encoder to fuse high-resolution vision and touch with an autoregressive tactile-prediction head that anticipates future contact signals. Building on this architecture, we devise an easy-to-challenging curriculum that steadily refines the visual-tactile latent space, boosting both accuracy and robustness. The learned cross-modal representation drives imitation learning for multi-fingered hands, enabling precise and adaptive manipulation. Across a suite of challenging real-world benchmarks, our method achieves approximately 50% higher success rates than prior state-of-the-art systems. To our knowledge, it is also the first to autonomously complete long-horizon dexterous manipulation tasks that demand highly precise control with an anthropomorphic hand—successfully executing up to 11 sequential stages and sustaining continuous operation for 2.5 minutes.

---

## 论文详细总结（自动生成）

# 论文详细总结：ViTacFormer: 学习视觉-触觉跨模态表示用于灵巧操作

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：灵巧操作是机器人实现类人交互的关键能力。虽然纯视觉方法发展迅速，但在非结构环境或视觉遮挡场景下，触觉感知对于精细控制至关重要。现有视觉-触觉融合方法存在分辨率低、融合不充分、难以处理长程任务等问题。
- **整体含义**：本文提出 ViTacFormer，通过跨注意力编码器融合高分辨率视觉与触觉信号，并结合自回归触觉预测头和易到难课程学习，显著提升多指灵巧手在复杂操作任务中的成功率和鲁棒性，首次实现了长达 2.5 分钟、11 个连续阶段的自主灵巧操作。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：学习联合的视觉-触觉跨模态表示，通过预测未来触觉信号辅助表征学习，并采用课程学习逐步优化潜在空间，最终驱动模仿学习进行灵巧操作。
- **关键技术细节**：
  - **跨注意力编码器（Cross-Attention Encoder）**：分别编码高分辨率视觉图像和触觉信号，通过跨注意力机制（cross-attention）实现模态间信息交互与融合，得到联合的视觉-触觉表征。
  - **自回归触觉预测头（Autoregressive Tactile-Prediction Head）**：作为辅助任务，基于当前状态和动作历史自回归地预测未来触觉接触信号。该预测头在训练时与主任务（模仿学习）联合优化，促使潜在空间编码时间序列触觉动态。
  - **易到难课程学习（Easy-to-Challenging Curriculum）**：训练过程中逐步增加任务难度（如遮挡程度、操作精度要求），使模型从简单场景开始学习，逐步适应复杂场景，从而提升最终鲁棒性。
- **整体流程**（文字说明）：
  1. 输入：高分辨率视觉图像 + 当前触觉信号 → 跨注意力编码器 → 联合表示；
  2. 联合表示同时传递给：① 策略网络（模仿学习，输出动作）；② 触觉预测头（输出未来触觉）；
  3. 训练损失：模仿学习损失 + 触觉预测损失；
  4. 课程学习：按难度递增顺序采样训练样本。

## 3. 实验设计

- **数据与场景**：在真实世界的多指灵巧手平台上进行，包含一系列具有挑战性的操作基准任务。文中提及“a suite of challenging real-world benchmarks”，但未列出具体任务名称或数据集细节。
- **Benchmark**：与前人 SOTA 系统在相同任务上对比，成功率提升约 50%。此外，首次完成长时程（11个连续阶段，2.5 分钟）灵巧操作任务（如使用拟人手的精细装配）。
- **对比方法**：对比了 prior state-of-the-art systems（未具体点名），推测包括纯视觉方法、简单融合方法（如直接拼接）等。消融实验可能包括：移除触觉预测头、移除课程学习、替换跨注意力为其他融合方式等。

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据中未提及 GPU 型号、数量、训练时长、参数量等信息。因此无法总结算力消耗。可能需要在完整论文中查找。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，至少包含：
  - 主要实验：在多个真实世界基准上与 prior SOTA 对比（成功率提升 50%）；
  - 长程任务演示：11 个阶段、2.5 分钟的连续操作；
  - 消融实验：应包含对跨注意力、触觉预测头、课程学习等组件的消融（隐含在方法论证中）。
- **充分性与公平性**：
  - 真实世界基准具有挑战性，对比 SOTA 提升显著，结果有说服力。
  - 但缺少详细的实验设置（相同种子、硬件配置、重复次数、统计显著性检验）说明，仅凭成功率数值难以完全判断公平性。文中提到“to our knowledge, it is also the first to autonomously complete long-horizon...”，表明长程任务是首次实现，但具体对比基线可能不完整。
  - 总体而言，实验设计合理，但客观性有待补充更多细节。

## 6. 主要结论与发现

- **主要结论**：ViTacFormer 通过跨注意力融合视觉和触觉，并引入触觉预测自监督任务和课程学习，显著提升了灵巧操作的成功率和鲁棒性，尤其在视觉遮挡场景下表现突出。
- **发现**：
  - 视觉-触觉联合表示比纯视觉或简单融合具有实质性优势。
  - 触觉预测作为辅助任务有助于学习更好的时序动态表征。
  - 课程学习有效提升了模型在复杂任务上的泛化能力。
  - 模型首次实现了长达 2.5 分钟、11 个连续阶段的自主灵巧操作，展示了长程精细控制能力。

## 7. 优点（方法与实验亮点）

- **方法亮点**：
  - 跨注意力机制实现了高效的视觉-触觉模态对齐与融合，优于简单拼接或相加。
  - 自回归触觉预测头是一种新颖的自监督辅助任务，使潜在空间包含未来触觉动态，增强时序建模。
  - 易到难课程学习设计简单有效，无需人工设计复杂课程。
- **实验亮点**：
  - 真实世界多指灵巧手平台，任务难度高且贴近实际应用。
  - 首次完成 11 阶段长程操作，展示系统的可靠性和鲁棒性。
  - 成功率提升 50% 的显著增益，具有实际意义。

## 8. 不足与局限

- **实验覆盖**：未提供具体任务描述、失败案例分析、不同遮挡程度或噪声水平的系统评估；缺少 Sim-to-Real 迁移验证（仅真实世界实验）；未与其他多模态架构（如使用 Transformer 的其他融合方案）进行充分对比。
- **偏差风险**：可能的过拟合风险——课程学习依赖难度标定，若标定不准确可能影响结果；触觉预测头依赖于未来触觉真值，训练时需额外传感器，限制了在无法获取触觉预测真值的场景下的推广。
- **应用限制**：
  - 要求配备高分辨率触觉传感器（如 GelSight 等），硬件成本较高。
  - 训练需要长时间序列触觉数据，数据采集成本高。
  - 长时程任务的成功率可能受累积误差影响，文中未分析误差传播。
- **资源与复现**：未公开代码、模型权重或详细超参数，且未说明算力要求，增加了复现难度。

（完）
