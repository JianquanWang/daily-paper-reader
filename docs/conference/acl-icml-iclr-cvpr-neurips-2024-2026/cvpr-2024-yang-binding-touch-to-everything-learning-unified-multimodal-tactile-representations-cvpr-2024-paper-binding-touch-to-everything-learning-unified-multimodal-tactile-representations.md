---
title: "Binding Touch to Everything: Learning Unified Multimodal Tactile Representations"
title_zh: 绑定触觉与一切：学习统一的多模态触觉表示
authors: "Yang, Fengyu, Feng, Chao, Chen, Ziyang, Park, Hyoungseob, Wang, Daniel, Dou, Yiming, Zeng, Ziyao, Chen, Xien, Gangopadhyay, Rit, Owens, Andrew, Wong, Alex"
date: 2024-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2024/papers/Yang_Binding_Touch_to_Everything_Learning_Unified_Multimodal_Tactile_Representations_CVPR_2024_paper.pdf"
tags: ["query:tactile-vla"]
score: 9.0
evidence: UniTouch统一触觉与视觉、语言、声音，实现通用触觉感知
tldr: 针对触觉多模态学习面临的昂贵数据采集和传感器异构问题，本文提出UniTouch统一触觉模型。该模型将触觉嵌入与预训练图像嵌入对齐，从而关联视觉、语言和声音等多种模态。引入可学习传感器特定令牌，支持同时从多种光学触觉传感器学习。UniTouch在零样本触觉感知任务上表现优异，是触觉基础模型的重要里程碑。
source: CVPR-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1795, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1797, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1792, \"height\": 602, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 411, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 436, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 886, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 779, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 795, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-yang-binding-touch-to-everything-learning-unified-multimodal-tactile-representations-cvpr-2024-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 873, \"height\": 358, \"label\": \"Table\"}]"
motivation: 触觉多模态学习受限于数据成本和传感器差异，缺乏统一模型。
method: UniTouch将触觉嵌入对齐到预训练图像嵌入，并提出传感器特定令牌处理异构传感器。
result: 在多项零样本触觉任务上达到领先性能。
conclusion: UniTouch实现了触觉与多模态的有效关联，推动了触觉基础模型的发展。
---

## Abstract
The ability to associate touch with other modalities has huge implications for humans and computational systems. However multimodal learning with touch remains challenging due to the expensive data collection process and non-standardized sensor outputs. We introduce UniTouch a unified tactile model for vision-based touch sensors connected to multiple modalities including vision language and sound. We achieve this by aligning our UniTouch embeddings to pretrained image embeddings already associated with a variety of other modalities. We further propose learnable sensor-specific tokens allowing the model to learn from a set of heterogeneous tactile sensors all at the same time. UniTouch is capable of conducting various touch sensing tasks in the zero-shot setting from robot grasping prediction to touch image question answering. To the best of our knowledge UniTouch is the first to demonstrate such capabilities.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：触觉感知对人类和机器人系统至关重要，但触觉多模态学习面临两大挑战：
  - **数据采集成本高**：触觉数据需要主动接触物体，难以大规模收集。
  - **传感器异构性**：不同视觉触觉传感器（如GelSight、DIGIT、Taxim、TACTO）在机械设计、弹性材料及成像上存在显著差异，导致领域鸿沟大，现有模型通常只能针对单一传感器。
- **整体含义**：本文旨在构建一个统一的触觉表示模型，使触觉信号能与视觉、语言、声音等多种模态有效关联，从而在不依赖配对数据的情况下零样本解决多种触觉感知任务，推动触觉基础模型的发展。

#### 2. 方法论：核心思想、关键技术细节
- **核心思想**：通过对比学习将触觉嵌入对齐到预训练的**图像嵌入空间**（基于ImageBind），该空间已与语言、音频等模态对齐，从而间接建立触觉与其他模态的关联。
- **关键技术细节**：
  - **触觉编码器**：使用Vision Transformer（ViT）作为骨干网络，接收触觉图像并输出1024维嵌入。
  - **传感器特定令牌**：为每种传感器引入一组可学习的token（L=5，K=3），作为前缀拼接到图像patch token前，用于捕获传感器特有的校准、背景颜色等属性，使模型能同时从多种传感器学习。
  - **对比学习目标**：采用InfoNCE损失函数，同时计算触觉→图像和图像→触觉的余弦相似度，最大化配对样本相似度，最小化非配对样本相似度。
  - **批次内采样策略**：为避免不同传感器数据在批次中产生过多易负样本，设置批次中σ=75%的数据来自同一数据集，其余来自其他数据集，增强模型对同类传感器内难负样本的分辨能力。
- **推理时未知传感器适配**：对于推理中未见过的传感器，通过计算输入触觉图像与各传感器原型（所有训练样本像素均值）的L1距离，取最近邻的传感器token作为前缀。

