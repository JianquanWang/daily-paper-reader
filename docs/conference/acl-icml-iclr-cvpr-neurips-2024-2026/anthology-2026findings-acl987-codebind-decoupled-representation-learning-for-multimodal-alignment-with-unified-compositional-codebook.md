---
title: "CodeBind: Decoupled Representation Learning for Multimodal Alignment with Unified Compositional Codebook"
title_zh: CodeBind：基于统一构成性码本的解耦表征学习用于多模态对齐
authors: "Zeyu Chen, Jie Li, Kai Han"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.987.pdf"
tags: ["query:tactile-vla"]
score: 6.0
evidence: 多模态表征对齐方法，可应用于触觉-视觉-语言
tldr: 针对多模态对齐中模态特有信息丢失和数据稀少问题，提出CodeBind，通过构成性码本分解共享与特有特征，增量式对齐目标模态与桥梁模态，无需全配对数据。该方法可扩展至触觉与视觉、语言的对齐，支持触觉VLA构建。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 727, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 716, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 795, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 715, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 761, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 783, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 718, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1590, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 786, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 783, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 760, \"height\": 290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 787, \"height\": 735, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 780, \"height\": 1783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 780, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 791, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 794, \"height\": 666, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 801, \"height\": 702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1385, \"height\": 2077, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.987/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1635, \"height\": 1870, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 808, \"height\": 647, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1661, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1658, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1659, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 808, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 810, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 813, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 811, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 812, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 796, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1660, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 813, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 814, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 771, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 812, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 815, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 805, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.987/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 808, \"height\": 173, \"label\": \"Table\"}]"
motivation: 传统多模态对齐忽略模态独有特征，且数据配对困难。
method: 设计模态共享-特有码本，分解特征并通过增量对齐避免全配对需求。
result: 在多个多模态对齐任务上达到最优，效率高。
conclusion: CodeBind为触觉与视觉语言对齐提供通用框架。
---

## Abstract
Multimodal representation alignment is pivotal for large language models and robotics. Traditional methods are often hindered by cross-modal information discrepancies and data scarcity, leading to suboptimal alignment spaces that overlook modality-unique features. We propose CodeBind, a framework that optimizes multimodal representation spaces through a modality-shared-specific codebook design. By incrementally aligning target and bridging modalities, CodeBind bypasses the need for fully paired data. Unlike traditional hard alignment, CodeBind decomposes features into shared components for semantic consistency and specific components for modality-unique details. This design utilizes a compositional vector quantization scheme, where a shared codebook bridges modality gaps and modality-specific codebooks mitigate representation bias by preventing dominant modalities from overshadowing others. Validated across nine modalities (text, image, video, audio, depth, thermal, tactile, 3D point cloud, EEG), CodeBind achieves state-of-the-art performance in multimodal classification and retrieval tasks. Project page: https://visual-ai.github.io/codebind

---

## 论文详细总结（自动生成）

# CodeBind: 基于构成性码本的多模态解耦表征学习 —— 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：多模态表征对齐中，传统“硬对齐”（hard alignment）方法存在两大缺陷：
  - **信息丢失**：将异构模态数据强制压缩到共享子空间，导致模态独有特征被忽略，出现“最小公分母”效应。
  - **表征偏差**：数据稀缺的模态（如触觉、热成像）容易被视觉等主导模态压制，削弱跨模态交互。
- **背景**：多模态对齐是LLM与机器人感知的关键，但现有方法依赖大规模配对数据或数据扩增，成本高且易引入噪声。需要一种无需全配对、能保留模态独有特征的可扩展对齐框架。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：通过“共享-特有码本”解耦表征，将每个模态的特征分解为：
  - **共享成分**：捕捉跨模态语义不变性（如“猫”的概念），用于对齐。
  - **特有成分**：保留模态细节（如颜色、纹理），用于精细检索。
- **关键技术细节**：
  1. **增量对齐**：以文本/图像为桥梁模态，逐步对齐目标模态（音频、深度、热成像等），避免全配对数据需求。
  2. **模态共享-特有码本（Modality-Shared-Specific Codebook）**：
     - 共享码本（`C_shared`）：所有模态共用，量化共享嵌入，确保语义一致性。
     - 特有码本（`C_spec`）：每个模态拥有独立码本，量化特有嵌入，防止模态坍缩。
  3. **构成性向量量化（Compositional VQ）**：
     - 将d维嵌入分成m个子向量，每个子向量独立量化，使表示空间指数级扩大（`K^m`组合），在不增加码本大小下提升容量。
     - 例如：1024共享码本 + 256特有码本，每个码向量维度8。
  4. **训练目标**：多任务损失函数，包括：
     - `L_align`：InfoNCE对比损失，对齐共享嵌入。
     - `L_recon`：重建损失（Transformer解码器），确保信息保留。
     - `L_orth`：正交损失，鼓励共享与特有嵌入正交。
     - `L_uni`：均匀损失，促进特有嵌入分布均匀。
     - `L_vq`：码本承诺损失（EMA更新）。
     - `L_cctr`, `L_cuni`：码向量正则化，防止码本坍缩。
     - `L_cm`：跨模态码匹配损失，同步配对模态的码向量分布。
  5. **自适应损失平衡**：通过EMA动态调整各损失权重，消除手动调参。
  6. **可扩展多路径对齐**：每个目标模态同时与多个桥梁模态对齐，且不同路径使用独立码本，支持高效增量扩展。
