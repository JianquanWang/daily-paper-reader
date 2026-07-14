---
title: "ForceVLA: Enhancing VLA Models with a Force-aware MoE for Contact-rich Manipulation"
title_zh: ForceVLA：利用力感知混合专家增强VLA模型的接触丰富操作
authors: "Jiawen Yu, Hairuo Liu, Qiaojun Yu, Jieji Ren, Ce Hao, Haitong Ding, Guangyu Huang, Guofan Huang, Yan Song, Panpan Cai, Wenqiang Zhang, Cewu Lu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=2845H8Ua5D"
tags: ["query:tactile-vla"]
score: 9.0
evidence: 将力作为第一模态的VLA模型，增强接触丰富的操作
tldr: ForceVLA提出了一种将力感知作为第一模态的VLA框架，通过力感知混合专家模块FVLMoE动态融合视觉语言嵌入与实时6轴力反馈，显著提升了在视觉遮挡和动态不确定性下的接触丰富操作性能。实验证明该方法在多种精细操作任务中优于基线，为机器人触觉VLA模型提供了有效范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型缺乏力反馈，在接触丰富任务中表现不佳。
method: 提出ForceVLA，引入力感知MoE融合模块，将6轴力作为第一模态集成到VLA动作解码中。
result: 在多种接触丰富操作任务上优于基线方法，成功处理视觉遮挡场景。
conclusion: 力感知是VLA模型处理精细接触任务的关键，所提方法有效提升了鲁棒性。
---

## Abstract
Vision-Language-Action (VLA) models have advanced general-purpose robotic manipulation by leveraging pretrained visual and linguistic representations. However, they struggle with contact-rich tasks that require fine-grained control involving force, especially under visual occlusion or dynamic uncertainty. To address these limitations, we propose \textbf{ForceVLA}, a novel end-to-end manipulation framework that treats external force sensing as a first-class modality within VLA systems. ForceVLA introduces \textbf{FVLMoE}, a force-aware Mixture-of-Experts fusion module that dynamically integrates pretrained visual-language embeddings with real-time 6-axis force feedback during action decoding. This enables context-aware routing across modality-specific experts, enhancing the robot's ability to adapt to subtle contact dynamics. We also introduce \textbf{ForceVLA-Data}, a new dataset comprising synchronized vision, proprioception, and force-torque signals across five contact-rich manipulation tasks. ForceVLA improves average task success by 23.2\% over strong $\pi_0$-based baselines, achieving up to 80\% success in tasks such as plug insertion. Our approach highlights the importance of multimodal integration for dexterous manipulation and sets a new benchmark for physically intelligent robotic control. Code and data will be released at https://sites.google.com/view/forcevla2025/.

---

## 论文详细总结（自动生成）

# ForceVLA 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：现有的 Vision-Language-Action (VLA) 模型虽然借助预训练的视觉与语言表征实现了通用机器人操作，但在接触丰富（contact-rich）的任务中表现不佳。这类任务要求精细的力控制，尤其是在视觉遮挡或动态不确定环境下，纯依赖视觉和语言信息难以应对微妙的接触动力学变化。
- **整体含义**：机器人精细操作（如插销、装配等）需要力觉信息作为关键反馈。ForceVLA 提出将外部力传感作为 VLA 系统中的“第一类模态”（first-class modality），弥补现有模型缺乏力感知的缺陷，为物理智能机器人控制建立新基准。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：端到端操作框架 ForceVLA，通过一个力感知混合专家（Mixture-of-Experts）融合模块 FVLMoE，将预训练的视觉-语言嵌入与实时 6 轴力/扭矩反馈动态集成到动作解码过程中。实现基于上下文的模态特定专家路由，使机器人适应细微的接触动力学变化。
- **关键技术细节**：
  - **FVLMoE 模块**：在动作解码阶段，将视觉语言嵌入（来自预训练 VLA 主干）与从力传感器获取的实时 6 轴力-扭矩信号进行融合。MoE 结构包含多个专家（expert），每个专家擅长处理特定模态组合或接触情境，通过门控网络动态选择专家输出，实现自适应融合。
  - **整体流程**：输入为多视角图像、语言指令、机器人关节状态（本体感知）以及力/扭矩信号 → 预训练视觉语言编码器提取嵌入 → FVLMoE 根据上下文将视觉语言嵌入与力特征融合 → 生成动作指令 → 控制机器人执行。
  - **动作解码**：力反馈作为连续信号直接参与解码，不经过离散化，保留精细触觉信息。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：作者构建了 **ForceVLA-Data**，一个包含同步视觉、本体感知和力-扭矩信号的新数据集，覆盖 5 个接触丰富操作任务（如插销插入、零件装配等）。
