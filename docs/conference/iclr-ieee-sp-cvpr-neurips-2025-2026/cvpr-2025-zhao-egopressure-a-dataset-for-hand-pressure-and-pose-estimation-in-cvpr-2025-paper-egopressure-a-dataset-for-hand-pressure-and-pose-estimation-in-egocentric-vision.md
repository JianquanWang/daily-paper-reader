---
title: "EgoPressure: A Dataset for Hand Pressure and Pose Estimation in Egocentric Vision"
title_zh: EgoPressure：用于第一人称视觉中手部压力和姿态估计的数据集
authors: "Zhao, Yiming, Kwon, Taein, Streli, Paul, Pollefeys, Marc, Holz, Christian"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhao_EgoPressure_A_Dataset_for_Hand_Pressure_and_Pose_Estimation_in_CVPR_2025_paper.pdf"
tags: ["query:tactile-vla"]
score: 8.0
evidence: 手部压力和姿态数据集用于触觉接触
tldr: 该论文针对机器人触觉感知中缺乏压力标注数据的问题，提出了EgoPressure数据集，包含高分辨率接触压力强度和精确手部姿态网格。基于该数据集，训练了从RGB图像估计施加压力的基准模型。该工作为多模态触觉感知研究提供了关键资源，可支持机器人通过视觉推断触觉信息。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1803, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1794, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 888, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 890, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1572, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 902, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 693, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 700, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1707, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 870, \"height\": 191, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 874, \"height\": 819, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1792, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 874, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-egopressure-a-dataset-for-hand-pressure-and-pose-estimation-in-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1545, \"height\": 260, \"label\": \"Table\"}]"
motivation: 现有数据集缺乏同时标注手部姿态和接触压力的资源，限制了触觉感知研究。
method: 通过多视角序列优化方法获取高精度压力强度和手部姿态标注，构建数据集。
result: 建立了压力估计基准，并验证了模型在未见场景下的泛化能力。
conclusion: 该数据集填补了触觉感知数据空白，促进机器人从视觉理解触觉交互。
---

## Abstract
Touch contact and pressure are essential for understanding how humans interact with objects and offer insights that benefit applications in mixed reality and robotics. Estimating these interactions from an egocentric camera perspective is challenging, largely due to the lack of comprehensive datasets that provide both hand poses and pressure annotations. In this paper, we present EgoPressure, an egocentric dataset that is annotated with high-resolution pressure intensities at contact points and precise hand pose meshes, obtained via our multi-view, sequence-based optimization method. We introduce baseline models for estimating applied pressure on external surfaces from RGB images, both with and without hand pose information, as well as a joint model for predicting hand pose and the pressure distribution across the hand mesh.Our experiments show that pressure and hand pose complement each other in understanding hand-object interactions.

---

## 论文详细总结（自动生成）

# EgoPressure：用于第一人称视觉中手部压力和姿态估计的数据集——论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有手-物交互数据集大多仅提供手部姿态或接触点标注，缺乏同时包含**高分辨率接触压力强度**和**精确手部网格**的标注资源，限制了从第一人称视觉（egocentric vision）理解触摸压力、进而支持增强现实/虚拟现实（AR/VR）和机器人灵巧操作的研究。
- **背景**：先前方法使用数据手套或触觉传感器会干扰自然触觉，而基于视觉的压力估计依赖的PressureVision等数据集仅提供静态相机视角且缺少手部姿态。因此，需要一个同时具备**第一人称视角、压力图、手部姿态网格**的综合数据集，以推动触觉感知从“接触检测”走向“压力空间定位”。
- **整体意义**：EgoPressure填补了这一空白，为从RGB图像联合估计手部姿态与压力分布提供了首个基准，证明压力和手部姿态可相互增强对手-物交互的理解。

## 2. 提出的方法论：核心思想、关键技术细节

### 2.1 核心思想
- 构建一个多相机+压力触摸板的采集平台，无标记地获取同步RGB-D序列与压力数据，并通过**多视图、序列优化的标注方法**自动生成精确的3D手部网格和全表面压力纹理图（UV map）。
- 基于该数据集，设计基线模型和联合模型（PressureFormer），验证在图像平面和手部网格上预测压力的可行性，并量化手部姿态信息对压力估计的提升。

### 2.2 关键技术细节

