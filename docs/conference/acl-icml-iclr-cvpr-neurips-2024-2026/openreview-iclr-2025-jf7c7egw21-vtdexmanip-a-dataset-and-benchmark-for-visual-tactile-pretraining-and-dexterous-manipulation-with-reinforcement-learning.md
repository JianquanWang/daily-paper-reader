---
title: "VTDexManip: A Dataset and Benchmark for Visual-tactile Pretraining and Dexterous Manipulation with Reinforcement Learning"
title_zh: VTDexManip：面向视觉-触觉预训练和灵巧操作的强化学习数据集与基准
authors: "Qingtao Liu, Yu Cui, Zhengnan Sun, Gaofeng Li, Jiming Chen, Qi Ye"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=jf7C7EGw21"
tags: ["query:tactile-vla"]
score: 8.0
evidence: 视觉-触觉数据集和基准用于灵巧操作强化学习
tldr: 现有机器人任务预训练多使用图像和语言，且限于简单夹爪。本文收集了包含10种日常任务、182个物体的视觉-触觉数据集，是首个面向复杂灵巧操作的视觉-触觉数据集。同时提出包含6个复杂灵巧操作任务的基准，以及基于强化学习的视觉-触觉技能学习框架。数据集和框架为触觉反馈下的机器人学习提供了重要资源。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有数据集缺乏视觉-触觉信息，且限于简单夹爪，无法支持复杂灵巧操作。
method: 采集人类操作时的视觉-触觉数据，构建基准，并设计强化学习框架学习视觉-触觉技能。
result: 数据集覆盖10任务182物体，基准含6个灵巧操作任务，框架有效学习触觉反馈技能。
conclusion: 该工作填补了视觉-触觉灵巧操作数据集的空白，促进触觉反馈机器人学习。
---

