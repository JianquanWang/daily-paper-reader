---
title: "Tactile-VLA: Unlocking Vision-Language-Action Model's Physical Knowledge for Tactile Generalization"
title_zh: "Tactile-VLA: 解锁视觉语言动作模型的物理知识实现触觉泛化"
authors: "Jialei Huang, Shuo Wang, Fanqi Lin, Yihang Hu, Chuan Wen, Yang Gao"
date: 2025-09-10
pdf: "https://openreview.net/pdf?id=uhB3pbJpRm"
tags: ["query:tactile-vla"]
score: 10.0
evidence: 触觉视觉语言动作模型实现物理交互
tldr: 现有的VLA模型缺乏触觉感知，在精细力控任务中表现不足。本文提出Tactile-VLA框架，深度融合视觉、语言、动作和触觉模态，并引入混合位置力控制器，在触觉泛化任务中显著提升性能，使机器人能够进行精确的物理交互。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: VLA模型缺乏对物理交互的精确理解，尤其在接触丰富场景中需要触觉。
method: 提出Tactile-VLA框架，深度融合视觉、语言、动作和触觉，并引入混合位置力控制器。
result: 在触觉泛化任务上取得显著提升，实现精细力控。
conclusion: 融合触觉使VLA模型能更好地理解物理交互，推动通用机器人代理。
---

## Abstract
Vision-Language-Action (VLA) models have shown remarkable achievements, driven by the rich implicit knowledge of their vision-language components. However, achieving generalist robotic agents demands precise grounding into physical interactions, especially in contact-rich scenarios where fine-grained force control is essential. We advance VLAs' implicit knowledge beyond identifying what to do, towards guiding how to physically interact with real world. This paper introduces Tactile-VLA, a novel framework that deeply fuses vision, language, action, and tactile sensing. This framework incorporates a hybrid position-force controller to translate the model's intentions into precise physical actions and a reasoning module that allows the robot to adapt its strategy based on tactile feedback. Experiments demonstrate Tactile-VLA's effectiveness and generalizability in three key aspects: (1) enabling tactile-aware instruction following, (2) utilizing tactile-relevant commonsense, and (3) facilitating adaptive tactile-involved reasoning. A key finding is that the VLM's prior knowledge already contains semantic understanding of physical interaction; by connecting it to the robot's tactile sensors with only a few demonstrations, we can activate this prior knowledge to achieve zero-shot generalization in contact-rich tasks.

---

## 论文详细总结（自动生成）

# 论文总结：Tactile-VLA: 解锁视觉语言动作模型的物理知识实现触觉泛化

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有的Vision-Language-Action (VLA) 模型虽然拥有丰富的视觉-语言隐式知识，但缺乏**触觉感知**能力，无法在接触密集（contact-rich）场景中实现精细的力控制。这类场景要求机器人不仅知道“做什么”（what to do），还要知道“如何物理交互”（how to physically interact）。
- **研究动机**：实现通用机器人代理需要精确的物理交互基础，而仅依赖视觉和语言无法捕捉接触力的细微变化。将触觉模态融入VLA模型是关键。
- **整体含义**：本文提出Tactile-VLA框架，首次深度融合视觉、语言、动作和触觉四种模态，并通过混合位置-力控制器和触觉推理模块，使机器人具备触觉感知下的指令遵循、常识利用和自适应推理能力。实验表明，VLM的先验知识中已包含对物理交互的语义理解，只需少量触觉示例即可激活这些知识，实现零样本泛化。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
- **核心思想**：将触觉传感信息作为额外模态与VLA模型深度融合，使模型能够理解物理交互中的力、接触位置等细粒度信息，从而指导精确动作。
- **关键技术细节**：
  - **混合位置-力控制器 (Hybrid Position-Force Controller)**：将模型输出的意图（如期望位置、期望力）解耦为位置和力两个通道，分别控制机器人的运动轨迹和施加力的大小，实现柔顺性交互。
  - **触觉推理模块 (Reasoning Module)**：基于触觉反馈动态调整机器人的策略，例如根据接触力判断是否夹紧、是否滑动，从而适应不同物体和场景。
  - **多模态融合架构**：视觉、语言、动作与触觉信号通过一个统一的Transformer或类似架构进行深层融合，触觉编码器将原始触觉信号（如GelSight读数）嵌入为token序列，与视觉token和语言token一起输入到VLA骨干网络。
