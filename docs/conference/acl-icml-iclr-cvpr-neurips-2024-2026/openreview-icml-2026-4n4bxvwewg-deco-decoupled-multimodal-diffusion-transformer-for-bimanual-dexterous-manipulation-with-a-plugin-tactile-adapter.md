---
title: "DECO: Decoupled Multimodal Diffusion Transformer for Bimanual Dexterous Manipulation with a Plugin Tactile Adapter"
title_zh: DECO：带插件触觉适配器的解耦多模态扩散Transformer用于双臂灵巧操作
authors: "Xukun Li, Yu Sun, Lei Zhang, Bo-Sheng Huang, Yibo Peng, Yuan Meng, Haojun Jiang, Shaoxuan Xie, Guocai Yao, Alois Knoll, Zhenshan Bing, Xinlong Wang, Zhenguo Sun"
date: 2026-04-30
pdf: "https://openreview.net/pdf/785d477a9845f0c98b07d8515ca63d310f921955.pdf"
tags: ["query:tactile-vla"]
score: 8.0
evidence: 具有触觉适配器的多模态扩散Transformer
tldr: DECO提出了解耦的多模态扩散Transformer，通过专门的条件路径分离视觉、本体感和触觉信号，并引入轻量级触觉适配器实现参数高效注入。配合DECO-50数据集，在双臂灵巧操作任务上展示了结构化多模态融合的优势，尤其提升了触觉信号的利用效率。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 双臂灵巧操作需要有效整合视觉、本体感和触觉等多模态输入，现有方法融合方式单一。
method: 提出解耦多模态扩散Transformer，通过专门条件路径分离各模态，并用轻量适配器注入触觉。
result: 在双臂灵巧操作数据集上验证了结构化多模态融合的有效性，触觉信号利用效率显著提升。
conclusion: DECO为多模态融合操作提供了灵活高效的框架，尤其适用于触觉集成。
---

## Abstract
Bimanual dexterous manipulation relies on integrating multimodal inputs to perform complex real-world tasks. To address the challenges of effectively combining these modalities, we propose DECO, a decoupled multimodal diffusion transformer that disentangles vision, proprioception, and tactile signals through specialized conditioning pathways, enabling structured and controllable integration of multimodal inputs, with a lightweight adapter for parameter-efficient injection of additional signals.
Alongside DECO, we release DECO-50 dataset for bimanual dexterous manipulation with tactile sensing, consisting of 50 hours of data and over 5M frames, collected via teleoperation on real dual-arm robots.
We train DECO on DECO-50 and conduct extensive real-world evaluation with over 2,000 robot rollouts. Experimental results show that DECO achieves the best performance across all tasks, with a 72.25\% average success rate and a 21\% improvement over the baseline. Moreover, the tactile adapter brings an additional 10.25\% average success rate across all tasks and a 20\% gain on complex contact-rich tasks while tuning less than 10\% of the model parameters.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
双臂灵巧操作（Bimanual Dexterous Manipulation）是机器人实现复杂真实世界任务的关键能力，这类任务强烈依赖多模态输入的有效整合，尤其是视觉、本体感和触觉信号。然而，现有方法在融合这些模态时往往采用单一或粗放的方式，缺乏结构化的解耦机制，难以灵活控制不同模态的贡献，尤其对于触觉这类非视觉信号，其注入效率和结构化利用不足。为此，论文提出**DECO**，旨在通过解耦多模态扩散Transformer实现更有效、可控制的多模态融合，并特别针对触觉信号设计了轻量级插件适配器，以参数高效的方式注入触觉信息，从而提升双臂灵巧操作的整体性能。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将视觉、本体感（proprioception）和触觉信号通过**专门的条件路径（specialized conditioning pathways）**进行解耦，避免不同模态之间的信息混杂，然后通过扩散Transformer架构实现结构化、可控的多模态集成。同时引入轻量级**触觉适配器（tactile adapter）**，仅需调整极少量参数即可将触觉信号高效注入模型。
- **关键技术细节**：
  - **解耦多模态扩散Transformer**：为每种模态设计独立的嵌入和条件编码路径，然后在Transformer的注意力机制中以解耦方式融合，保留各模态的特异性。
  - **插件触觉适配器（Plugin Tactile Adapter）**：一种轻量级模块，插入到预训练或主模型的特定层中，通过微调少于10%的模型参数实现触觉信号的注入，避免全模型微调带来的算力浪费和灾难性遗忘。
  - **扩散模型框架**：采用扩散过程生成机器人动作轨迹，将多模态条件作为去噪过程的引导。
