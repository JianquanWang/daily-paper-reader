---
title: "Touch2Shape: Touch-Conditioned 3D Diffusion for Shape Exploration and Reconstruction"
title_zh: "Touch2Shape: 触觉条件化3D扩散用于形状探索与重建"
authors: "Wang, Yuanbo, Zhang, Zhaoxuan, Qiu, Jiajin, Sun, Dilong, Meng, Zhengyu, Wei, Xiaopeng, Yang, Xin"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_Touch2Shape_Touch-Conditioned_3D_Diffusion_for_Shape_Exploration_and_Reconstruction_CVPR_2025_paper.pdf"
tags: ["query:tactile-vla"]
score: 7.0
evidence: 使用触觉图像进行三维形状感知与重建
tldr: 现有3D扩散模型依赖视觉图像，难以捕捉复杂形状的局部细节。本文提出Touch2Shape，利用触觉图像条件化扩散模型进行形状探索与重建。通过触觉嵌入模块和触觉形状融合模块，模型能生成紧凑表征并融合触觉与形状信息。实验表明该方法在局部细节重建上优于纯视觉方法，为多模态触觉感知提供了新思路。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1796, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1757, \"height\": 1016, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1613, \"height\": 754, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 809, \"height\": 397, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 875, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1798, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-touch2shape-touch-conditioned-3d-diffusion-for-shape-exploration-and-reconstruction-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 775, \"height\": 366, \"label\": \"Table\"}]"
motivation: 现有视觉3D重建方法受遮挡和光照限制，难以捕获局部细节，本文利用触觉图像弥补这一不足。
method: 提出触觉条件化扩散模型，包含触觉嵌入模块和触觉形状融合模块，从触觉图像重建三维形状。
result: 模型能从触觉图像生成高质量3D形状，尤其在局部细节上优于纯视觉方法。
conclusion: 触觉信息有效增强3D重建的精细度，推动了多模态感知在机器人中的应用。
---

## Abstract
Diffusion models have made breakthroughs in 3D generation tasks. Current 3D diffusion models focus on reconstructing target shape from images or a set of partial observations. While excelling in global context understanding, they struggle to capture the local details of complex shapes and limited to the occlusion and lighting conditions. To overcome these limitations, we utilize tactile images to capture the local 3D information and propose a Touch2Shape model, which leverages a touch-conditioned diffusion model to explore and reconstruct the target shape from touch. For shape reconstruction, we have developed a touch embedding module to condition the diffusion model in creating a compact representation and a touch shape fusion module to refine the reconstructed shape. For shape exploration, we combine the diffusion model with reinforcement learning to train a policy. This involves using the generated latent vector from the diffusion model to guide the touch exploration policy training through a novel reward design. Experiments validate the reconstruction quality thorough both qualitatively and quantitative analysis, and our touch exploration policy further boosts reconstruction performance.

---

## 论文详细总结（自动生成）

# Touch2Shape 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：当前 3D 扩散模型主要依赖视觉图像（单张、多视图或部分观测）进行形状重建，虽然能较好地把握全局结构，但在复杂形状的局部细节重建上表现不足，且容易受遮挡和光照变化的影响。
- **动机**：触觉图像能够提供局部 3D 位置和形变信息，不受光照和遮挡干扰，适合捕捉局部细节。本文旨在利用触觉信号，结合扩散模型的生成能力，实现基于触觉的形状探索与重建，解决纯视觉方法的局限性。
- **整体含义**：提出 Touch2Shape 模型，首次将触觉条件引入 3D 扩散框架，支持触觉仅模式（T）和视觉-触觉模式（T+V），在主动触觉探索下逐步提升重建质量。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：使用预训练的 VQ-VAE（基于 TSDF 体积）将 3D 形状编码为低维紧凑潜向量；然后训练一个触觉条件化的扩散模型，从触摸历史（一系列触觉图像）生成去噪后的潜向量，该潜向量用于两件事：① 在最终步骤通过触觉形状融合模块解码出完整形状；② 在每个探索步骤，结合强化学习策略预测下一个最佳触摸位置。
- **关键技术细节**：
  - **触觉嵌入**：预训练 TouchCNN 模型从每个触觉图像预测触觉图表（chart），包含接触点坐标和状态；将所有触摸图表合并为 N×M×4 张量，加上位置编码后通过卷积与池化得到 N 个 token。
  - **对比触觉编码器**：利用 MoCo 框架进行对比学习，将触觉特征（查询）与形状潜向量特征（键）拉近，使触觉和形状在联合空间中对齐。
  - **扩散模型训练**：损失函数 `L_diff = || E_ω(z_t, r(t), C(T_0,...,T_{n-1})) - ω_t ||^2`，其中 C 是触觉条件提取网络，E_ω 是去噪网络，输入为加噪潜向量、时间嵌入和触觉条件。
  - **触觉形状融合模块**：将触觉图表的全局信息体素化后经额外编码器提取多尺度特征，与 VQ-VAE 解码器中对应尺度的特征进行加权融合（公式 4），最后微调解码器。
  - **策略训练（强化学习）**：使用 DQN，动作为球面上 50 个预定义位置；输入为初始潜向量、当前触觉条件的去噪潜向量及动作嵌入，通过全连接层预测每个动作的 Q 值。奖励函数定义为 `R = H(L_diff(t, n-1) - L_diff(t, n))`，即鼓励动作使扩散损失下降（去噪潜向量更接近真实潜向量）。