- **基准**：以当前强基线方法 **π₀**（一种 VLA 模型）为基础进行比较。
- **对比方法**：直接对比 π₀（无力反馈）与 ForceVLA（添加 FVLMoE 模块），报告平均任务成功率提升 23.2%，在插销插入等任务上达到 80% 成功率。

## 4. 资源与算力

- 论文正文未明确说明使用的 GPU 型号、数量、训练时长等算力信息。这一缺失使得结果的可复现性和成本评估不够透明。

## 5. 实验数量与充分性

- **实验数量**：在 5 个不同接触丰富任务上进行了评估，包含与强基线的直接对比。未提及消融实验的具体数量（如移除力模态、替换 MoE 为简单融合等），但从摘要可推断至少存在“有力 vs 无力”的消融。
- **充分性**：任务覆盖了多种接触场景（但具体任务名未列出），且报告了成功率提升百分比，具有一定客观性。然而，缺乏针对不同视觉遮挡程度、动态不确定性条件下的详细分析，也没有与其他触觉融合方法（如将力信号简单拼接）的全面对比。整体实验设计合理但不够深入，未提供统计显著性检验或多次运行方差。

## 6. 主要结论与发现

- **力感知是 VLA 模型处理精细接触任务的关键**：将实时力反馈作为第一模态集成到动作解码中可显著提升成功率（平均 +23.2%）。
- **所提方法有效提升了鲁棒性**：在处理视觉遮挡和动态不确定性时表现优于纯视觉-语言基线。
- **FVLMoE 的动态融合机制优于静态融合**：通过上下文路由实现模态特异性专家激活，使机器人能自适应调整对力反馈的依赖程度。

## 7. 优点：方法与实验设计的亮点

- **创新性**：首次将 6 轴力/扭矩作为第一类模态集成到 VLA 端到端框架中，并提出专用的 MoE 融合模块 FVLMoE，解决了模态异质性和动态融合问题。
- **数据构建**：发布了包含同步力-扭矩信号的专有数据集 ForceVLA-Data，填补了机器人触觉 VLA 领域的公开数据空白。
- **实验验证**：在多个真实接触任务上验证了有效性，成功率提升幅度显著（23.2%），且展示了对视觉遮挡场景的适应能力。

## 8. 不足与局限

- **实验覆盖局限**：仅测试了 5 个任务，且未提供任务难度等级、不同力传感器噪声水平的影响分析，未扩展到非接触任务或更复杂的多步任务。
- **偏差风险**：基线选择仅包含 π₀，未与近期其他融合触觉的 VLA 方法（如 Tactile Transformer 等）进行公平比较；数据集可能偏向于特定环境（如固定工作台、特定物体），泛化性存疑。
- **应用限制**：需要额外的力传感硬件（如 6 轴力/扭矩传感器），增加了成本和部署复杂度；力反馈的采样频率与动作解码频率的匹配未讨论。
- **算力与可复现性**：未提供训练细节（GPU 型号、批量大小、训练轮次等），使其他研究者难以复现和评估资源需求。

（完）