#### 2.2.1 无标记手部姿态标注方法
- **初始化**：使用HaMeR[54]从每台静态相机的RGB图像估计初始MANO手部参数（姿态θ、平移t），通过三角化消除尺度-平移歧义；利用Segment-Anything（SAM）获取手部分割掩膜。
- **两阶段优化**：
  - **阶段1 – 姿态优化**（Pose Optimization）：使用可微分渲染器DIB-R，最小化渲染损失和网格交叉损失，优化θ、t。目标函数：L_pose = L_R + L_insec。
  - **阶段2 – 形状细化**（Shape Refinement）：固定姿态，引入顶点位移D_vert（沿法线方向），优化网格细节，同时引入**虚拟渲染**损失（L_vR）将压力数据融入优化。
- **虚拟渲染机制**：在触摸板下方放置一台虚拟正交相机，渲染手部网格的纹理UV图（压力）并与地面真实压力图P_gt对齐，同时利用接触区域深度约束确保物理接触。损失函数：L_vR = MSE(渲染压力, P_gt) + L1(接触区域深度差)。

#### 2.2.2 PressureFormer联合模型
- **架构**：基于HaMeR的ViT，提取图像特征tokens和手部顶点V_hand。使用Transformer解码器，以顶点作为查询tokens，交叉注意力于图像特征，输出每个顶点的D维特征。
- **UV压力预测**：将顶点特征映射到MANO模型的UV坐标，经两层卷积神经网络插值，得到通道数为C（压力类别数）的UV压力图U_pred。
- **损失函数**：L_PF = w1·L_c（粗粒度UV压力交叉熵）+ w2·L_p（通过可微分渲染将UV压力渲染到图像平面后与P_gt的交叉熵）。
- **训练技巧**：使用手部中心裁剪、数据增强（平移、缩放、旋转）。

## 3. 实验设计

### 3.1 数据集
- **EgoPressure（主数据集）**：21名参与者，5小时RGB-D视频（7台静态+1台头戴相机，30fps），共4.3M帧；包含31种手势（触摸、拖动、按压等），压力图来自Sensel Morph触摸板（240×169.5mm，4种表面纹理）。
- **PressureVision数据集**：用于泛化测试的公开数据集（仅静态相机）。
- **Meta Quest 3**：额外定性泛化测试（真实环境）。

### 3.2 Benchmark任务与对比方法
#### 任务1：图像平面压力预测（Table 2）
- **方法**：PressureVisionNet[19]（RGB only） → [19] + 2.5D手部关键点（预测/真实） → 通过HaMeR[54]或地面真实姿态提供额外输入通道。
- **评价指标**：Contact IoU、Volumetric IoU、MAE、Temporal Accuracy。
- **设置**：
  - 训练/测试均在**第一人称视图**（egocentric）。
  - 训练/测试均在**相同外部相机视图**（exocentric，固定视角2,3,4,5）。
  - **跨视图泛化**：训练于相机2,3,4,5，测试于相机1,6,7。
- **核心结论**：融合真实手部姿态可显著提升压力估计（Vol. IoU提升最高达7%），即使使用预测姿态也有改善。

#### 任务2：手部网格压力预测（Table 3）
- **方法**：PressureFormer（Ours） vs. 图像投影基线（PressureVisionNet及其姿态增强版）通过HaMeR网格反向投影→UV压力映射。
- **评价指标**：图像平面的Contact/Vol. IoU、MAE、Temp. Acc.；UV压力图的Contact/Vol. IoU。
- **设置**：使用所有相机视图训练（15人），测试6人；额外在仅第一人称视图上评估；泛化至PressureVision数据集。
- **核心结果**：PressureFormer在UV压力IoU上显著领先（33.12% vs. 基准最高24.10%），图像平面Contact IoU也优于基线，且泛化到PressureVision时大幅超越（29.03% Image Contact IoU vs. 7.54%）。

#### 消融实验
- PressureFormer去掉粗粒度UV损失（L_c）→性能下降（UV Vol. IoU从24.54%降至18.61%），证明UV监督的必要性。

### 3.3 评价指标
- Contact IoU（接触区域交并比）、Volumetric IoU（压力值加权的交并比）、MAE（平均绝对误差，kPa）、Temporal Accuracy（时间一致性）。UV压力图对应指标类似。

