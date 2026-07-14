---
title: "MultiPLY: A Multisensory Object-Centric Embodied Large Language Model in 3D World"
title_zh: MultiPLY：三维世界中的多感官物体中心具身大语言模型
authors: "Hong, Yining, Zheng, Zishuo, Chen, Peihao, Wang, Yian, Li, Junyan, Gan, Chuang"
date: 2024-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2024/papers/Hong_MultiPLY_A_Multisensory_Object-Centric_Embodied_Large_Language_Model_in_3D_CVPR_2024_paper.pdf"
tags: ["query:tactile-vla"]
score: 9.0
evidence: 多感官具身大语言模型，包含触觉
tldr: MultiPLY提出了一种多感官具身大语言模型，能够融合视觉、听觉、触觉和热感等多模态交互数据，建立词、动作和感知之间的关联。该模型通过主动探索3D环境收集多感官信息，弥补了现有大语言模型被动接收数据的不足。实验表明其在多感官场景理解任务上表现优异，为机器人多模态感知提供了新范式。
source: CVPR-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1711, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 737, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1516, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1498, \"height\": 755, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 894, \"height\": 605, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 770, \"height\": 568, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 900, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2024-accepted/cvpr-2024-hong-multiply-a-multisensory-object-centric-embodied-large-language-model-in-3d-cvpr-2024-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 583, \"height\": 311, \"label\": \"Table\"}]"
motivation: 现有大语言模型缺乏主动交互和收集多感官信息的能力，无法建立词、动作和感知之间的联系。
method: 提出MultiPLY模型，整合视觉、音频、触觉和热感信息，通过主动探索3D环境收集多感官数据。
result: 在多项多感官交互任务中取得领先性能，验证了主动多感官感知的有效性。
conclusion: MultiPLY成功将多感官交互数据融入大语言模型，为机器人多模态感知提供了新思路。
---

## Abstract
Human beings possess the capability to multiply a melange of multisensory cues while actively exploring and interacting with the 3D world. Current multi-modal large language models however passively absorb sensory data as inputs lacking the capacity to actively interact with the objects in the 3D environment and dynamically collect their multisensory information. To usher in the study of this area we propose MultiPLY a multisensory embodied large language model that could incorporate multisensory interactive data including visual audio tactile and thermal information into large language models thereby establishing the correlation among words actions and percepts. To this end we first collect Multisensory Universe a large-scale multisensory interaction dataset comprising 500k data by deploying an LLM-powered embodied agent to engage with the 3D environment. To perform instruction tuning with pre-trained LLM on such generated data we first encode the 3D scene as abstracted object-centric representations and then introduce action tokens denoting that the embodied agent takes certain actions within the environment as well as state tokens that represent the multisensory state observations of the agent at each time step. In the inference time MultiPLY could generate action tokens instructing the agent to take the action in the environment and obtain the next multisensory state observation. The observation is then appended back to the LLM via state tokens to generate subsequent text or action tokens. We demonstrate that MultiPLY outperforms baselines by a large margin through a diverse set of embodied tasks involving object retrieval tool use multisensory captioning and task decomposition.

---

## 论文详细总结（自动生成）

# 论文总结：MultiPLY: A Multisensory Object-Centric Embodied Large Language Model in 3D World

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：传统多模态大语言模型（如LLaVA、Flamingo、BLIP-2、PaLM-E）主要处理2D视觉-语言任务，缺乏对3D环境进行主动交互和动态收集多感官信息的能力。人类能够通过探索和交互（如视觉、听觉、触觉、温度）获取多感官线索，而现有模型只能被动接收数据，无法建立“词-动作-感知”之间的关联。
- **整体含义**：本文旨在构建一种能够主动与3D环境交互、融合多感官信息（视觉、听觉、触觉、热感）的具身大语言模型，从而弥合语言模型与机器人具身感知之间的鸿沟，为机器人多模态感知和决策提供新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出**MultiPLY**模型，通过引入“动作令牌”（Action Tokens）和“状态令牌”（State Tokens），让LLM能够主动生成动作指令，驱动具身代理在3D环境中执行交互（如导航、观察、触摸、敲击等），并接收多感官反馈作为后续输入，形成闭环的交互式推理。
- **关键技术细节**：
  - **多感官数据集**：构建**Multisensory Universe**，包含约50万条数据，由ChatGPT驱动的代理在HM3D场景中生成任务，并与新增的交互物体（来自ObjectFolder和Objaverse）交互，收集视觉、触觉（DiffTactile模拟）、温度、环境音、冲击声等感官数据。
  - **物体中心场景表示**：将3D场景抽象为物体中心表示（O×1024特征），使用ConceptGraphs+CLIP编码物体特征，并加入位置编码。环境音使用CLAP音频编码器。
  - **动作令牌**：定义特殊令牌如`<SELECT>`（选择物体）、`<NAVIGATE>`（导航）、`<OBSERVE>`（获取物体点云）、`<TOUCH>`（获取触觉和温度）、`<HIT>`（获取冲击声）、`<PICK-UP>`、`<PUT-DOWN>`、`<LOOK-AROUND>`等。
  - **状态令牌**：定义对应反馈令牌如`<OBJECT>`（点云特征）、`<IMPACT SOUND>`（冲击声）、`<TACTILE>`（触觉热力图）、`<TEMPERATURE>`（温度热力图）。各模态使用不同的编码器（CLIP、CLAP）及单层线性适配器映射到LLM特征空间。
  - **训练流程**：
    - 第一阶段：模态对齐，使用AudioSet、AudioCaps及ChatGPT生成的配文训练传感器-语言适配器，冻结图像编码器和LLM。
    - 第二阶段：指令微调，使用Multisensory Universe对整个模型（LLaVA backbone）进行微调，优化LLM损失和物体选择（`<SELECT>`）的二元交叉熵损失。
  - **推理**：模型生成动作令牌后，代理在Habitat-sim中执行动作，返回感官反馈并通过状态令牌注入LLM，继续生成后续文本或动作。

