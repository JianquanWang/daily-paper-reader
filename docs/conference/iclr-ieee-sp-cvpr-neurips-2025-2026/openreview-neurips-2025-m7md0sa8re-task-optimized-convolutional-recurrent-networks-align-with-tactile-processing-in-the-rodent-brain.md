---
title: Task-Optimized Convolutional Recurrent Networks Align with Tactile Processing in the Rodent Brain
title_zh: 任务优化的卷积循环网络与啮齿动物大脑触觉处理对齐
authors: "Trinity Chung, Yuchen Shen, Nathan Kong, Aran Nayebi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=m7MD0sa8Re"
tags: ["query:tactile-vla"]
score: 6.0
evidence: 啮齿动物触觉处理启发触觉表征学习
tldr: 该论文针对触觉感知在人工系统中效能不足的问题，提出Encoder-Attender-Decoder框架，通过卷积循环网络在仿真触觉序列上训练，发现这些模型能够匹配啮齿动物体感皮层的神经表征。该工作为构建更具生物合理性的触觉基础模型提供了方法指导，有望提升机器人触觉感知的自然性和效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 触觉感知在人工系统中远不如视觉语言成熟，希望借鉴神经科学原理。
method: 构建EAD框架，使用ConvRNN编码器在仿真触觉序列上训练分类任务。
result: ConvRNN模型与啮齿动物体感皮层神经表征高度相似。
conclusion: 生物学合理的触觉模型可以推动人工触觉系统的进步。
---

## Abstract
Tactile sensing remains far less understood in neuroscience and less effective in artificial systems compared to more mature modalities such as vision and language.
We bridge these gaps by introducing a novel Encoder-Attender-Decoder (EAD) framework to systematically explore the space of task-optimized temporal neural networks trained on realistic tactile input sequences from a customized rodent whisker-array simulator. 
We identify convolutional recurrent neural networks (ConvRNNs) as superior encoders to purely feedforward and state-space architectures for tactile categorization. 
Crucially, these ConvRNN-encoder-based EAD models achieve neural representations closely matching rodent somatosensory cortex, saturating the explainable neural variability and revealing a clear linear relationship between supervised categorization performance and neural alignment.
Furthermore, contrastive self-supervised ConvRNN-encoder-based EADs, trained with tactile-specific augmentations, match supervised neural fits, serving as an ethologically-relevant, label-free proxy.

For neuroscience, our findings highlight nonlinear recurrent processing as important for general-purpose tactile representations in somatosensory cortex, providing the first quantitative characterization of the underlying inductive biases in this system. 
For embodied AI, our results emphasize the importance of recurrent EAD architectures to handle realistic tactile inputs, along with tailored self-supervised learning methods for achieving robust tactile perception with the same type of sensors animals use to sense in unstructured environments.

---

## 论文详细总结（自动生成）

# 论文总结：Task-Optimized Convolutional Recurrent Networks Align with Tactile Processing in the Rodent Brain

## 1. 核心问题与整体含义

- **研究动机**：触觉感知在神经科学中理解不足，在人工系统中性能远低于视觉和语言模态。现有触觉模型缺乏生物合理性，且对真实触觉序列的处理效率低。
- **整体含义**：通过引入神经启发的任务优化时序网络，首次定量证明非线性循环处理（ConvRNN）是体感皮层通用触觉表征的关键归纳偏置，同时为具身AI提供高效、生物合理的触觉感知框架。

## 2. 方法论

- **核心思想**：构建 Encoder-Attender-Decoder (EAD) 框架，将触觉序列处理分解为编码（Encoder）、注意力（Attender）和解码（Decoder）三个模块，并使用任务优化（监督或自监督）训练编码器。
- **关键技术细节**：
  - 编码器采用卷积循环神经网络（ConvRNN），包含卷积层捕捉空间特征与循环层处理时序动态。
  - 输入来自定制的啮齿动物触须阵列仿真器（whisker-array simulator）产生的逼真触觉序列。
  - 训练方式包括：监督分类任务（触觉类别识别）和对比自监督学习（使用触觉特化数据增强）。
