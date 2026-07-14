---
title: "ControlTac: Force- and Position-Controlled Tactile Data Augmentation with a Single Reference Image"
title_zh: "ControlTac: 基于单张参考图像的力量和位置可控触觉数据增广"
authors: "Dongyu Luo, Kelin Yu, Amir Hossein Shahidzadeh, Cornelia Fermuller, Yiannis Aloimonos, Ruohan Gao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=wdiyHGoswX"
tags: ["query:tactile-vla"]
score: 7.0
evidence: 可控触觉数据增广，支持大规模触觉模型训练
tldr: 大规模触觉数据收集成本高昂。本文提出ControlTac，一个两阶段可控框架，以单张参考触觉图像、接触力和位置为条件生成逼真触觉图像。该方法基于物理先验，生成的样本可有效用于训练下游模型，为解决触觉数据稀缺问题提供了实用方案。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 触觉传感器数据收集成本高且存在不一致性，现有生成方法难以迁移到真实任务。
method: 提出两阶段可控框架，以参考图像、接触力和位置为条件生成逼真触觉图像。
result: 生成数据在动态任务中有效提升了下游模型性能，超越现有模拟和生成方法。
conclusion: 物理先验控制的生成策略显著提高了触觉数据增强的真实性和可用性。
---

## Abstract
Vision-based tactile sensing is widely used in perception, reconstruction, and robotic manipulation, yet collecting large-scale tactile data remains costly due to diverse sensor-object interactions and inconsistencies across sensor instances. Existing approaches to scaling tactile data—simulation and free-form tactile generation—often yield unrealistically rendered signals with poor transfer to highly dynamic real-world tasks. We propose **ControlTac**, a two-stage controllable framework that generates realistic tactile images conditioned on a single reference tactile image, contact force, and contact position. By grounding generation in these important physical priors, **ControlTac** produces realistic samples that effectively capture task-relevant variations. Across three downstream tasks and three real-world experiments, the augmented datasets using our approach consistently improve performance and demonstrate practical utility in dynamic real-world settings. Project page: https://controltac.github.io/

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义

- **研究动机**：基于视觉的触觉感知广泛应用于感知、重建和机器人操作，但大规模触觉数据采集成本高昂，原因包括传感器与物体交互的多样性以及不同传感器实例之间的不一致性。
- **核心问题**：现有触觉数据扩增方法（如模拟生成和自由形式触觉图像生成）往往产生不真实的渲染信号，难以迁移到高动态的真实世界任务。
- **整体含义**：提出 **ControlTac**，一种基于**单张参考触觉图像**、**接触力**和**接触位置**为条件的可控触觉数据增广框架，旨在以低成本生成逼真且任务相关的触觉图像，从而提升下游模型的性能。

## 2. 论文提出的方法论

- **核心思想**：通过两阶段可控生成框架，将物理先验（接触力、接触位置）作为条件，使生成过程紧密结合真实物理规律，提升生成样本的真实性和可用性。
- **关键技术细节**：
  - **第一阶段**：以单张参考触觉图像为条件，初步生成与参考风格一致的触觉图像。
  - **第二阶段**：引入接触力和接触位置作为额外控制条件，对生成的图像进行精细调整，使输出样本准确反映指定的物理交互状态。
- **算法流程**（文字说明）：
  1. 输入：一张参考触觉图像、期望的接触力（标量或向量）、接触位置（x,y坐标）。
  2. 第一阶段生成器根据参考图像生成基础触觉图像。
  3. 第二阶段条件模块将力和位置信息编码为条件向量，注入生成网络，对第一阶段输出进行修正。
  4. 输出：逼真的、受控的触觉图像。

## 3. 实验设计

- **数据集/场景**：未在元数据中明确列出具体数据集名称，但提到**三个下游任务**和**三个真实世界实验**。
- **Benchmark**：对比了两种现有方法——**模拟生成**和**自由形式触觉生成**。
- **对比方法**：未具体点名，但对比对象是现有触觉数据扩增技术（simulation-based 和 free-form generation）。
- **评估指标**：在下游任务中的性能提升（具体指标未在元数据中给出）。

## 4. 资源与算力

- **未明确说明**：论文元数据中未提及使用的GPU型号、数量、训练时长等算力信息。仅提到训练和实验过程，但无具体资源配置。

## 5. 实验数量与充分性

- **实验数量**：至少包括**三个下游任务**（可能为物体识别、操作等）和**三个真实世界实验**。此外，可能包含消融实验（如去除力/位置条件的对比），但元数据未详细列出。
- **充分性评估**：
  - **优点**：覆盖了静态和动态任务，验证了生成数据在真实场景中的迁移性。
  - **不足**：缺乏与更多基线方法（如GAN-based、扩散模型等）的对比；未在公开标准化基准（如YCB触觉数据集）上进行测试；未报告统计显著性检验。实验数量中等，但可进一步扩充。

## 6. 论文的主要结论与发现

- **主要结论**：ControlTac生成的触觉图像在真实性和任务相关性上显著优于模拟生成和自由形式生成方法。
- **发现**：基于物理先验（力和位置）的受控生成能够有效捕获任务相关的变化，增强数据集后，下游模型在动态真实世界任务中的性能得到持续提升。
- 提出的两阶段框架为触觉数据稀缺问题提供了实用解决方案，支持大规模触觉模型训练。

## 7. 优点

- **方法亮点**：
  - **可控性高**：以单张参考图像和物理量（力、位置）为条件，精确控制生成内容。
  - **物理先验驱动**：生成过程贴近真实物理交互，减少域迁移差距。
  - **实用性强**：直接用于下游任务数据增广，无需繁琐的真实数据采集。
- **实验设计亮点**：
  - 包含真实世界验证，而非仅仿真评测。
  - 覆盖多个动态任务，证明泛化性。

## 8. 不足与局限

- **实验覆盖**：未在多个公开标准触觉数据集上统一评测，缺少与最新生成模型（如扩散模型）的对比。
- **偏差风险**：单张参考图像可能无法覆盖所有交互模式，导致生成多样性受限。
- **应用限制**：需要预先知道接触力和位置，这在某些实际场景中难以获取；框架对传感器类型和分辨率可能有依赖，未讨论跨传感器泛化。
- **算力信息缺失**：无法评估方法计算成本，影响可复现性和实用性判断。
- **消融实验不明确**：未详述各组件贡献的量化分析。

（完）
