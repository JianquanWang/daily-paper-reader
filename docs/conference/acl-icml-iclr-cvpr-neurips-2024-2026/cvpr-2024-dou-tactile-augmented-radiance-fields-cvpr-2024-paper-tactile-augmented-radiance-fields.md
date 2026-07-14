---
title: Tactile-Augmented Radiance Fields
title_zh: 触觉增强辐射场
authors: "Dou, Yiming, Yang, Fengyu, Liu, Yi, Loquercio, Antonio, Owens, Andrew"
date: 2024-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2024/papers/Dou_Tactile-Augmented_Radiance_Fields_CVPR_2024_paper.pdf"
tags: ["query:tactile-vla"]
score: 9.0
evidence: 提出触觉增强辐射场，通过跨模态生成融合视觉和触觉
tldr: 本文针对场景表示中缺乏触觉信息的问题，提出触觉增强辐射场。利用视觉触觉传感器的相机特性和场景区域触觉相似性，训练条件扩散模型从神经辐射场渲染的图像生成对应触觉图像。收集了最大规模的空间对齐视觉-触觉数据集。实验表明生成的触觉图像与实际触觉高度一致，为机器人触觉感知和虚拟交互提供了新工具。
source: CVPR-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1803, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 876, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1803, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1809, \"height\": 937, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1809, \"height\": 730, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 877, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 874, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 878, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-dou-tactile-augmented-radiance-fields-cvpr-2024-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 875, \"height\": 477, \"label\": \"Table\"}]"
motivation: 现有场景表示仅依赖视觉，无法提供物理触感，限制了需要触觉反馈的机器人任务。
method: 提出触觉增强辐射场，使用条件扩散模型从NeRF渲染的RGB-D图像生成触觉图像，并利用大量对齐数据训练。
result: 生成的触觉图像与真实触觉数据匹配度高，跨模态生成准确，且可用于虚拟触摸。
conclusion: 触觉增强辐射场有效融合视觉和触觉，为机器人操作和虚拟交互提供共享3D表示。
---

## Abstract
We present a scene representation that brings vision and touch into a shared 3D space which we call a tactile-augmented radiance field. This representation capitalizes on two key insights: (i) ubiquitous vision-based touch sensors are built on perspective cameras and (ii) visually and structurally similar regions of a scene share the same tactile features. We use these insights to train a conditional diffusion model that provided with an RGB image and a depth map rendered from a neural radiance field generates its corresponding tactile "image". To train this diffusion model we collect the largest collection of spatially-aligned visual and tactile data. Through qualitative and quantitative experiments we demonstrate the accuracy of our cross-modal generative model and the utility of collected and rendered visual-tactile pairs across a range of downstream tasks. Project page: https://dou-yiming.github.io/TaRF

---

## 论文详细总结（自动生成）

# Tactile-Augmented Radiance Fields 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有计算机视觉模型仅依赖视觉信息，缺乏对物体触觉属性（如表面纹理、微几何、软硬度）的感知能力，而触觉数据收集昂贵、耗时，且现有视觉-触觉数据集大多存在空间未对齐、场景规模小、样本稀疏等问题。
- **研究动机**：为了将触觉感知融入3D场景表示，使机器能够“不仅看到，还能感觉到”，从而赋能机器人操作、材料模拟、虚拟现实等应用。
- **整体含义**：提出一种名为**触觉增强辐射场（Tactile-Augmented Radiance Field, TaRF）** 的场景表示，将视觉与触觉统一到一个共享的3D空间，并利用生成模型在未探测区域合成触觉信号。

## 2. 论文提出的方法论

### 核心思想
- 利用NeRF获得场景的3D视觉重建，结合稀疏的触觉探测样本，通过条件扩散模型在场景任意位置生成触觉图像（来自视觉触觉传感器DIGIT的输出）。

### 关键技术细节
- **数据采集与对齐**：
  - 将触觉传感器（DIGIT）与iPhone相机固定在同一杆上，同步拍摄视频和触觉数据。
  - 通过结构光运动（SfM）估计相机位姿，利用触觉传感器内参和手动标注的像素对应点（通过触觉棋盘格）求解传感器与相机的相对位姿（基于透视相机重投影误差最小化）。
- **触觉生成模型**：
  - 采用条件潜在扩散模型，以NeRF渲染的RGB图像和深度图作为条件，并额外输入传感器无接触时的背景图像。
  - 使用对比学习（ResNet-50）预训练视觉-触觉编码器，作为扩散模型的条件编码。
  - 训练流程：先在YCB-Slide数据集上预训练无条件扩散模型，再在自有数据集上微调。