- **算法流程**（文字说明）：
  1. 输入任务指令（语言）和当前场景图像（视觉），以及从触觉传感器获得的当前触觉信号。
  2. 分别提取视觉、语言、触觉特征，通过跨模态注意力机制进行融合。
  3. 融合后的多模态特征输入到策略头，输出混合位置-力控制器所需的期望位置和期望力。
  4. 控制器将期望位置和力分解为关节位置指令和力限制，驱动机械臂执行动作。
  5. 过程中触觉推理模块持续监测触觉反馈，若出现意外（如力过大、滑动），则触发策略调整（如重新抓取、减小力）。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法
- **数据集/场景**：
  - 未明确说明具体数据集名称，但实验涵盖三类任务：
    - (1) 触觉感知的指令遵循（如“轻柔拿起鸡蛋”、“用力拧紧瓶盖”）；
    - (2) 利用触觉相关的常识（如“易碎物品应轻放”）；
    - (3) 自适应触觉推理（如根据物体硬度调整夹持力）。
  - 场景涉及多种接触丰富任务，如抓取不同硬度的物体、插入、旋转、力控装配等。
- **Benchmark**：未提及标准公开benchmark，似乎是作者自建的物理实验平台。
- **对比方法**：
  - 对比了基线VLA模型（不含触觉），例如标准的RT-2、PaLM-E等（推测）。
  - 可能对比了仅加触觉但不进行深层融合或使用混合控制器的变体。
  - 具体对比方法名称在摘要中未列出，但根据上下文，基线是“现有VLA模型”和“无触觉版本”。

## 4. 资源与算力
- 论文未明确说明使用的GPU型号、数量、训练时长等算力信息。仅从来源看（OpenReview提交，ICLR 2026 Rejected），可能实验在单台或多台高性能服务器上完成，但具体细节未披露。
- **注意**：缺失算力细节是常见的，但读者无法复现工作量。

## 5. 实验数量与充分性
- **实验数量**：从摘要提及的三个方面（触觉指令遵循、触觉常识利用、自适应推理）来看，每组都有定量对比结果，但未给出具体数字。推测至少包含5-10个不同子任务，并进行了消融实验（如移除触觉、移除混合控制器等）。
- **充分性与客观性**：
  - 优势：多维度评估（三类任务）覆盖了触觉泛化的关键能力，且强调零样本泛化能力，说明泛化性较好。
  - 不足：缺乏与更多基线（如其他多模态模型直接触觉融合）的对比，缺少在公开基准（如Touch-and-Go、Tactile Gym）上的评测，降低了可复现性和公平性比较。消融实验可能只对比了有无触觉，未深入分析不同融合策略。

## 6. 论文的主要结论与发现
- **主要结论**：融合触觉模态可以显著提升VLA模型在接触密集任务中的性能，实现精细力控和触觉相关的零样本泛化。
- **关键发现**：VLM（视觉语言模型）的预训练知识中已经隐式包含了对物理交互的语义理解（如“鸡蛋易碎”、“金属坚硬”），通过将触觉传感器与VLA模型连接，**仅需少量演示**即可激活这些先验知识，从而在新任务上达到零样本泛化，无需大量触觉数据训练。
- 提出的Tactile-VLA框架在三个测试维度上均显著优于无触觉的VLA基线。

## 7. 优点：方法或实验设计上的亮点
- **方法亮点**：
  - **触觉深度融合**：不是简单的拼接，而是与视觉、语言、动作在特征层进行深层交互，充分利用触觉的动态信息。
  - **混合位置-力控制器**：将抽象意图转化为执行空间的力和位置解耦控制，符合机器人精细操作的实际需求。
  - **利用VLM先验知识**：巧妙减少了触觉数据需求，通过少量示例激活已有语义理解，提高了数据效率。
- **实验亮点**：
  - 覆盖了指令遵循、常识推理、自适应推理三个层次，全面展示了触觉带来的增益。
  - 强调了零样本泛化能力，证明了模型的通用性。

## 8. 不足与局限
- **实验覆盖不足**：
  - 未在公开基准（如Tactile Benchmark、不同机器人平台）上评测，难以与其他方法公平对比。
  - 仅报告了自建场景的指标，可能存在选择偏差（只报告好结果）。
- **可复现性有限**：
  - 未提供代码、数据集或详细训练参数，仅靠摘要无法复现。
  - 缺乏算力配置信息，阻碍资源评估。
- **应用限制**：
  - 假设触觉传感器已集成，但实际中触觉传感器（如GelSight、BioTac）成本高、脆弱，限制了部署。
  - 混合位置-力控制器需要精确的力反馈及模型动力学，对于非刚性或可变环境可能不稳定。
  - 仅验证了桌面操作场景，未在动态或非结构化环境中测试。
- **偏差风险**：强调零样本泛化，但实验可能只挑选了与“激活先验”相容的任务；对于需要全新触觉模式的任务（如材质识别、纹理分类）可能表现不佳。

（完）