## 3. 实验设计

- **数据集与场景**：
  - 3D场景：基于Habitat-Matterport 3D (HM3D)语义数据集（216个空间，3100个房间）。
  - 新增交互物体：来自ObjectFolder（1000个物体网格，含冲击声、材料）和Objaverse（约80万3D物体），由ChatGPT选择并分配材质、温度等属性。
  - 评估时使用全新的场景和物体（不来自Multisensory Universe）。
- **benchmark**：四种具身任务：
  - 物体检索（Object Retrieval）：从多个相似物体中利用多感官数据检索正确目标。
  - 工具使用（Tool Use）：根据情境检索合适工具（需考虑材质、温度等）。
  - 多感官描述（Multisensory Captioning）：描述物体的多感官属性（需要交互）。
  - 任务分解（Task Decomposition）：将高层任务分解为子动作（需交互和感官反馈）。
- **对比方法**：
  - 单模态检索模型：CLIP、CLAP。
  - 多模态绑定模型：ImageBind、PointBind（2D/3D版本），包括无交互、有交互（Oracle）、微调版本。
  - LLM基座：PointBind-LLM、LLaVA、3D-LLM（均为微调或未微调版本）。
  - MultiPLY的2D变体（MultiPLY-2D）。

## 4. 资源与算力

- 文中明确说明：使用**FSDP（Fully Sharded Data Parallel）在128块V100 GPU**上高效训练。具体训练时长未提及，但提到两个阶段训练（第一阶段冻结部分参数，第二阶段全模型微调），且数据集规模为50万条数据。未提供具体的训练天数或小时数。

## 5. 实验数量与充分性

- **实验数量**：四大任务各有完整结果表（表1-4），每个任务对比了约8-12种基线方法。此外，文中提到在补充材料中进行了更多消融实验（如不同感官组合、有无交互的对比），但主文中未展示。
- **充分性与公正性**：
  - 覆盖了多种任务类型（检索、工具使用、描述、分解），体现了模型的通用性。
  - 基线方法包括无交互、Oracle交互、微调版本，实现公平对比。
  - 测试场景和物体均未在训练集中出现，保证了泛化性评估。
  - 但未报告方差或重复实验次数，也未提供详细的超参数设置。此外，工具使用和任务分解的成功率较低（MultiPLY分别为41.6%和30.2%），仍有提升空间。

## 6. 论文的主要结论与发现

- MultiPLY在四个任务上均大幅优于所有基线模型（如物体检索准确率56.7% vs PointBind-LLM 48.9%；工具使用41.6% vs PointBind-LLM 32.1%；多感官描述BLEU4 20.1 vs 14.5；任务分解30.2% vs 3D-LLM 22.4%）。
- **关键发现**：
  1. 多感官信息整合显著优于单模态。
  2. 3D表示优于2D表示。
  3. 基于LLM的交互式推理优于简单的相似度检索（绑定模型），因为LLM能逐步推理不同感官信息，而非简单融合。
  4. 主动交互（动作令牌驱动）比无交互或Oracle交互更有效，尤其在需要区分细微感官差异时。

## 7. 优点

- **方法创新**：首次将多感官交互数据（触觉、温度、冲击声）完整融入LLM，并设计动作/状态令牌机制实现端到端指令微调。
- **数据集贡献**：构建了规模达50万条的多感官交互数据集，涵盖多种任务，可促进后续研究。
- **实验设计全面**：在多种具身任务上评估，对比多种基线，并设置不同交互程度（无/有/微调）的消融，验证了交互和LLM推理的必要性。
- **代码与数据开源**：论文提供项目网站（https://vis-www.cs.umass.edu/multiply），促进可复现性。

## 8. 不足与局限

- **动作执行依赖预定义策略**：MultiPLY未涉及详细导航与控制策略，仅调用预定义路径规划模块，未实现端到端的具身控制。
- **模拟环境与真实世界差距**：所有实验在Habitat-sim中进行，触觉和声音为模拟数据，未在真实机器人上验证，可能存在sim-to-real gap。
- **数据集生成依赖ChatGPT**：ChatGPT可能引入偏见或错误，且任务生成依赖人工设计的提示词。
- **泛化能力有限**：工具使用和任务分解成功率较低（41.6%和30.2%），模型在复杂多步推理上仍有不足。
- **计算资源昂贵**：使用128块V100 GPU，对一般研究团队门槛较高。
- **消融实验不足**：主文仅提供四个整体任务结果，未在正文中展示详细消融（如不同感官组合的贡献、状态令牌的影响等），仅提及在补充材料中有，可能影响对模型各个模块重要性的直观理解。

（完）
