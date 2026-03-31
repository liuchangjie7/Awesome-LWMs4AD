# Awesome Latent World Models for Autonomous Driving

![License](https://img.shields.io/badge/license-MIT-blue.svg)
[![arXiv](https://img.shields.io/badge/arXiv-2X0X.XXXXX-<COLOR>.svg)](https://arxiv.org/abs/XXXX.XXXXX)

This is the official repository for the paper **Latent World Models for Autonomous Driving: A Comprehensive Survey**. We warmly welcome contributions from everyone to this repository. Please feel free to submit issues or pull requests for any missing papers, datasets, or methodologies. Our team is committed to maintaining and updating the repository regularly.

## Contents

- [Introduction](#introduction)
- [Methodology](#methodology)
  - [Feature Alignment](#feature-alignment)
  - [Value Alignment](#value-alignment)
  - [Behavior Alignment](#behavior-alignment)
- [Applications](#applications)
- [Benchmarks](#benchmarks)
  - [Benchmark Datasets](#Benchmark Datasets)
  - [Evaluation Metrics](#Evaluation Metrics)

- [Citation](#citation)

## Introduction

Autonomous driving is undergoing a critical paradigm shift toward cognitive reasoning architectures. While explicit generative world models suffer from high computational latency and pixel-level redundancies, **Latent World Models (LWMs)** offer a highly efficient alternative by compressing high-dimensional sensory inputs into compact, task-driven latent spaces. 

Our review systematically categorizes LWMs and maintains a live repository of the latest implementations, datasets, and evaluation metrics.

<div align="center">
  <img src="https://github.com/liuchangjie7/Awesome-LWMs4AD/blob/main/LWMs4AD.assets/chapter1.jpg" 
       alt="photo1"  />
</div>


## Methodology

We categorize Latent World Models into three core alignment paradigms based on their training objectives and inference mechanisms.

<div align="center">
  <img src="https://github.com/liuchangjie7/Awesome-LWMs4AD/blob/main/LWMs4AD.assets/chapter3_2.jpg" 
       alt="photo1"
       width="80%"/>
</div>

### Feature Alignment
> **Feature Alignment** learns spatio-temporal consistency without pixel reconstruction, filtering out high-frequency sensory noise to focus purely on core semantics and dynamics.

| Method | Latent Representation | Dynamics Architecture | Training Objective | Inference Mechanism | Open Source |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [I-JEPA](https://arxiv.org/pdf/2301.08243) | Continuous Patch | ViT Block | Latent Distance | Masked Prediction | [code](https://github.com/facebookresearch/ijepa) |
| [Dense-JEPA](https://openreview.net/pdf?id=8GCcSXlkZN) | Continuous Patch | Dense ViT Block | Latent Distance | Masked Prediction | ❌ |
| [C-JEPA](https://arxiv.org/pdf/2410.19560) | Continuous Patch | ViT Block | Distance Regularization | Masked Prediction | ❌ |
| [AD-L-JEPA](https://arxiv.org/pdf/2501.04969) | BEV Embeddings | BEV Transformer | Latent Distance | Masked Prediction | [code](https://github.com/HaoranZhuExplorer/adljepa) |
| [Point-JEPA](https://arxiv.org/pdf/2404.16432) | Point Embeddings | Point Transformer | Latent Distance | Masked Prediction | [code](https://github.com/Ayumu-J-S/Point-JEPA) |
| [V-JEPA](https://arxiv.org/pdf/2404.08471) | Spatiotemporal Clips | Video Transformer | Latent Distance | Masked Prediction | [code](https://github.com/facebookresearch/jepa) |
| [V-JEPA 2](https://arxiv.org/pdf/2506.09985) | Spatiotemporal Embeddings | Video Transformer | Latent Distance | Masked Prediction | [code](https://github.com/facebookresearch/vjepa2) |
| [Drive-JEPA](https://arxiv.org/pdf/2601.22032) | Planning Spatiotemporal | Video ViT Predictor | Task Latent Distance | Masked Pretraining | [code](https://github.com/linhanwang/Drive-JEPA) |
| [DINO-WM](https://arxiv.org/pdf/2411.04983) | Patch Features | ViT Block | Latent Distance | Forward Prediction | [code](https://github.com/gaoyuezhou/dino_wm) |
| [UnO](https://openaccess.thecvf.com/content/CVPR2024/papers/Agro_UnO_Unsupervised_Occupancy_Fields_for_Perception_and_Forecasting_CVPR_2024_paper.pdf) | Continuous 4D Field | Neural ODE | Occupancy Probability | Querying 4D Field | ❌ |
| [MC-JEPA](https://arxiv.org/pdf/2307.12698) | Decoupled Features | Decoupled Transformer | Latent Distance | Masked Prediction | ❌ |
| [PanDora](https://arxiv.org/pdf/2406.09455) | Video States and Language | Hybrid Transformer | Latent Distance | Autoregressive Generation | [code](https://github.com/maitrix-org/Pandora) |
| [LAW](https://arxiv.org/pdf/2406.08481) | Action Aware Latents | Action Conditioned Transformer | Action Latent Distance | Forward Prediction | [code](https://github.com/BraveGroup/LAW) |
| [T-JEPA](https://arxiv.org/pdf/2406.12913) | Trajectory Segments | Trajectory Transformer | Latent Distance | Masked Prediction | [code](https://github.com/Jacobieee/T-JEPA) |
| [HiT-JEPA](https://arxiv.org/pdf/2507.00028) | Trajectory Segments | Trajectory Transformer | Latent Distance | Masked Prediction | [code](https://anonymous.4open.science/r/HiT-JEPA/config.py) |

### Value Alignment
> **Value Alignment** optimizes internal simulators for downstream decision-making, transforming passive environmental representations into actionable planning substrates.

| Method | Latent Representation | Dynamics Architecture | Training Objective | Inference Mechanism | Open Source |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [MuZero](https://arxiv.org/pdf/1911.08265) | Continuous Space | Recurrent Network | Value Policy Reward | MCTS | ❌ |
| [EfficientZero](https://arxiv.org/pdf/2111.00210) | Continuous Space | Recurrent Network | Value Policy Consistency | MCTS | [code](https://github.com/YeWR/EfficientZero) |
| [Think2Drive](https://link.springer.com/chapter/10.1007/978-3-031-72995-9_9) | Sequence of Tokens | World Model Transformer | Value Reward | MCTS | ❌ |
| [L3P](https://proceedings.mlr.press/v139/zhang21x/zhang21x.pdf) | Graph of Landmarks | Topological Graph | Reachability Value | Graph Search | [code](https://github.com/LunjunZhang/world-model-as-a-graph) |
| [MILE](https://proceedings.neurips.cc/paper_files/paper/2022/file/827cb489449ea216e4a257c47e407d18-Paper-Conference.pdf) | Continuous Space | Probabilistic Imagination | Action Regression | Gradient Optimization | [code](https://github.com/wayveai/mile) |
| [UniAD](https://arxiv.org/pdf/2212.10156) | Continuous Queries | Query Transformer | Planning Loss | Gradient Optimization | [code](https://github.com/OpenDriveLab/UniAD) |
| [SafeDreamer](https://arxiv.org/pdf/2307.07176) | Continuous Space | RSSM Dreamer Architecture | Reward Safety Penalty | Lagrangian Optimization | [code](https://github.com/PKU-Alignment/SafeDreamer) |
| [DreamerAD](https://arxiv.org/pdf/2603.24587) | Denoised Latent Features | DiT Shortcut Forcing | Latent Reward GRPO | Single Step Latent RL | ❌ |
| [WorldRFT](https://doi.org/10.1609/aaai.v40i14.38149) | Spatially Aware Latents | Hierarchical Transformer | Planning Aligned RFT | Iterative Refinement | [code](https://github.com/pengxuanyang/WorldRFT) |

### Behavior Alignment
> **Behavior Alignment** models multi-agent interactive trajectories, decoupling the scene to learn independent latent features and causal relationships for various traffic participants.

| Method | Latent Representation | Dynamics Architecture | Training Objective | Inference Mechanism | Open Source |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [MultiPath++](https://arxiv.org/pdf/2111.14973) | Object Centric Latents | Interaction Graph | Trajectory Distance | Anchor Inference | ❌ |
| [TrafficBots](https://arxiv.org/pdf/2303.04116) | Personality Embeddings | Scene Centric CVAE | ELBO Prediction | Conditioned Sampling | [code](https://github.com/zhejz/TrafficBots) |
| [CCE-MASAC](https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/05085.pdf) | Multi Agent Game Latents | Markov Game Dynamics | Nash Equilibrium Objective | Game Theoretic Rollout | [code](https://github.com/qiaoguanren/Multi-agent-Competitive-Autonomous-Driving) |
| [CarFormer](https://arxiv.org/pdf/2407.15843) | Latent Object Slots | Autoregressive Transformer | Trajectory Alignment | Slot Attention Decoding | [code](https://github.com/Shamdan17/CarFormer) |
| [Wayformer](https://arxiv.org/pdf/2207.05844) | Scene Tokens | Multi Axis Attention | Trajectory Alignment | Scene Centric Decoding | ❌ |
| [Forecast-MAE](https://arxiv.org/pdf/2308.09882) | Trajectory Context Tokens | Masked Autoencoder | Trajectory Reconstruction | Mask Predict Decoding | [code](https://github.com/jchengai/forecast-mae) |



## Applications

This section summarizes how Latent World Models are deployed across various autonomous driving tasks, from environmental dynamics modeling to safety-critical control.

<div align="center">
  <img src="https://github.com/liuchangjie7/Awesome-LWMs4AD/blob/main/LWMs4AD.assets/chapter4_1.jpg" 
       alt="photo1"  />
</div>

| Method                                                       | Application Scenario | Key Contribution                           | Control Type      | Open Source                                                  |
| :----------------------------------------------------------- | :------------------- | :----------------------------------------- | :---------------- | :----------------------------------------------------------- |
| [DriveWorld](https://openaccess.thecvf.com/content/CVPR2024/papers/Min_DriveWorld_4D_Pre-trained_Scene_Understanding_via_World_Models_for_Autonomous_CVPR_2024_paper.pdf) | Latent Dynamics      | 4D spatiotemporal disentanglement          | Open-loop         | ❌                                                            |
| [Drive-OccWorld](https://doi.org/10.1609/aaai.v39i9.33010)   | Latent Dynamics      | Vision-centric 4D occupancy forecasting    | Open-loop         | [code](https://github.com/yuyang-cloud/Drive-OccWorld)       |
| [OccLLAMA](https://arxiv.org/pdf/2409.03272)                 | Latent Dynamics      | Unified geometry-language representation   | Open-loop         | ❌                                                            |
| [BYOL-Drive](https://www.mdpi.com/2075-1702/13/3/231)        | Latent Dynamics      | Probabilistic dynamics for robustness      | Open-loop         | ❌                                                            |
| [Iso-Dream](https://proceedings.neurips.cc/paper_files/paper/2022/file/9316769afaaeeaad42a9e3633b14e801-Paper-Conference.pdf) | Predictive Driving   | Disentangling ego-motion and env-flow      | Open-loop         | [code](https://github.com/panmt/Iso-Dream)                   |
| [PIWM](https://arxiv.org/pdf/2509.12437)                     | Predictive Driving   | Emergence of physical laws in latent space | Open-loop         | [code](https://github.com/TUM-AVS/physics-wm)                |
| [EOT-WM](https://doi.org/10.1609/aaai.v40i16.38403)          | Predictive Driving   | Multi-agent trajectory co-evolution        | Open-loop         | ❌                                                            |
| [Dreamer](https://arxiv.org/pdf/1912.01603)                  | Predictive Control   | Complex objective-driven behaviors         | Closed-loop       | [code](https://github.com/danijar/dreamer)                   |
| [TD-MPC2](https://arxiv.org/pdf/2310.16828)                  | Predictive Control   | Scalable latent-space policy optimization  | Closed-loop (MPC) | [code](https://github.com/nicklashansen/tdmpc2)              |
| [UniAD](https://dl.acm.org/doi/pdf/10.1145/3009957)          | Predictive Control   | Fully end-to-end planning alignment        | Closed-loop       | [code](https://github.com/OpenDriveLab/UniAD)                |
| [SafeDreamer](https://arxiv.org/pdf/2307.07176)              | Safety Verification  | Risk costs integrated into imagination     | Closed-loop       | [code](https://github.com/PKU-Alignment/SafeDreamer)         |
| [TOKEN](https://arxiv.org/pdf/2407.00959)                    | Safety Verification  | Object-level tokens for long-tail events   | Open-loop         | [code](https://github.com/thomasrantian/TOKEN_MM-LLM_for_AutoDriving) |
| [NVIDIA Cosmos](https://arxiv.org/pdf/2501.03575)            | Safety Verification  | Large-scale physical consistency           | Simulation-free   | [code](https://github.com/Saloni1Parekh609/Cosmos)           |



## Benchmarks

LWMs fundamentally reshape autonomous driving paradigms by discarding pixel-level reconstruction. This unique latent architecture renders traditional evaluation pipelines obsolete. This section systematically outlines the essential benchmark datasets and tailored multidimensional evaluation metrics.

### Benchmark Datasets

> To comprehensively support the dynamic rollouts and interactive decision-making of LWMs, existing benchmark datasets are categorized into the following four domains. *(Click on the dataset names to access their official repositories).*

| Dataset                                                      | Year | Dataset Size      | Input Modality       | Key Annotations                  | Supported Evaluation       |
| :----------------------------------------------------------- | :--- | :---------------- | :------------------- | :------------------------------- | :------------------------- |
| **1) Dynamics Learning**                                     |      |                   |                      |                                  |                            |
| [**nuScenes**](https://www.nuscenes.org/nuscenes)            | 2020 | 40K frames        | Camera, LiDAR, Radar | 3D BBox, Map, Ego Pose           | Open-loop Planning         |
| [**Waymo Open**](https://waymo.com/open/)                    | 2020 | 104K frames       | Camera, LiDAR        | 3D BBox, Map, Trajectories       | Open-loop Planning         |
| [**Argoverse 2**](https://github.com/argoverse/av2-api)      | 2023 | 250K logs         | Camera, LiDAR        | HD Map, Multi-Agent Trajectories | Open-loop Planning         |
| [**WOMD-E2E**](https://waymo.com/open/data/motion/)          | 2024 | 4,021 clips       | Camera, LiDAR        | Multi-Agent Trajectories, Action | Reactive Closed-loop       |
| **2) Video Pretraining**                                     |      |                   |                      |                                  |                            |
| [**OpenDV-2K**](https://github.com/OpenDriveLab/DriveAGI)    | 2024 | 65.1M frames      | Camera Only          | Pseudo Ego Trajectory            | Latent Representation      |
| [**BDD100K**](https://bair.berkeley.edu/blog/2018/05/30/bdd/) | 2020 | 100K videos       | Camera Only          | 2D BBox, Lane & Turn Actions     | Domain Adaptation          |
| [**SHIFT**](https://github.com/SysCV/shift-dev)              | 2022 | 5M frames         | Multimodal           | Dense Depth, Segmentation        | Domain Adaptation          |
| [**DrivePhysica**](https://github.com/DrivePhysica)          | 2024 | 10M frames        | Camera Only          | Unannotated Physics Evolution    | Video Pretraining          |
| **3) Closed-loop Simulators**                                |      |                   |                      |                                  |                            |
| [**nuPlan**](https://www.nuscenes.org/nuplan)                | 2021 | 1,500 hours       | Camera, LiDAR, Map   | Human Trajectories, Ego Action   | Reactive Closed-loop       |
| [**Bench2Drive**](https://github.com/Thinklab-SJTU/Bench2Drive) | 2024 | 10K clips         | Multimodal           | Dense Action, Ego State          | CARLA Closed-loop          |
| [**NAVSIM**](https://github.com/autonomousvision/navsim)     | 2024 | >1M frames        | Camera, LiDAR        | Action-Trajectory Alignment      | Non-reactive Closed-loop   |
| **4) VLA Reasoning**                                         |      |                   |                      |                                  |                            |
| [**DriveLM**](https://github.com/OpenDriveLab/DriveLM)       | 2024 | 445K QA pairs     | Camera, LiDAR        | Graph QA, Logical Reasoning      | Instruction Fidelity       |
| [**LMDrive**](https://github.com/opendilab/LMDrive)          | 2024 | 120K trajectories | Camera, Text         | Nav Prompts, Ego Action          | Language-guided Control    |
| [**Rank2Tell**](https://usa.honda-ri.com/rank2tell)          | 2024 | 50K trajectories  | Camera, LiDAR        | Importance Ranking, Ego Action   | Reasoning Interpretability |
| [**AutoVLA**](https://github.com/ucla-mobility/AutoVLA)      | 2024 | 80K episodes      | Multimodal           | Multimodal QA, Policy Steps      | VLA Reasoning              |

### Evaluation Metrics

> Evaluating LWMs requires multidimensional quantitative metrics that go beyond pixel-level reconstruction. We summarize the indispensable metrics tailored for latent architectures below. 

| Category                   |     Dir.     | Metric        | Full Name                  | Definition / Formula                                         | Target Capability           |
| :------------------------- | :----------: | :------------ | :------------------------- | :----------------------------------------------------------- | :-------------------------- |
| **Latent Quality**         |  $\uparrow$  | **LP**        | Linear Probing             | Downstream task accuracy of frozen encoder                   | Semantic Disentanglement    |
|                            | $\downarrow$ | **LPE**       | Latent Prediction Error    | $\Vert z_{t+1} - \hat{z}_{t+1} \Vert_2^2$ or $1 - \cos(z_{t+1}, \hat{z}_{t+1})$ | Dynamics Consistency        |
|                            |  $\uparrow$  | **LHC**       | Long-Horizon Consistency   | Error decay over multi-step unrolling                        | Temporal Stability          |
|                            |  $\uparrow$  | **DS**        | Disentanglement Score      | InfoNCE loss for action-environment independence             | Action-Conditioned Fidelity |
|                            |  $\uparrow$  | **TCS**       | Temporal Consistency       | Variance of transitions across adjacent frames               | Motion Smoothness           |
|                            |  $\uparrow$  | **NMI**       | Normalized Mutual Info.    | Mutual information of latent clusters and labels             | Feature Interpretability    |
|                            | $\downarrow$ | **LPIPS-F**   | Feature-level LPIPS        | Perceptual similarity in feature space                       | Perceptual Preservation     |
| **Open-loop Accuracy**     | $\downarrow$ | **ADE / FDE** | Avg / Final Disp. Error    | $\frac{1}{T} \sum_{t=1}^{T} \Vert p_t - \hat{p}_t \Vert_2$ and $\Vert p_T - \hat{p}_T \Vert_2$ | Trajectory Accuracy         |
|                            | $\downarrow$ | **CR**        | Collision Rate             | $\%$ of predictions intersecting obstacles                   | Safety Awareness            |
|                            | $\downarrow$ | **MR**        | Miss Rate                  | $\%$ of unpredicted ground-truth trajectories                | Scenario Coverage           |
|                            |  $\uparrow$  | **PDMS**      | Predictive Driver Score    | Consistency with human driving patterns                      | Human-like Interaction      |
| **Closed-loop Robustness** |  $\uparrow$  | **DS**        | Driving Score              | $\text{Route Completion} \times (1 - \text{Penalty})$        | Comprehensive Policy        |
|                            |  $\uparrow$  | **SR**        | Success Rate               | $\%$ of collision-free completed episodes                    | Safe Navigation Limit       |
|                            | $\downarrow$ | **IS**        | Infraction Score           | Cumulative penalty for traffic violations                    | Long-tail Safety            |
|                            |  $\uparrow$  | **RC**        | Route Completion           | $\%$ of planned route successfully traversed                 | Goal-directed Execution     |
|                            |  $\uparrow$  | **IF**        | Instruction Fidelity       | Alignment with natural language prompts                      | Language-guided Control     |
|                            |  $\uparrow$  | **RI**        | Reasoning Interpretability | CoT consistency with human logic                             | Action Explainability       |


## Citation

If you find this repository or our survey useful for your research, please consider citing our paper:

```bibtex