- **算法流程**（文字说明）：
  1. 输入多模态数据：RGB图像（视觉）、机器人关节角度/力矩（本体感）、触觉传感器读数（触觉）。
  2. 各模态经过独立的编码器提取特征，得到专用条件表示。
  3. 在扩散Transformer中，将噪声动作序列与各条件表示一起输入多头注意力模块，但注意力计算中通过掩码或分离机制确保不同模态特征在各自路径中更新。
  4. 触觉适配器作为一个侧支模块，仅在触觉存在时激活，其输出与主模型的特征进行逐元素加法或交叉注意力融合。
  5. 经过T步去噪后得到最终动作序列，交由机器人执行。

## 3. 实验设计
- **数据集**：论文提出了**DECO-50数据集**，包含50小时、超过500万帧的双臂灵巧操作数据，通过遥操作在真实双机器人平台上采集，具备触觉传感信息。这是当前该领域规模较大的触觉-灵巧操作数据集。
- **基准（Benchmark）**：基于DECO-50数据集训练模型，并在真实机器人上进行超过2000次 rollout 评估。未明确列出其他公开基准，但通过消融实验和基线对比衡量性能。
- **对比方法**：摘要仅提及“基线”（baseline），未具体说明基线方法名称（可能是无触觉适配器版本或其他简单融合模型）。对比指标为任务成功率。
- **主要结果**：
  - DECO在所有任务上平均成功率**72.25%**，相比基线提升**21%**。
  - 触觉适配器带来额外**10.25%**平均成功率提升，在复杂接触密集型任务上提升**20%**。

## 4. 资源与算力
论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅指出触觉适配器仅需调整**少于10%的模型参数**，暗示训练效率较高，但缺乏量化数据。

## 5. 实验数量与充分性
- **实验数量**：进行了超过**2000次真实机器人 rollout**，包含多个任务，应涵盖不同接触难度。此外，做了消融实验（对比有/无触觉适配器），以及可能的多模态条件对比。
- **充分性**：真实机器人大规模测试比仿真更客观，2000次次数充足，可统计显著差异。但论文仅提供了平均成功率提升百分比，未列出每个任务的详细成功率、方差或置信区间，且未与其它多模态策略（如扩散策略、基于RNN/Transformer的基线）公开对比，可能削弱充分性。
- **公平性**：基线可能为DECO去掉触觉适配器的版本，属于自消融，对比公平。但未与外部方法（如其他VLA模型）比较，外部公平性受限。

## 6. 论文的主要结论与发现
1. **解耦多模态融合有效**：DECO通过专门条件路径分离视觉、本体感和触觉，比简单拼接或共注意力融合获得更好性能。
2. **触觉适配器参数高效且有效**：仅需微调不到10%参数，即可显著提升成功率，尤其在依赖触觉反馈的复杂接触任务上（提升20%）。
3. **大规模真实数据驱动**：DECO-50数据集为双臂灵巧操作提供了高质量训练资源，支撑了模型性能。
4. 整体达到**72.25%平均成功率**，验证了所提出框架在真实机器人上的实用潜力。

## 7. 优点
- **方法亮点**：
  - 提出**解耦条件路径**，使不同模态可以独立编码并融合，增强了可控性和可解释性。
  - **插件触觉适配器**设计轻量，易于集成到现有扩散Transformer中，提升了触觉信号利用效率。
  - 基于**扩散Transformer**，能处理动作序列的长期依赖和高维多模态条件。
- **实验亮点**：
  - 收集了大规模真实双臂灵巧操作数据集（DECO-50），促进该领域研究。
  - 2000次真实世界 rollout 验证了方法的实际效果，而非仅仅仿真。
  - 消融实验量化了触觉适配器的贡献。

## 8. 不足与局限
- **实验覆盖不足**：
  - 未与当前流行的多种VLA（视觉-语言-动作）模型、扩散策略（Diffusion Policy）或其他多模态融合方法进行横向比较，缺乏与SOTA的全面对比。
  - 未公开任务具体定义、环境变化、触点分布等，难以评估泛化性。
  - 仅在一个数据集（DECO-50）上训练和测试，未见在不同机器人平台或不同物体上的迁移实验。
- **偏差风险**：
  - DECO-50数据采集依赖遥操作，可能引入操作员习惯偏差。
  - 成功率提升百分比虽高，但未给出绝对数值和方差，可能存在统计稳健性问题。
- **应用限制**：
  - 需依赖触觉传感器硬件，且适配器仅针对触觉，对其他模态（如力、声音）未涉及。
  - 扩散Transformer的推理速度未提及，可能影响实时性要求高的场景。
  - 参数调整少于10%是优点，但未说明这部分参数如何选择（哪些层），可能存在主观性。

（完）