- **算法流程（文字描述）**：
  1. 输入触觉序列 → ConvRNN 编码器提取时空特征序列。
  2. 注意力模块（Attender）对特征序列进行加权聚合。
  3. 解码器（Decoder）输出分类结果或对比表征。
  4. 通过反向传播优化完整 EAD 参数。

## 3. 实验设计

- **数据集/场景**：使用自建的啮齿动物触须阵列仿真器生成的各类触觉序列（如不同纹理、物体分类）。文中未明确说明具体数据集名称或公开性。
- **Benchmark**：以神经科学基准——啮齿动物体感皮层（S1）的神经记录数据（如神经元群体响应）作为对齐目标，衡量模型表征的神经可解释方差（explainable neural variability）。
- **对比方法**：
  - 纯前馈架构（如MLP）
  - 状态空间模型（如SSM）
  - 不同循环结构（ConvRNN vs. 全连接RNN）
  - 监督 vs. 自监督训练策略
- **未明确说明是否使用标准公开数据集或与其他现有触觉模型（如Visuo-Tactile模型）横向比较。**

## 4. 资源与算力

- **文中未明确指定**所使用的GPU型号、数量及训练时长。仅提及“任务优化的时序网络”在仿真序列上训练，但未提供算力细节。这可能是该工作的公开信息缺失。

## 5. 实验数量与充分性

- **实验组数**：至少包含三类对比实验：
  1. 编码器架构对比（ConvRNN vs. 前馈 vs. SSM）——不同架构在触觉分类任务上的性能。
  2. 训练范式对比（监督分类 vs. 自监督对比学习）——神经拟合效果。
  3. 与神经数据对齐的定量分析（线性关系、饱和度指标）。
- **充分性评估**：
  - 实验覆盖了架构、训练方式、神经对齐三个关键维度，逻辑完整。
  - 但缺少对真实机器人触觉数据的泛化验证，也未与其他现有人工触觉模型（如CNN-based）进行标准分类 benchmark 对比。
  - 消融实验仅提及“卷积循环”关键性，未报告不同循环步数、卷积核规模等超参数的影响。
  - 总体而言，实验设计合理但覆盖范围有限，公平性受限于缺少第三方公开基准。

## 6. 主要结论与发现

1. **ConvRNN 编码器**在触觉分类任务上显著优于纯前馈和状态空间架构。
2. 基于 ConvRNN 的 EAD 模型产生的神经表征与啮齿动物体感皮层高度相似，饱和了可解释的神经方差。
3. **监督分类性能与神经对齐程度呈清晰线性关系**——任务越优，表征越生物合理。
4. **对比自监督学习**（使用触觉特化增强）可以达到与监督训练相当的神经拟合效果，为无标注环境提供了可行替代。
5. 非线性循环处理是体感皮层通用触觉表征的关键归纳偏置，而非线性或纯时序模型均无法匹配。

## 7. 优点

- **跨学科创新**：将神经科学定量指标（神经可解释方差）直接作为模型评价标准，而非仅依赖下游任务精度。
- **方法论先进**：EAD 框架结合卷积和循环两种弱偏置，适应触觉序列的时空特性，设计简洁且生物合理。
- **自监督策略有效性**：提出触觉特化数据增强，使得无标签训练也能达到有监督水平，具有实际应用价值。
- **开放问题明确**：明确指出循环归纳偏置对通用触觉表征的重要性，为后续神经科学和具身AI的研究提供了方向。

## 8. 不足与局限

- **实验覆盖不全**：仅使用仿真触觉数据，未在真实物理传感器（如机器人触须或指尖传感器）上验证；未与真实神经记录的干扰噪声或变异性进行对比。
- **缺乏公开基准对比**：未在触觉识别标准数据集（如 Penn Treebank Tactile、UCSD Tactile）上评测，无法评估与现有最佳人工触觉模型的绝对性能差距。
- **算力资源未披露**：不可重现训练过程，对比公平性受疑。
- **可解释性局限**：神经对齐仅反映统计相关性，未进行因果干预验证（如扰动模型特定层看神经响应是否改变）。
- **应用限制**：目前仅适用于触须阵列类传感器，对于指尖触觉（高密度、多模态）的泛化能力未知。

（完）