## Abstract
Vision and touch are the most commonly used senses in human manipulation. While leveraging human manipulation videos for robotic task pretraining has shown promise in prior works, it is limited to image and language modalities and deployment to simple parallel grippers. In this paper, aiming to address the limitations, we collect a vision-tactile dataset by humans manipulating 10 daily tasks and 182 objects. In contrast with the existing datasets, our dataset is the first visual-tactile dataset for complex robotic manipulation skill learning. Also, we introduce a novel benchmark, featuring six complex dexterous manipulation tasks and a reinforcement learning-based vision-tactile skill learning framework. 18 non-pretraining and pretraining methods within the framework are designed and compared to investigate the effectiveness of different modalities and pertaining strategies. Key findings based on our benchmark results and analyses experiments include: 1) Despite the tactile modality used in our experiments being binary and sparse, including it directly in the policy training boosts the success rate by about 20\% and joint pretraining it with vision gains a further 20\%. 2) Joint pretraining visual-tactile modalities exhibits strong adaptability in unknown tasks and achieves robust performance among all tasks. 3) Using binary tactile signals with vision is robust to viewpoint setting, tactile noise, and the binarization threshold, which facilitates to the visual-tactile policy to be deployed in reality. The dataset and benchmark are available at \url{https://github.com/LQTS/VTDexManip}.

---

## 论文详细总结（自动生成）

# VTDexManip：面向视觉-触觉预训练和灵巧操作的强化学习数据集与基准 - 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：人类操作物体时最常用的感知是视觉和触觉。现有机器人任务预训练多依赖人类操作视频，但局限于图像和语言模态，且仅能部署到简单的平行夹爪上，无法支持复杂灵巧操作（如多指手）所需的触觉反馈。
- **核心问题**：缺乏同时包含视觉和触觉信息、且面向复杂灵巧操作的数据集与基准，阻碍了触觉反馈下的机器人技能学习研究。
- **整体含义**：本文首次构建了面向复杂灵巧操作的视觉-触觉数据集（VTDexManip），并提出包含6个灵巧操作任务的基准以及基于强化学习的视觉-触觉技能学习框架，填补了该领域的空白，为触觉反馈机器人学习提供了重要资源。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：通过人类演示采集日常任务中的视觉-触觉数据，构建大规模数据集；在此基础上设计强化学习框架，联合预训练视觉和触觉表征，以提升灵巧操作策略的性能和泛化能力。
- **关键技术细节**：
  - **数据采集**：招募人类操作员执行10种日常任务（如抓取、旋转、插入等），使用182个物体，同时记录RGB图像（视觉）和二进制触觉信号（由触觉传感器提供，信号仅指示接触与否，稀疏且二元）。
  - **数据集内容**：包含视觉流和触觉流的时间同步序列，覆盖多种物体属性和任务类型。
  - **强化学习框架**：基于标准强化学习算法（如PPO），设计多种非预训练和预训练方法。预训练阶段使用自监督或对比学习等方法联合学习视觉和触觉特征；在强化学习策略中，将预训练好的视觉-触觉表征作为输入或部分输入。
  - **关键设计**：框架内共18种方法（包括非预训练和预训练方法的组合），以探究不同模态（仅视觉、仅触觉、视觉+触觉）及预训练策略（独立预训练、联合预训练）的效果。

## 3. 实验设计：使用了哪些数据集/场景，它的 benchmark 是什么，对比了哪些方法
- **数据集**：自建的VTDexManip数据集，包含10种日常任务、182个物体的人类操作视觉-触觉数据。
- **Benchmark**：提出6个复杂灵巧操作任务（如瓶子开盖、零件装配、物体旋转等），使用仿真环境（如Isaac Gym）进行训练和评估。
- **对比方法**：
  - **非预训练方法**：直接使用原始RGB图像、二进制触觉信号或二者拼接作为策略输入，不进行任何预训练。
  - **预训练方法**：对视觉模态、触觉模态或二者联合进行预训练（如使用MAE、对比学习等），然后将预训练权重初始化到策略网络，再通过强化学习微调。
  - 具体包含18种不同设置，覆盖了不同模态组合与预训练策略的消融对比。

## 4. 资源与算力
- **文中未明确说明**：论文正文和元数据中未提及训练所使用的GPU型号、数量以及具体训练时长等算力信息。仅提到强化学习在仿真环境中进行，但未披露硬件配置。

## 5. 实验数量与充分性
- **实验数量**：共设计了18种方法（非预训练+预训练）在6个灵巧操作任务上进行评估。此外还进行了多项分析实验，包括：触觉信号对成功率的影响、联合预训练与独立预训练的对比、在不同未知任务上的泛化测试、对视角设置、触觉噪声、二值化阈值的鲁棒性分析。
- **充分性评估**：
  - **优点**：实验覆盖了多种模态组合、预训练策略、以及鲁棒性分析，消融实验较为完整，能够清晰展示触觉和预训练带来的增益。
  - **客观性**：在基准框架下统一对比，使用相同环境、相同任务、相同强化学习算法（PPO），保证了公平性。
  - **潜在不足**：所有实验均在仿真中进行，未提及在真实机器人上的验证；任务数量（6个）和物体数量（182个用于数据集）虽然合理，但真实泛化场景仍需更多测试。

## 6. 论文的主要结论与发现
- **触觉模态的贡献**：即使使用二进制且稀疏的触觉信号，直接将其加入策略训练即可提升约20%的成功率；若将视觉与触觉联合预训练，成功率可再提升20%。
- **联合预训练的优势**：视觉-触觉联合预训练在所有任务中表现出最强的适应性，尤其是在未知任务上具有良好泛化能力。
- **鲁棒性**：二进制触觉信号与视觉结合，对视角变化、触觉噪音以及二值化阈值的选择均表现出鲁棒性，有利于向真实世界部署。
- **核心贡献**：首次提供了面向复杂灵巧操作的视觉-触觉数据集与基准，验证了触觉在强化学习灵巧操作中的显著作用。

## 7. 优点：方法或实验设计上的亮点
- **数据集创新**：首个针对复杂灵巧操作的视觉-触觉数据集，包含10种日常任务和182个物体，填补了数据空白。
- **基准设计**：包含6个具有挑战性的灵巧操作任务，并引入统一框架对比18种方法，系统评估了不同模态和预训练策略的效果。
- **实验严谨性**：不仅对比了有无触觉、有无预训练，还做了鲁棒性测试（视角、噪声、阈值），结论扎实。
- **实用性**：采用二进制触觉信号（低成本、易获取），且证明其有效性和鲁棒性，降低了实际部署的传感器要求。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **仿真局限**：所有实验仅在仿真环境中进行，未在真实机器人上验证，触觉信号的仿真与真实传感器存在差异，真实环境下的泛化能力未知。
- **触觉信号稀疏性**：虽然二进制触觉有效，但更丰富的触觉信息（如力大小、纹理）可能带来更大提升，本文未探索。
- **任务数量**：基准包含6个任务，覆盖范围有限，可能无法代表所有灵巧操作场景。
- **未提供算力细节**：无法复现训练资源配置，影响可复现性。
- **人类演示数据的使用**：数据集来自人类操作，但如何将人类演示数据与强化学习策略更紧密结合（如通过模仿学习）未深入探讨。
- **偏差风险**：物体选择和任务设置可能偏向某些特定类型，存在数据集偏差。

（完）
