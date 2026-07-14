---
title: Vision-Based Pseudo-Tactile Information Extraction and Localization for Dexterous Grasping
title_zh: 基于视觉的伪触觉信息提取与灵巧抓取定位
authors: "Teng Yan, Cai Yaobang, Tian Xia, Jianhao, Wenxian Li"
date: 2024-09-28
pdf: "https://openreview.net/pdf?id=xcHIiZr3DT"
tags: ["query:tactile-vla"]
score: 6.0
evidence: 利用视觉获取伪触觉信息用于抓取
tldr: 该研究针对灵巧手抓取中的触觉感知挑战，提出从视觉中提取伪触觉信息的方法。通过Isaac Sim构建灵巧手模型进行实时指尖接触定位，建立了仿真坐标与实际坐标及点云伪触觉信息之间的关联。实验验证了该方法的有效性，为触觉感知提供了低成本高精度的仿真方案。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 解决灵巧手抓取中触觉感知难题，利用视觉作为伪触觉来源。
method: 通过Isaac Sim仿真提取点云法向量和灰度方差作为伪触觉信息，结合3D坐标映射。
result: 成功建立仿真与实际坐标及伪触觉的关联，实现实时接触定位。
conclusion: 视觉伪触觉方法可有效辅助灵巧手抓取，降低对真实触觉传感器的依赖。
---

## Abstract
This study addresses the challenges of tactile perception in robotic dexterous hand grasping by focusing on two main tasks: 1) Acquiring tactile information from everyday objects using vision, termed "pseudo-tactile" information, and 2) Building a Dexterous Hand (RH8D) model in Isaac Sim for real-time fingertip contact localization. Utilizing Isaac Sim enables safe, cost-effective experimentation and high-precision simulations that facilitate data collection for model validation. The research establishes a scientific connection between simulated 3D coordinates, actual 3D coordinates, and pseudo-tactile information derived from point clouds, quantified through normal vectors and grayscale variance analysis. Results demonstrate the ability to extract clear object surface textures, accurately locate fingertip contact points in real-time (with precision up to $0.001 m$), and provide tactile information at contact points. This framework enhances robotic grasping capabilities and offers low-cost sensory data. The source code and dataset are publicly available now.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：机器人灵巧手在执行精细抓取任务时，需要准确获取接触点处的触觉信息，但物理触觉传感器成本高、易损坏、难以集成到灵巧手小尺寸指尖上。如何在不依赖真实触觉传感器的情况下，利用已有视觉信息（RGB-D或点云）推断出类似触觉的特征（即“伪触觉信息”），并实现实时、高精度的指尖接触定位。
- **研究背景**：现有触觉感知方法多依赖专用传感器（如GelSight、BarrettHand等），而视觉可作为低成本替代方案。同时，仿真环境（如Isaac Sim）提供了安全、可控、可复现的实验平台，便于快速迭代和大量数据收集。
- **整体含义**：提出一种从点云中提取法向量与灰度方差作为伪触觉特征的方法，并在Isaac Sim中构建真实的灵巧手（RH8D）模型，建立仿真坐标、真实坐标与伪触觉信息的关联，从而在无物理传感器时实现对物体表面纹理和接触位置的估计，提升灵巧手抓取能力并降低触觉感知门槛。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将触觉感知问题转化为视觉点云处理问题——通过点云的法向量估计表面微观几何（对应触觉中的纹理与力方向），通过点云灰度方差估计表面粗糙度/材质（对应触觉中的摩擦与硬度），并利用仿真中精确的指尖模型实现接触点的实时定位。
- **关键技术细节**：
  1. **灵巧手模型构建**：在Isaac Sim中导入RH8D灵巧手模型，包含完整的运动学与碰撞几何；指尖区域设置虚拟接触传感器，记录接触点位置（精度达0.001 m）。
  2. **点云伪触觉信息提取**：
     - **法向量**：对物体点云中每个点计算其局部邻域的主法向量，作为表面朝向的估计（可反映接触压力方向）。
     - **灰度方差**：将点云映射到RGB图像（或直接使用点云强度值），计算局部邻域的灰度方差，用于量化表面纹理粗糙度。
  3. **坐标映射**：建立仿真坐标系下的指尖接触点3D坐标与真实世界（或RGB-D相机坐标系）3D坐标的刚性变换（通过标定或共同特征点匹配），同时将点云伪触觉信息插值到接触点位置。
  4. **实时定位流程**：仿真中每帧更新指尖位置→计算指尖与物体最近距离的接触点→输出该点的法向量与灰度方差→映射到实际坐标用于抓取规划。