## 4. 资源与算力

- **文中未明确报告GPU型号、数量或训练时长**。仅提及工作站配置为Intel Core i7-9700K、Nvidia GeForce RTX 3070用于数据采集。对于模型训练，未披露具体计算资源。因此无法评估训练成本。

## 5. 实验数量与充分性

### 5.1 实验数量
- **图像平面基准**（Table 2）：共9个条件（3个评估设置 × 3种输入模态）。每种条件在15人训练、6人测试上运行。
- **UV压力联合模型**（Table 3）：共7个条件（包括两个评价视角和消融、泛化）。
- **定性实验**：在Meta Quest 3上展示泛化；多视图可视化；压力分布热图。

### 5.2 充分性与公平性
- **充分性**：覆盖了多相机视图、第一人称、跨视图泛化、消融以及公开数据集泛化，具有一定广度。但**缺乏与其他联合估计方法的对比**（目前没有其他公开工作做同样任务）。
- **公平性**：基线模型均采用作者提供的代码或官方实现，且引入姿态增强时控制额外信息量。消融实验验证了UV损失和姿态信息的独立贡献。
- **不足**：仅一个消融实验（是否使用粗UV损失），未探索不同网络架构、不同损失权重、不同数据增强策略。也未详细分析压力定量误差随施加力的分布。

## 6. 主要结论与发现

1. **数据集贡献**：EgoPressure是第一个**第一人称、裸手、带压力标注和3D手部网格**的数据集，含4.3M帧，覆盖21人31种手势，支持多视图和头戴视角。
2. **手部姿态提升压力估计**：在图像平面压力预测中，使用地面真实2.5D姿态比无姿态提升Vol. IoU约3%~7%；即使使用HaMeR预测姿态也有提升，证明姿态是有效辅助信息。
3. **联合估计的优势**：PressureFormer直接预测手部UV压力图，在UV空间精度远超间接投影方法，且能泛化到未见相机布局（Meta Quest 3）和公开数据集PressureVision，表明**在网格上建模压力更具迁移性**。
4. **压力与姿态互补**：结合两者可更完整理解手-物交互，例如区分轻触和重按、定位受力区域。

## 7. 优点

### 方法亮点
- **无标记自动标注**：利用多视图几何+可微分渲染+压力数据，实现无需物理标记的手部网格与压力纹理联合优化，精度高且可扩展。
- **新颖的联合模型PressureFormer**：首次将压力预测集成到手部网格UV空间，通过可微分渲染实现图像平面与网格平面双重监督，形成自一致性。
- **丰富的实验设计**：同时评估图像平面和UV空间压力，并验证跨视图、跨数据集泛化，展示实际部署潜力。

### 数据集亮点
- **大规模、多模态**：RGB-D（静态+头戴）、压力、手部网格、文本纹理图，时间同步精确（PTP驱动，IR标记验证）。
- **手势多样性**：31种手势覆盖触摸、拖动、按压、捏合等，包含不同力度等级。
- **受试者多样性**：21人（6女/15男，年龄23-32），身高体重手型分布较广，标注了MANO形状参数β。

## 8. 不足与局限

- **场景限制**：仅限**平面交互**（触摸板），无法扩展至任意造型物体表面（如球体、工具），限制了在真实机器人操作环境中的直接应用。
- **单手交互**：数据集仅包含单手操作，未涵盖双手协同场景（如抓取大型物体、双手配合）。
- **环境限制**：均在室内受控环境采集，背景为绿幕，光照条件有限（3种等级），未涉及室外、复杂纹理背景。
- **数据偏差**：参与者均为同机构年轻人（23-32岁），手部形态学偏年轻，可能存在人口统计偏差。
- **压力传感器精度**：Sensel Morph虽提供高分辨率，但仅限于接触平面，无法检测非接触方向的力（如侧向力）。
- **实验覆盖有限**：
  - 消融实验仅一个，未系统性分析不同损失权重、不同顶点数、不同特征维度的影响。
  - 缺少与基于物理模拟的方法（如ContactPose、GRAB的推理压力）的对比。
  - 未评估模型在运动模糊、严重遮挡等真实退化条件下的鲁棒性。
- **计算资源未报告**：无法判断模型训练效率及可复现性。

（完）