### 算法流程（文字描述）
1. 用NeRF从视频帧重建场景3D视觉场。
2. 通过标定得到每个触觉样本的3D位姿。
3. 从该位姿渲染RGB-D图像作为条件。
4. 训练条件扩散模型`pφ(τ | v, d, b)`，其中`τ`为触觉图像，`v`、`d`为RGB和深度，`b`为背景。
5. 推理时，对新位置渲染条件，经扩散模型生成触觉图像，并用对比模型重排序提高质量。

## 3. 实验设计

- **数据集**：
  - 自采集：13个日常场景（办公室、工作室、走廊、室外等），共19.3k对齐的视觉-触觉对，每个场景约1k-2k样本。
  - 公开数据集：YCB-Slide（用于预训练），Touch and Go（用于材料分类任务对比）。
- **Benchmark**：
  - 密集触觉估计：FID、PSNR、SSIM、CVTP（视觉-触觉对比相似度）。
  - 触觉定位：2D热图可视化、3D定位mAP。
  - 材料分类：20类材料分类、软硬二分类、平滑/粗糙二分类准确率。
- **对比方法**：
  - L1（相同架构但L1损失）
  - VisGel（GAN-based）
  - Chance（随机）
  - ObjectFolder 2.0、VisGel、Touch and Go等用于材料分类比较。

## 4. 资源与算力

文中明确提及：
- **NeRF训练**：单张NVIDIA RTX 2080 Ti，200k steps，学习率1e-2。
- **对比学习预训练**：4张NVIDIA RTX 2080 Ti，20 epochs，batch size 256。
- **扩散模型训练**：4张NVIDIA A40 GPU，batch size 48，30 epochs，学习率1e-5（按GPU数×batch size缩放）。
- 推理时：200步去噪，guidance scale 7.5，重排序取16个样本。

**注意**：未说明总训练时长（小时/天），但给出了迭代数和epoch数。

## 5. 实验数量与充分性

- **实验数量**：
  - 密集触觉估计（表2）：对3个方法进行定量对比。
  - 消融实验（表3）：6种变体（去RGB、去深度、去对比预训练、去重排序、去多尺度条件）。
  - 3D触觉定位（表4）：对比Chance、Real、Real+Estimated，4个距离阈值。
  - 材料分类（表5）：与4个现有数据集对比，并展示添加合成数据后的提升。
- **充分性**：
  - 消融覆盖了主要组件，验证了RGB、深度、对比学习、重排序的作用。
  - 下游任务验证了生成触觉的有效性（合成数据带来提升）。
  - 不足：所有实验均在同一数据集（自采场景）上评估，未在完全不同的场景或传感器上测试泛化性；材料分类任务中使用的测试数据来自GelSight传感器（与DIGIT不同），但预训练混合了Touch and Go，对比设计公平。

## 6. 论文的主要结论与发现

- 通过多视图几何约束，可以低成本地将触觉传感器与相机标定，得到空间对齐的视觉-触觉数据。
- 条件扩散模型能有效从单张RGB-D图像生成逼真的触觉图像，在FID和CVTP上远优于L1和VisGel基线。
- 场景的3D几何（深度图）和对比学习预训练对生成质量有显著贡献。
- 生成的合成触觉数据可提升下游任务（3D触觉定位、材料分类）性能，表明模型捕获了有用的触觉特征。
- 提出的TaRF表示能实现“准密集”的触觉传播，填补稀疏探测之间的空白。

## 7. 优点

- **方法新颖性**：首次将NeRF与触觉生成模型结合，实现场景级、空间对齐的视觉-触觉表示。
- **采集方案低成本**：仅用智能手机、自拍杆和商用触觉传感器，无需机器人或专业设备，易于扩展。
- **大规模数据集**：19.3k对齐样本，是目前最大规模的实景视觉-触觉对数据集。
- **生成质量高**：扩散模型优于GAN和L1，能够恢复微几何细节（如布料纹理）。
- **下游任务验证充分**：通过触觉定位和材料分类证明了合成数据的实用价值。

## 8. 不足与局限

- **对齐精度限制**：由于SfM和标定误差，厘米级的位姿误差可能导致像素级错位，影响生成质量（文中承认）。
- **场景刚性假设**：假设场景在触摸时不变形，不适用于弹性或可变形表面。
- **传感器视野小**：DIGIT传感器视野极小，生成模型所需条件图像需从NeRF渲染高分辨率视图，计算开销大。
- **实验局限性**：
  - 仅在自采场景中评估，缺乏跨数据集、跨传感器泛化实验。
  - 未在真实机器人系统上验证（如抓取成功率提升）。
  - 材料分类对比中，虽混合了Touch and Go数据，但自采数据与测试数据分布不完全一致，可能引入偏差。
- **依赖手动标注**：标定过程需要手动标注触觉棋盘格的对应点，虽然数量少（6-15点），但限制了自动化程度。
- **计算资源需求高**：扩散模型需要4块A40 GPU训练，推理需多次采样和重排序，实时性受限。

（完）