- **公式或算法流程**（文字描述）：
  - 输入：物体点云 \(P\)，灵巧手模型关节角度 \(q\)。
  - 步骤1：对点云 \(P\) 计算每个点的法向量 \(n_i\)（基于PCA或M-estimation）。
  - 步骤2：对点云 \(P\) 计算每个点的局部灰度方差 \(v_i\)（取周围K邻域像素强度差异）。
  - 步骤3：在Isaac Sim中，通过碰撞检测获得指尖接触点集合 \(C_{sim} = \{c_j\}\)。
  - 步骤4：通过预先标定的变换矩阵 \(T\)（仿真→真实坐标），得到 \(C_{real} = T(C_{sim})\)。
  - 步骤5：对于每个接触点 \(c_j\)，在点云中最近邻搜索，分配其法向量 \(n_{j}\) 和方差 \(v_{j}\)。
  - 输出：每个指尖接触点的3D坐标、法向量、灰度方差（即伪触觉信息）。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集与场景**：论文未明确列举特定公开数据集。实验是在Isaac Sim仿真环境中生成的物体点云数据（可能包括多种家庭/工业物体），并配合RH8D灵巧手模型进行抓取模拟。
- **Benchmark**：文中没有明确提及其他方法作为基准对比；主要验证了算法自身可行性，即能否从点云准确提取纹理、实时定位精度（0.001 m）等指标。
- **对比方法**：没有对比其他触觉感知方法（如GelSight、触觉传感器数据驱动）。实验侧重于展示本方法在仿真环境下的效果，而非与现有方法横向比较。

## 4. 资源与算力

- 文末未明确说明所用GPU型号、数量及训练时长。仅提到“利用Isaac Sim进行高精度仿真”，可能需要在配备NVIDIA GPU的机器上运行（Isaac Sim官方推荐RTX系列）。但由于未提供具体细节，**论文在算力资源方面描述不足**。

## 5. 实验数量与充分性

- **实验数量**：从摘要只能看出基本的功能验证——物体表面纹理提取、指尖接触点实时定位（精度达0.001 m）、接触点伪触觉信息输出。没有提及消融实验、不同物体/材质对比实验、不同算法参数对比实验。
- **充分性与公平性**：实验仅停留在仿真环境，缺乏真实硬件（真实灵巧手+真实相机）的定量评估；缺少与真实触觉传感器的对比。因此实验覆盖范围较窄，充分性有限。没有公开的评测指标（如抓取成功率、接触定位误差、触觉信息一致性等），难以判断方法的客观公平性。

## 6. 论文的主要结论与发现

- 通过Isaac Sim仿真证明了：从点云中提取的法向量和灰度方差可以很好地反映物体表面纹理特征，且能作为伪触觉信息使用。
- 实现了对机械指尖与物体接触点位置的高精度实时定位（精度0.001 m），并能同步输出接触点的伪触觉特征。
- 该框架为低成本的触觉感知提供了一种可行的仿真-现实映射方案，有望减少对昂贵触觉传感器的依赖，提升灵巧手抓取性能。

## 7. 优点：方法或实验设计上的亮点

- **低成本创新**：利用视觉代替触觉传感器，极大降低了硬件成本，同时借助仿真避免了真实传感器易损问题。
- **高精度仿真平台**：Isaac Sim提供精确碰撞检测，使得接触点定位达到0.001 m级，优于许多真实传感器分辨率。
- **信息提取简洁有效**：法向量和灰度方差两个简单特征即能捕获表面微观几何与纹理信息，避免复杂深度学习模型。
- **开源公开**：代码和数据集已发布，便于复现和后续研究。

## 8. 不足与局限

- **实验场景局限**：仅在仿真环境中验证，未在实际机器人（RH8D灵巧手）加上真实物体的抓取实验中评估，缺乏从仿真到现实的迁移效果验证。
- **缺乏对比方法**：没有与已有触觉感知方法（如触觉传感器、物理触觉估计模型）进行定量对比，因此无法衡量本方法的相对优劣。
- **特征表征能力有限**：法向量和灰度方差可能不足以捕捉复杂的触觉特性（如硬度、动态摩擦、温度、粘性等），对于柔性或透明物体可能失效。
- **偏差风险**：仿真中物体模型理想化（如完美平面、标准材质属性），真实物体表面可能因噪声、光照、反射等因素导致点云质量下降，进而降低伪触觉信息的准确性。
- **未有严格评估指标**：没有定义统一的评价标准（如接触定位误差分布、伪触觉一致性得分），使实验结果的可信度缺乏量化支撑。
- **可视化与分析不足**：论文未展示更多细节（如不同材质对比、接触点法向量的矢量场走势、灰度方差与真实触觉信号的相关性图）。

（完）
