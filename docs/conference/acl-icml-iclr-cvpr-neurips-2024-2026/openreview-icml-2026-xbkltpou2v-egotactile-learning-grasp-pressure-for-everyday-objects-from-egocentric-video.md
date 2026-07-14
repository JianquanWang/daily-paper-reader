---
title: "EgoTactile: Learning Grasp Pressure for Everyday Objects from Egocentric Video"
title_zh: EgoTactile：从第一人称视频学习日常物体的抓取压力
authors: "Yuan Zeng, Yujia Shi, Tiao Tan, Xingting Li, Yaqi Qin, Zongqing Lu, Wenming Yang, Jing-Hao Xue, Qingmin Liao"
date: 2026-04-30
pdf: "https://openreview.net/pdf/b02faf175af988d2c77293bf0c703db9aca7bfee.pdf"
tags: ["query:tactile-vla"]
score: 7.0
evidence: 从第一人称视频估计全手抓取压力，多模态触觉感知
tldr: EgoTactile构建了第一人称视频与全手抓取压力对应的基准数据集，覆盖日常物体，并提出EgoPressureFormer和EgoPressureDiff方法从视频中估计触觉压力，解决了现有方法局限于平面或指尖接触的问题，为机器人多模态触觉感知和抓取控制提供了视觉驱动的触觉推理途径。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 从第一人称视频估计全手抓取压力对沉浸式VR和机器人操作至关重要，但现有方法依赖侵入式硬件或局限于简单场景。
method: 提出EgoTactile基准，配对第一人称视频与全手压力真值，并设计了EgoPressureFormer判别基线及EgoPressureDiff扩散模型处理观测不确定性。
result: 在多种日常物体上验证了方法有效性，且裸手迁移子集展现了自然场景泛化能力。
conclusion: EgoTactile为从视觉推断触觉压力提供了基准和方法，支撑多模态触觉感知研究。
---

## Abstract
Estimating full-hand grasp pressure from egocentric video is critical for immersive VR and robotic manipulation, yet dense tactile sensing often relies on intrusive hardware. 
Existing vision-based methods predominantly rely on planar surfaces or fingertip contacts, failing to generalize to complex 3D object interactions. 
Therefore, we introduce EgoTactile, a benchmark pairing egocentric video with full-hand pressure supervision for diverse everyday objects, incorporating a bare-hand transfer subset to enable generalization to natural scenarios. 
Leveraging this benchmark, we first establish EgoPressureFormer as a discriminative baseline. Beyond this, to explicitly address the uncertainty in partial observations, we propose EgoPressureDiff, a conditional diffusion framework that adapts a large-scale pre-trained video diffusion backbone. By combining rich world knowledge priors with a Physically-Informed Feature Rectification layer to inject semantic constraints, our approach effectively hallucinates plausible contact patterns and resolves visual-physical ambiguities. 
Extensive experiments demonstrate that our method achieves superior performance on the benchmark and robust transferability to in-the-wild scenarios. Our project page is at https://egotactile.github.io/.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：从第一人称视频中估计全手抓取压力对于沉浸式VR交互和机器人灵巧操作至关重要，但现有的密集触觉传感方法通常依赖侵入式硬件（如传感手套），而基于视觉的方法大多局限于平面接触或指尖接触，难以推广到复杂的3D物体交互场景。
- **背景**：缺乏大规模的第一人称视频与全手压力真值配对的数据集，使得视觉驱动的触觉推理研究受限。现有方法无法处理部分观测的不确定性以及视觉与物理之间的歧义。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个配对第一人称视频与全手抓取压力真值的基准数据集（EgoTactile），并设计两种方法从视频中推断压力分布：一种判别式基线（EgoPressureFormer）和一种生成式扩散模型（EgoPressureDiff），后者利用大规模预训练视频扩散先验来显式处理部分观测的不确定性。
- **关键技术细节**：
  - **EgoPressureFormer**：作为判别式基线，直接学习视频特征到压力图的映射。
  - **EgoPressureDiff**：基于条件扩散框架，采用大规模预训练的视频扩散骨干作为基础模型，并引入**Physically-Informed Feature Rectification (PIFR)** 层，用于注入物理语义约束（如接触力学的一致性），从而在视觉模糊或遮挡情况下合理“幻想”出物理合理的接触模式。
- **没有提供明确的公式或算法流程图**，但该方法本质上是将扩散模型的条件生成能力与物理先验相结合。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：作者构建了**EgoTactile基准数据集**，包含第一人称视角下对多种日常物体的抓取视频，以及对应的全手压力真值。此外，还特别设置了**裸手迁移子集**，用于评估方法在自然场景（无传感手套）下的泛化能力。
- **基准与对比**：
  - 基准方法包括自身提出的判别式基线**EgoPressureFormer**。
  - 未明确列出其他外部对比方法（可能因为这是首次提出该任务），但通过与EgoPressureFormer的对比来验证扩散模型的有效性。
- **评估任务**：在多种日常物体上的压力预测性能，以及零样本迁移到野外（in-the-wild）场景。

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长。通常在ICML等顶会论文中，实验资源配置可能放在附录，但此处提供的文本不包含此信息。需要指出这一缺失。

### 5. 实验数量与充分性

- **实验数量**：根据摘要描述，进行了“extensive experiments”，包括基准数据集上的性能验证和裸手迁移子集的泛化测试。但未给出具体的实验组数（如不同物体类别、不同环境光照、不同抓取姿态下的细分实验）。
- **充分性判断**：
  - 正面：包含基准测试和迁移测试，初步验证了方法的有效性和泛化性。
  - 不足：缺乏与传统触觉传感方法（如实际压力手套）的直接量化对比；未讨论不同视频帧率、遮挡程度等影响因素；消融实验未在摘要中体现（可能正文中有），但根据当前文本无法完全评估实验的全面性。

### 6. 论文的主要结论与发现

- EgoTactile基准填补了从第一人称视频估计全手抓取压力的空白，为多模态触觉感知研究提供了支撑。
- 所提出的EgoPressureDiff（条件扩散框架）在基准上取得了优于判别式基线的性能，并且能够鲁棒地泛化到野外真实场景。
- 物理信息特征修正层（PIFR）有效解决了视觉-物理歧义，提升了接触模式还原的物理合理性。

### 7. 优点

- **新颖性**：首次构建第一人称视频与全手压力真值的配对数据集，超越了之前仅限平面或指尖接触的工作。
- **方法创新**：引入大规模预训练视频扩散骨干到触觉估计任务，结合物理先验，利用生成模型的内在不确定性建模能力，有效应对视觉遮挡和模糊。
- **泛化设计**：包含裸手迁移子集，使得方法可摆脱传感手套限制，更贴近实际应用。

### 8. 不足与局限

- **实验覆盖**：未详细报告不同物体材质、不同抓取力度下的性能变化；迁移测试的野外场景多样性描述不够具体。
- **偏差风险**：压力真值可能通过侵入式传感手套获取，裸手迁移子集是否真的完全无传感器干扰？标注过程中可能存在系统偏差。
- **应用限制**：方法依赖第一人称视频的稳定拍摄，在剧烈运动或严重遮挡下可能失效；扩散模型推理速度较慢，不适合实时应用。
- **未提供算力成本**，不利于研究者复现或评估资源需求。

（完）