#### 3. 实验设计：数据集、Benchmark与对比方法
- **训练与评估数据集**（见表1）：
  - **训练集**：Touch and Go（GelSight, 120k）、The Feeling of Success（GelSight, 9.3k）、YCB-Slide（DIGIT, 183k）、ObjectFolder 2.0（Taxim, 180k）。
  - **评估集**（含域外）：
    - 域内：上述训练集对应的测试分割。
    - 域外：ObjectFolder Real（GelSlim, 20k）、ObjectFolder 1.0（TACTO, 20k）、SSVTP（DIGIT, 4.6k）——包含2种训练未见的传感器。
- **Benchmark与任务**：
  - **零样本触觉理解**：材料分类、机器人抓取稳定性预测。
  - **跨模态检索**：触觉→视觉、触觉→文本、触觉→音频检索（在ObjectFolder 2.0上评估）。
  - **图像合成**：触觉→图像生成（Touch and Go数据集）。
  - **Touch-LLM**：触觉问答（触觉图像描述、抓取稳定性、接触定位）。
  - **X-to-touch生成**：从视觉/文本/音频生成触觉图像。
- **对比方法**：
  - 线性探测基线：ImageNet预训练、VT CMC、SSVTP（包含单数据集和多数据集训练版本）。
  - 跨模态检索：CCA、PLSCA、DSCMR、DAR（监督方法）。
  - 图像合成：Pix2Pix、VisGel、Vision-from-touch。
  - Touch-LLM：BLIP-2、InstructBLIP、LLaVA-1.5、ImageBind-LLM。

#### 4. 资源与算力
- 文中有明确说明：使用**4块NVIDIA A40 GPU**，batch size为48，训练150个epoch，采用AdamW优化器，基础学习率1×10⁻⁵，余弦退火调度。

#### 5. 实验数量与充分性
- **实验数量**：涵盖6个主要任务（材料分类、抓取预测、跨模态检索、触觉驱动图像生成、Touch-LLM、X-to-touch生成），每个任务在多个数据集（共7个数据集，含域内和域外）上进行评估。
- **消融实验**：表8对传感器特定令牌、批次内采样策略进行了逐项消融（在Touch and Go上零样本材料分类），验证了各模块的有效性。
- **充分性与公平性**：
  - 与多个现有方法在相同设置下比较（如线性探测、全监督、零样本）。
  - 对于零样本触觉理解，目前尚无其他方法可公平对比，作者展示了自身结果。
  - 实验设计较为全面，覆盖了多个应用场景和传感器类型，但域外泛化实验仅包含两种未见传感器，样本量有限（ObjectFolder Real和ObjectFolder 1.0各20k），可能存在偏差。

#### 6. 主要结论与发现
- UniTouch能够**零样本**完成多种触觉感知任务，包括材料分类（如Touch and Go上52.7%准确率，接近部分监督方法）、抓取稳定性预测（域内82.3%、域外75.8%）、跨模态检索（触觉→视觉mAP 41.9%，超越监督方法）。
- **传感器特定令牌**和**批次内采样**显著提升了多传感器联合训练的性能（表8显示从基线21.4%提升至52.7%）。
- 触觉与文本的对齐通过合适的提示词（如“This feels like [CLS]” vs 视觉提示）可有效利用，提示词设计对零样本分类影响显著（表7）。
- Touch-LLM在触觉图像描述上（GPT-4评分3.54）大幅超越现有VLM（最佳基线2.33），表明触觉嵌入的成功迁移。
- 触觉→图像生成虽在FID上略逊于专用监督方法（103.11 vs 81.2），但在CVTP和材料一致性指标上更优，证明了零样本泛化能力。

#### 7. 优点
- **创新性**：首次将触觉与ImageBind对齐，实现跨模态零样本能力，扩展了触觉基础模型的研究边界。
- **统一性**：通过传感器特定token和采样策略，成功在多个异构触觉传感器上联合训练并泛化到未见传感器。
- **应用广泛**：零样本即可完成多种传统上需要监督学习的任务（抓取预测、材料分类、图像生成、问答），降低了触觉应用的数据门槛。
- **实验设计完整**：多任务、多数据集、多模态评估，包括域外泛化和消融，验证了方法鲁棒性。

#### 8. 不足与局限
- **传感器类型局限**：模型仅针对视觉触觉传感器（输出图像），未涵盖力、压力、振动等其他类型触觉传感器，限制了应用范围。
- **可解释性不足**：嵌入空间为“黑盒”，难以直观解释触觉特征与物理属性的对应关系。
- **域外泛化验证有限**：仅评估了两种未见传感器（GelSlim和TACTO），且每个数据集规模不大（20k），泛化到更多传感器或真实场景的能力尚需进一步验证。
- **零样本性能仍有差距**：虽然零样本表现可观，但在材料分类等任务上仍低于某些有监督方法（如Touch and Go上52.7% vs VT CMC监督的56.5%）。
- **未讨论公平性和偏差**：训练数据来自特定环境（如桌面抓取、可控实验室），可能导致对现实复杂场景（如户外、动态接触）的泛化偏差。

（完）