- **架构**：基于ImageBind/ViT-Lens，冻结桥梁模态编码器，目标模态编码器通过LoRA微调。训练时包含重建模块，推理时仅使用共享嵌入，丢弃特有部分和重建模块以轻量化。

## 3. 实验设计：数据集、基准、对比方法

- **模态与数据集**（共9种）：
  - 图像：ImageNet-1K, Places365
  - 视频：Kinetics400, MSR-VTT
  - 深度：NYU-D, SUN-D
  - 音频：AudioSet, VGGSound, ESC, Clotho, AudioCaps
  - 热成像：LLVIP, FLIR_v2
  - 触觉：TAG-M, TAG-H/S, TAG-R/S
  - EEG：IN-EEG
  - 3D点云：ModelNet40
- **基准**：分类任务使用Acc@1（AudioSet用mAP），检索任务使用Recall@1/Recall@10。
- **对比方法**：
  - 基线：ImageBind, ViT-Lens
  - 其他SOTA：FreeBind, OmniBind, LanguageBind, OneLLM, OneEncoder, UNI_ALIGN等。
- **实验设置**：以ImageBind和ViT-Lens为基础，插入CodeBind模块，得到CodeBind-IB和CodeBind-VL。所有对比保持相同数据集和设置，确保公平。

## 4. 资源与算力

- 论文明确说明：使用 **8块NVIDIA RTX 3090 GPU** 进行训练，学习率 `5×10^{-4}`。不同模态的batch size和损失权重在附录表1中给出。未说明整体训练时长。

## 5. 实验数量与充分性

- **实验数量**：丰富且充分，包括：
  - 主要结果表2（a/b）：覆盖9种模态，多个数据集，包含分类和检索指标。
  - 与SOTA对比表3：6种方法。
  - 消融实验（表6-8）：分别验证码本、解耦、重建、损失函数、码本配置（共享/分离、构成性、大小维度）、损失函数逐项添加。
  - 嵌入空间可视化（图4-5）、码本分布分析、线性探测、精细检索（表4、图6-7）、多模态融合（表5）。
  - 代码使用率/困惑度分析（附录表8）、损失权重自适应对比（附录表2）。
- **充分性**：实验设计全面，涵盖了不同模态、不同任务、不同组件、不同超参数，消融细致（如共享码本大小、特有码本大小、码向量维度）。对比方法均为近期顶级工作，数据集标准，结果可重复。
- **公平性**：在相同基线（ImageBind/ViT-Lens）上插入CodeBind，保持其他条件一致；对比SOTA时明确指出其他方法使用了不同数据扩增策略，但CodeBind未使用额外数据，对比客观。

## 6. 主要结论与发现

- **性能提升**：CodeBind在9种模态上均显著优于基线，尤其在数据稀缺的触觉、热成像、EEG上提升巨大（如LLVIP +32.1%，FLIR_v2 +50.6%，IN-EEG +14.7%）。
- **模态间隙缩小**：t-SNE可视化显示共享嵌入跨模态更混合，且修正式调制有效分离共享与特有特征。
- **丰富保留**：通过精细检索和线性探测证明特有嵌入保留了模态独有的物理细节（如纹理、颜色、背景），而共享嵌入负责语义对齐。
- **码本设计有效**：构成性VQ优于标准VQ，共享码本比分离码本更好，码本大小调节权衡对齐与重建。
- **可扩展性**：无需全配对数据，支持任意新模态的增量集成。

## 7. 优点

- **创新性**：提出解耦表征+共享-特有码本范式，解决了传统硬对齐的固有缺陷（信息丢失与偏差），是方法上的重要贡献。
- **实用性**：增量对齐策略降低数据需求，插拔式设计可轻松融入现有框架（ImageBind/ViT-Lens），推理轻量。
- **鲁棒性**：构成性VQ和自适应损失平衡有效应对数据不平衡和码本坍缩，算法稳定。
- **全面验证**：9种模态、多种任务、多个数据集、多维度消融，实验规模和严谨性很强。
- **开源与可复现**：提供项目页面和公开检查点，附录包含完整超参数和实现细节。

## 8. 不足与局限

- **可解释性局限**：对于非视觉模态（如触觉、EEG）的特有信息，缺乏强基础空间（如VLM）进行解释性验证，目前主要依赖文本锚定，论文承认此为局限。
- **文本模态简化**：文本仅使用共享嵌入，未分解特有成分，可能限制了文本粒度细节的利用。
- **重建模块开销**：训练时重建模块增加计算量，但推理时丢弃，不影响部署。
- **应用限制**：未在真实机器人或大规模多模态理解系统中进行端到端验证；仅在分类/检索任务评估，对复杂推理任务（如问答、生成）的增益未充分展示。
- **可能的数据偏差**：尽管不需要全配对数据，但桥梁模态（文本/图像）仍依赖预训练模型（OpenCLIP），不同桥梁质量可能影响对齐效果。
- **公平性对比偏差**：部分SOTA方法（如LanguageBind）使用了额外合成数据或大规模数据扩增，而CodeBind仅用自然配对数据，虽然性能可比，但直接对比时可能存在不公平性（论文已指出这一点）。

（完）
