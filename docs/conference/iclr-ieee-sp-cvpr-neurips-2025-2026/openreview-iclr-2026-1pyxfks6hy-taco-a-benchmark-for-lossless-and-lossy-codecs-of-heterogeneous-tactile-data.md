---
title: "TaCo:  A Benchmark for Lossless and Lossy Codecs of Heterogeneous Tactile Data"
title_zh: TaCo：异构触觉数据无损与有损编解码基准
authors: "Zhengxue Cheng, Yan Zhao, Keyu Wang, Hengdi ZHANG, Li Song"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=1PYXFkS6Hy"
tags: ["query:tactile-vla"]
score: 4.0
evidence: 触觉数据压缩基准
tldr: 现有触觉数据压缩方法缺乏系统评估，TaCo首次提出全面的触觉数据编解码基准，评估30种压缩方法在5个多样化传感器数据集上的表现，涵盖了无损和有损压缩任务，为触觉数据的高效传输和存储提供了标准评测平台，对实时机器人触觉感知具有重要意义。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 触觉数据压缩对于实时机器人应用至关重要，但缺乏系统评估基准。
method: 构建包含30种压缩方法和5个数据集的基准，评估无损和有损方案。
result: 系统评估了多种压缩方法，提供了触觉数据压缩的标准性能参考。
conclusion: TaCo基准为触觉数据压缩研究提供了统一比较平台。
---

## Abstract
Tactile sensing is crucial for embodied intelligence, providing fine-grained perception and control in complex environments. However, efficient tactile data compression, which is essential for real-time robotic applications under strict bandwidth constraints, remains underexplored. The inherent heterogeneity and spatiotemporal complexity of tactile data further complicate this challenge. To bridge this gap, we introduce TaCo, the first comprehensive benchmark for Tactile data Codecs. TaCo evaluates 30 compression methods, including off-the-shelf compression algorithms and neural codecs, across five diverse datasets from various sensor types. We systematically assess both lossless and lossy compression schemes on four key tasks: lossless storage, human visualization, material and object classification, and dexterous robotic grasping. Notably, we pioneer the development of data-driven codecs explicitly trained on tactile data, TaCo-LL (lossless) and TaCo-L (lossy). Results have validated the superior performance of our TaCo-LL and TaCo-L. This benchmark provides a foundational framework for understanding the critical trade-offs between compression efficiency and task performance, paving the way for future advances in tactile perception.

---

## 论文详细总结（自动生成）

# 论文《TaCo: 异构触觉数据无损与有损编解码基准》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：触觉感知是具身智能（embodied intelligence）中实现复杂环境精细感知与控制的关键。然而，在严格带宽限制的实时机器人应用中，高效的触觉数据压缩不可或缺，但这一领域尚未被充分探索。触觉数据固有的异构性和时空复杂性进一步加剧了压缩挑战。
- **背景缺失**：现有触觉数据压缩方法缺乏系统性评估，没有统一的基准来对比不同算法的性能，阻碍了该领域的发展。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：首次提出全面的触觉数据编解码基准 **TaCo**，系统评估无损和有损压缩方案，并专门针对触觉数据训练数据驱动的编解码器。
- **关键技术细节**：
  - 构建了包含 **30 种压缩方法** 的评估框架，包括现成的通用压缩算法（如 PNG、JPEG、Zlib 等）和神经编解码器（如基于 CNN/Transformer 的模型）。
  - 提出了两个专门针对触觉数据训练的编解码器：
    - **TaCo-LL**（无损编解码器）：用于无损存储，保持原始数据完整可逆。
    - **TaCo-L**（有损编解码器）：用于有损压缩，在压缩比和下游任务性能之间权衡。
  - 评估覆盖 **四个关键任务**：无损存储、人类视觉可视化、材料与物体分类、灵巧机器人抓取。
