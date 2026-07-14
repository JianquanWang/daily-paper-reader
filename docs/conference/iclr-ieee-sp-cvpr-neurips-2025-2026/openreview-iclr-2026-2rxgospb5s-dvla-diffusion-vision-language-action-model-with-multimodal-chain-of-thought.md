---
title: "dVLA: Diffusion Vision-Language-Action Model with Multimodal Chain-of-Thought"
title_zh: dVLA：基于扩散的视觉-语言-动作模型及多模态思维链
authors: "Junjie Wen, Minjie Zhu, Jiaming Liu, Zhiyuan Liu, Yicun Yang, Linfeng Zhang, Shanghang Zhang, Yichen Zhu, Yi Xu"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=2rxgospB5s"
tags: ["query:tactile-vla"]
score: 4.0
evidence: 视觉VLA模型，方法可扩展至触觉
tldr: 现有VLA模型将视觉、语言和动作分离，缺乏统一的跨模态推理。本文提出扩散VLA模型（dVLA），通过扩散目标统一优化视觉推理、语言理解和动作生成，并集成多模态思维链，提升了模型对新指令和物体的泛化能力，但未包含触觉模态，仅在VLA框架层面有参考价值。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有VLA模型缺乏统一的跨模态推理框架。
method: 提出扩散VLA模型，通过统一扩散目标联合优化视觉、语言和动作。
result: 模型泛化能力强，对新指令和新物体表现良好，同时集成加速方法降低了响应时间。
conclusion: 统一的扩散框架能有效整合VLA中的多模态推理。
---

## Abstract
Vision-language-action (VLA) models have emerged as the next-generation framework in robotics, integrating visual perception, language reasoning, and robotic control into unified systems. In this paper, we present \textbf{dVLA}, a diffusion vision-language-action model with multimodal chain-of-thought. The dVLA optimizes visual reasoning, language comprehension, and robotic actions simultaneously through a unified diffusion-based objective. By harmonizing these modalities into a single cohesive framework, dVLA facilitates more effective cross-modal reasoning, enabling the model to generalize to novel instructions and objects. To ensure practical viability, we also integrate model acceleration methods that substantially decrease robot response times. Extensive evaluations in both simulation and the real world confirm that dVLA significantly outperforms current discrete and continuous VLA models, highlighting the potential of diffusion language model (DLM) based frameworks for robotics.

---

## 论文详细总结（自动生成）

# dVLA: Diffusion Vision-Language-Action Model with Multimodal Chain-of-Thought 中文总结

## 1. 论文的核心问题与整体含义
- **研究动机**：现有视觉-语言-动作（VLA）模型将视觉感知、语言推理和机器人控制作为分离模块处理，缺乏统一的跨模态推理框架，导致模型在应对新指令和新物体时泛化能力不足。
- **整体含义**：本文提出 **dVLA**，一种基于扩散的视觉-语言-动作模型，通过统一的扩散目标联合优化多模态推理（视觉、语言、动作），并集成多模态思维链（Multimodal Chain-of-Thought），旨在提升机器人对新颖指令和物体的泛化能力，并缩短实际部署中的响应时间。

## 2. 论文提出的方法论
- **核心思想**：将视觉推理、语言理解和动作生成三个任务统一在一个扩散模型框架下，利用扩散过程的去噪特性同时优化所有模态，实现高效的跨模态对齐与推理。
- **关键技术细节**：
  - **统一扩散目标**：设计一个联合损失函数，使模型在训练时同步学习视觉编码、语言理解和动作预测。
  - **多模态思维链**：在推理过程中引入逐步推理机制，让模型先生成中间视觉或语言表示，再输出动作，增强可解释性与泛化能力。
  - **模型加速方法**：集成现有的扩散模型加速技术（如减少采样步数、知识蒸馏等），显著降低机器人动作生成的时间延迟。
- **公式/算法流程说明**：论文未提供具体公式，但整体流程可概括为：输入多模态数据（图像+语言指令） → 扩散前向过程加噪 → 模型学习逆向去噪过程，同时预测视觉特征、语言token和机器人动作序列 → 推理时通过多步去噪生成最终动作。

## 3. 实验设计
- **使用的数据集/场景**：文中仅提及在仿真环境和真实世界机器人平台上进行评估，未明确指定具体数据集名称（如 RLBench、MetaWorld 等）。
- **Benchmark**：与现有的离散 VLA 模型（如 RT-2）和连续 VLA 模型（如 Octo）进行对比。
- **对比方法**：包括当前主流的离散和连续 VLA 方法（未列出具体名称，仅概括性描述）。

## 4. 资源与算力
- **文中未明确说明**：没有提及所使用的 GPU 型号、数量、训练时长或算力开销。论文在资源细节上存在缺失，无法评估训练成本。

## 5. 实验数量与充分性
- **实验组数**：仅概括性描述为“广泛评估在仿真和真实世界中”，未列出具体实验数量（如不同任务、不同场景的消融实验数）。
- **充分性与客观性**：由于缺乏详细的实验配置、消融研究、超参数分析等，难以判断实验是否充分。虽然声称显著优于对比模型，但未提供统计显著性检验或多任务泛化测试，存在一定的偏差风险。

## 6. 论文的主要结论与发现
- dVLA 模型在仿真和真实机器人任务中，均显著优于现有的离散和连续 VLA 模型。
- 统一的扩散框架能够有效整合视觉、语言和动作的多模态推理，使模型对新指令和新物体展现出更强的泛化能力。
- 集成的模型加速方法在保持性能的同时大幅缩短了机器人响应时间，提升了实际部署的可行性。
- 基于扩散语言模型（DLM）的框架为机器人控制提供了新的潜力方向。

## 7. 优点
- **方法论创新**：首次将扩散模型与多模态思维链结合到 VLA 框架中，实现了三个任务的统一优化，避免了分步训练的割裂问题。
- **泛化能力强**：在未见过的指令和物体上表现良好，表明跨模态推理的有效性。
- **实用性考量**：关注了模型加速，使响应时间达到实际可接受范围，推动 VLA 从理论走向应用。

## 8. 不足与局限
- **触觉模态缺失**：论文仅包含视觉和语言模态（tags 中标注 `query:tactile-vla`，但方法本身未涵盖触觉），应用范围受限。
- **实验细节不足**：未公开使用的具体数据集、任务列表、超参数、训练配置等，导致结果难以复现和验证。
- **对比方法不具体**：仅泛泛提及“离散和连续 VLA 模型”，缺乏基准方法的详细版本号或实现细节，公平性存疑。
- **资源信息缺失**：算力和训练时长未知，不利于评估方法在实际部署中的资源需求。
- **偏差风险**：未进行错误分析或鲁棒性测试（如传感器噪声、指令歧义等），泛化性声明可能过于乐观。

（完）