- **算法流程**（文字描述）：
  1. 预训练 VQ-VAE 编码器/解码器、TouchCNN、对比触觉编码器。
  2. 固定预训练模块，训练扩散模型（触觉条件化）。
  3. 训练触觉形状融合模块（精调解码器）。
  4. 在仿真环境中，使用当前触摸历史得到去噪潜向量，利用 Q 网络选择动作；收集新触摸图像后更新潜向量，并在最终步骤解码完整形状。

## 3. 实验设计
- **数据集**：
  - **ABC 数据集**：约 40,000 个无明确类别的 CAD 物体，形状多样，难度高。
  - **ShapeNet 数据集**：1,650 个物体，涵盖 6 个类别（碗、瓶、相机、罐、吉他、杯子）。
- **触觉图像与视觉图像**：均使用与 ActiveVT 相同的仿真环境渲染生成。
- **基准方法**：
  - 在 ABC 数据集上对比 VTRecon [33]（仅触觉/视觉+触觉重建）和 ActiveVT [34]（主动触觉重建）。
  - 在 ShapeNet 数据集上对比 TouchSDF [7]（基于隐式函数的触觉重建）。
- **评价指标**：Chamfer Distance (CD) 和 Earth Mover’s Distance (EMD)，均为越低越好。
- **实验场景**：
  - 不同触摸次数（0, 1, 5, 10, 20 次 grasp/touch）。
  - 两种输入模式：触觉仅（T）、视觉+触觉（T+V）。
  - 策略评估时对比 Oracle、Random、Even 基线，并报告 5 次 grasp 后 CD 与初始 CD 的比值。

## 4. 资源与算力
- **GPU 型号与数量**：NVIDIA GeForce RTX 4090（文中明确提到）。
- **训练时长**：所有网络（扩散模型、触觉形状融合、策略）训练总计约一周。
- **具体迭代配置**：
  - VQ-VAE 预训练（按 SDFusion 设置，未报告迭代数）。
  - 扩散模型：1,000,000 迭代，学习率 1e-5，batch size 12。
  - 触觉形状融合：250,000 迭代，学习率 1e-4，batch size 8。
  - 策略训练：200 epochs，学习率 3e-4，batch size 16。
- **实现框架**：PyTorch。

## 5. 实验数量与充分性
- **主要实验结果表**：
  - 表 1：ABC 数据集上不同 grasp 数量（0,1）的 CD 对比（T 和 T+V 设置）。
  - 表 2：ShapeNet 数据集上 1,10,20 次 touch 的 EMD 对比（T 和 T+V，与 TouchSDF）。
  - 表 3：策略评估（5 次 grasp 后 CD 改进比率，T 和 T+V）。
  - 表 4：消融研究（对比学习、形状融合模块的效果，T/V/T+V）。
- **可视化**：图 4（ABC 示例）、图 5（探索过程）、图 6（T/V/T+V 对比）。
- **充分性评价**：
  - 覆盖两个不同规模和难度数据集。
  - 与多个现有 SOTA 方法对比，包括被动和主动触觉重建。
  - 消融实验验证了对比学习模块和触觉形状融合模块的必要性。
  - 策略评估使用了 Oracle 上界、Random 和 Even 基线，公平合理。
  - 实验条件（仿真渲染）与基线方法一致，保证公平。
  - **结论**：实验设计较为全面，客观公正，验证了各模块的作用。

## 6. 主要结论与发现
1. **重建性能**：Touch2Shape 在 ABC 和 ShapeNet 上均显著优于 VTRecon、ActiveVT 和 TouchSDF，尤其在视觉-触觉设置下 CD 和 EMD 大幅降低，表明模型能有效融合触觉与视觉信息。
2. **策略有效性**：通过强化学习训练的触摸探索策略相比 Random、Even 基线，能更快降低重建误差，接近 Oracle 上界，证明潜向量引导的探索是有效的。
3. **模块贡献**：对比触觉编码器和触觉形状融合模块各自带来性能提升（消融实验表 4），缺少任一模块都会导致 CD 增大。
4. **探索进化**：随着 touch 次数增加，重建质量逐步逼近真实形状（图 5），验证了主动触觉探索的价值。

## 7. 优点
- **创新性**：首次将触觉条件融入 3D 扩散模型，解决了纯视觉局部细节缺失的问题并支持主动探索。
- **架构设计**：利用低维潜向量分离了形状探索与最终解码，避免每一步都生成高分辨率体积，效率高。
- **融合策略**：提出触觉形状融合模块，通过多尺度特征加权融合纠正扩散生成与触觉局部信息的不一致。
- **奖励设计**：基于扩散损失变化设计的奖励函数无需最终形状输出，简化策略训练。
- **实验严谨**：多数据集、多基线、多轮次对比，消融实验充分。

## 8. 不足与局限
- **仿真环境依赖**：所有触觉图像和视觉图像均来源于仿真渲染，未在真实机器人平台验证，存在 sim-to-real 差距。
- **物体类别有限**：ShapeNet 仅 6 个类别，ABC 虽多样但为 CAD 数据，真实世界中物体材质、柔性等未考虑。
- **触觉数量限制**：实验中最大 touch 次数为 20，更长时间探索的收益未分析；且 ABC 实验中触觉仅设置下性能提升幅度仍然有限（CD 从 40→6.79，仍高于 T+V 的 1.4）。
- **计算资源需求较高**：训练需 RTX 4090 约一周，对资源要求较高；推理时需运行扩散模型多步采样，实时性可能受限于 64³ 体积。
- **可解释性不足**：奖励函数基于扩散损失变化，但该损失本身与最终重建误差之间的相关性未显式证明。
- **未来方向**：作者提及的迁移到真实平台、全场景重建、神经渲染等尚未实现。

（完）