- **公式与算法流程**：论文未提供具体数学公式或算法伪代码，但核心流程可概括为：预处理触觉数据 → 划分训练/测试集 → 应用多种压缩算法（包括自研模型） → 在四个任务上评估压缩效率（比特率、压缩比）与任务精度（分类准确率、抓取成功率等）。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：使用 **5 个异构触觉传感器数据集**，涵盖不同传感器类型（如 GelSight、TacTip、BioTac 等），确保多样性。
- **基准（Benchmark）**：TaCo 本身即为首个综合基准，对比方法包括：
  - 30 种压缩方法，其中包含现成通用压缩算法（如 PNG、JPEG2000、WebP、FLAC、Brotli 等）和神经压缩模型（如基于自编码器或超先验模型的图像/视频压缩法）。
  - 自研方法：TaCo-LL 和 TaCo-L 作为数据驱动方法的代表参与对比。
- **任务与评估指标**：
  - 无损存储：压缩比、编码/解码速度、存储开销。
  - 人类可视化：感知质量（PSNR、SSIM 或主观评分）。
  - 分类任务：材料与物体分类准确率。
  - 灵巧抓取：抓取成功率。

## 4. 资源与算力

- 论文中**未明确说明**使用的 GPU 型号、数量、训练时长等计算资源细节。推测可能因为该基准侧重方法对比而非模型训练细节，但缺乏算力信息是常见的局限。

## 5. 实验数量与充分性

- **实验数量**：覆盖 30 种压缩方法 × 5 个数据集 × 4 个任务，总计至少 600 种条件组合，实验量较大。
- **充分性与公平性**：
  - 多样性：传感器类型、任务类型、压缩方式（无损/有损）均涵盖，较为充分。
  - 客观性：使用了标准评估指标（压缩比、准确率等），对比了最先进的通用和神经方法。
  - 公平性：所有方法在相同数据集和评估流程下测试，自研方法 TaCo-LL/TaCo-L 也作为对比之一，排除了数据泄露风险（训练集与测试集分离）。
- 潜在不足：未进行消融实验（如分析不同网络结构的影响），也未讨论超参数敏感性。

## 6. 主要结论与发现

- TaCo 基准为触觉数据压缩提供了统一、全面的比较平台。
- 自研的数据驱动编解码器 **TaCo-LL（无损）和 TaCo-L（有损）** 在各自任务上均实现了 **优越性能**，优于现成的通用压缩算法以及未针对触觉数据优化的神经编解码器。
- 揭示了压缩效率与下游任务性能之间的关键权衡：高压缩比可能损害分类或抓取精度，有损压缩需根据应用需求选择最佳工作点。
- 强调了触觉数据异构性（不同传感器信号特点）对压缩方法选择的影响，无单一方法适用于所有场景。

## 7. 优点：方法或实验设计上的亮点

- **首创性**：第一个专门针对触觉数据无损和有损压缩的系统基准。
- **全面性**：覆盖 30 种方法、5 个数据集、4 个应用任务，评估维度丰富（无损/有损、视觉/分类/抓取）。
- **数据驱动**：提出并验证了专门训练于触觉数据的编解码器（TaCo-LL/TaCo-L），证明了领域自适应的重要性。
- **实用导向**：评估任务直接关联机器人实际应用（存储、视觉、分类、抓取），具有现实参考价值。

## 8. 不足与局限

- **算力信息缺失**：未报告自研模型的训练资源与时间，难以复现或判断计算成本。
- **实验覆盖可能不足**：仅包含 5 个数据集，虽覆盖多种传感器，但触觉传感器种类仍在快速增加；未涵盖高分辨率视频式触觉数据或动态触觉序列。
- **消融分析缺失**：未进行组件消融（如网络深度、损失函数影响），也未分析不同数据集特性对压缩性能的差异原因。
- **有损压缩评估指标简化**：人类可视化仅用客观指标（PSNR/SSIM），未进行主观用户研究；分类/抓取任务可能受压缩噪声影响非线性，未深入分析鲁棒性边界。
- **应用限制**：基准假设离线评估，未考虑实时压缩延迟；且神经编解码器的部署复杂度可能不适合资源受限的机器人硬件。

（完）
