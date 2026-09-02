# Awesome Latent World Models for Autonomous Driving

![arXiv](https://img.shields.io/badge/arXiv-coming%20soon-lightgrey.svg)

This is the official repository for the paper **Latent World Models for Autonomous Driving: A Taxonomy and Survey**. We welcome issues and pull requests for missing papers, datasets, code, and corrections.

## Contents

- [Introduction](#introduction)
- [Methodology](#methodology)
  - [Feature Alignment](#feature-alignment)
  - [Value Alignment](#value-alignment)
  - [Behavior Alignment](#behavior-alignment)
- [Applications](#applications)
- [Benchmarks](#benchmarks)
  - [Benchmark Datasets](#benchmark-datasets)
  - [Evaluation Metrics](#evaluation-metrics)
- [Citation](#citation)
- [Contributing](#contributing)
- [Contact](#contact)
- [License](#license)

## Introduction

Autonomous driving is evolving from fragmented modular pipelines toward more integrated system-level architectures for perception--prediction--planning--control coordination. **Latent World Models (LWMs)** provide a compact systems-oriented modeling paradigm for connecting perception, prediction, and decision-making by compressing high-dimensional sensory inputs into latent states that support downstream prediction and planning.

This repository tracks representative papers, datasets, metrics, and open-source projects related to LWMs for autonomous driving. The taxonomy and terminology follow the revised survey manuscript.

<div align="center">
  <img src="./LWMs4AD.assets/chapter1.jpg"
       alt="Systematic overview of LWMs for autonomous driving"
       width="90%"/>
</div>

## Methodology

We categorize LWMs according to their dominant alignment objectives: **feature alignment**, **value alignment**, and **behavior alignment**. Methods that provide temporally consistent latent rollout are treated as core LWMs, while methods that mainly provide latent interaction priors without closed-loop action-conditioned rollout are treated as LWM-related modules.

<div align="center">
  <img src="./LWMs4AD.assets/chapter3_2.jpg"
       alt="Taxonomy of latent world model methods"
       width="80%"/>
</div>

### Feature Alignment

> **Feature Alignment** learns latent representation or dynamics consistency without relying primarily on pixel-level reconstruction.

| Method | Latent Representation | Dynamics Architecture | Training Objective | Inference Mechanism | Open Source |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [I-JEPA](https://arxiv.org/abs/2301.08243) | Continuous Patch | ViT Block | Latent Distance | Masked Prediction | [code](https://github.com/facebookresearch/ijepa) |
| [Dense-JEPA](https://openreview.net/forum?id=8GCcSXlkZN) | Continuous Patch | Dense ViT Block | Latent Distance | Masked Prediction | ❌ |
| [C-JEPA](https://proceedings.neurips.cc/paper_files/paper/2024/hash/ba2255d847c8223ce8e2d62b2016ad2f-Abstract-Conference.html) | Continuous Patch | ViT Block | Distance Regularization | Masked Prediction | ❌ |
| [AD-L-JEPA](https://arxiv.org/abs/2501.04969) | BEV Embeddings | BEV Transformer | Latent Distance | Masked Prediction | [code](https://github.com/HaoranZhuExplorer/adljepa) |
| [Point-JEPA](https://arxiv.org/abs/2404.16432) | Point Embeddings | Point Transformer | Latent Distance | Masked Prediction | [code](https://github.com/Ayumu-J-S/Point-JEPA) |
| [V-JEPA](https://openreview.net/forum?id=WFYbBOEOtv) | Spatiotemporal Clips | Video Transformer | Latent Distance | Masked Prediction | [code](https://github.com/facebookresearch/jepa) |
| [V-JEPA 2](https://arxiv.org/abs/2506.09985) | Spatiotemporal Embeddings | Video Transformer | Latent Distance | Masked Prediction | [code](https://github.com/facebookresearch/vjepa2) |
| [Drive-JEPA](https://arxiv.org/abs/2601.22032) | Planning Spatiotemporal | Video ViT Predictor | Task Latent Distance | Masked Pretraining | [code](https://github.com/linhanwang/Drive-JEPA) |
| [DINO-WM](https://arxiv.org/abs/2411.04983) | Patch Features | ViT Block | Latent Distance | Forward Prediction | [code](https://github.com/gaoyuezhou/dino_wm) |
| [UnO](https://openaccess.thecvf.com/content/CVPR2024/html/Agro_UnO_Unsupervised_Occupancy_Fields_for_Perception_and_Forecasting_CVPR_2024_paper.html) | Continuous 4D Field | Neural ODE | Occupancy Probability | Querying 4D Field | ❌ |
| [MC-JEPA](https://arxiv.org/abs/2307.12698) | Decoupled Features | Decoupled Transformer | Latent Distance | Masked Prediction | ❌ |
| [PanDora](https://arxiv.org/abs/2406.09455) | Video States and Language | Hybrid Transformer | Latent Distance | Autoregressive Generation | [code](https://github.com/maitrix-org/Pandora) |
| [LAW](https://arxiv.org/abs/2406.08481) | Action Aware Latents | Action Conditioned Transformer | Action Latent Distance | Forward Prediction | [code](https://github.com/BraveGroup/LAW) |
| [T-JEPA](https://dl.acm.org/doi/10.1145/3678717.3691281) | Trajectory Segments | Trajectory Transformer | Latent Distance | Masked Prediction | [code](https://github.com/Jacobieee/T-JEPA) |
| [HiT-JEPA](https://arxiv.org/abs/2507.00028) | Trajectory Segments | Trajectory Transformer | Latent Distance | Masked Prediction | [code](https://anonymous.4open.science/r/HiT-JEPA/config.py) |

### Value Alignment

> **Value Alignment** optimizes latent simulators or latent dynamics for decision-related values, rewards, costs, or policies.

| Method | Latent Representation | Dynamics Architecture | Training Objective | Inference Mechanism | Open Source |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [MuZero](https://www.nature.com/articles/s41586-020-03051-4) | Continuous Space | Recurrent Network | Value Policy Reward | MCTS | ❌ |
| [EfficientZero](https://proceedings.neurips.cc/paper/2021/hash/3305f2cfc46c0f045fe1f39b4afc1a23-Abstract.html) | Continuous Space | Recurrent Network | Value Policy Consistency | MCTS | [code](https://github.com/YeWR/EfficientZero) |
| [Think2Drive](https://link.springer.com/chapter/10.1007/978-3-031-72995-9_9) | Sequence of Tokens | World Model Transformer | Value Reward | MCTS | ❌ |
| [L3P](https://proceedings.mlr.press/v139/zhang21x.html) | Graph of Landmarks | Topological Graph | Reachability Value | Graph Search | [code](https://github.com/LunjunZhang/world-model-as-a-graph) |
| [MILE](https://proceedings.neurips.cc/paper_files/paper/2022/hash/827cb489449ea216e4a257c47e407d18-Abstract-Conference.html) | Continuous Space | Probabilistic Imagination | Action Regression | Gradient Optimization | [code](https://github.com/wayveai/mile) |
| [UniAD](https://openaccess.thecvf.com/content/CVPR2023/html/Hu_Planning-Oriented_Autonomous_Driving_CVPR_2023_paper.html) | Continuous Queries | Query Transformer | Planning Loss | Gradient Optimization | [code](https://github.com/OpenDriveLab/UniAD) |
| [SafeDreamer](https://arxiv.org/abs/2307.07176) | Continuous Space | RSSM Dreamer Architecture | Reward Safety Penalty | Lagrangian Optimization | [code](https://github.com/PKU-Alignment/SafeDreamer) |
| [DreamerAD](https://arxiv.org/abs/2603.24587) | Denoised Latent Features | DiT Shortcut Forcing | Latent Reward GRPO | Single Step Latent RL | ❌ |
| [WorldRFT](https://doi.org/10.1609/aaai.v40i14.38149) | Spatially Aware Latents | Hierarchical Transformer | Planning Aligned RFT | Iterative Refinement | [code](https://github.com/pengxuanyang/WorldRFT) |
| [SoAD](https://ieeexplore.ieee.org/abstract/document/11516327) | Vector World States | Vector World Model | Safety Value Estimation | Planning Rescoring | ❌ |

### Behavior Alignment

> **Behavior Alignment** models multi-agent interactions, behavior distributions, and traffic simulation priors.

| Method | Latent Representation | Dynamics Architecture | Training Objective | Inference Mechanism | Open Source |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [TrafficSim](https://openaccess.thecvf.com/content/CVPR2021/html/Suo_TrafficSim_Learning_To_Simulate_Realistic_Multi-Agent_Behaviors_CVPR_2021_paper.html) | Joint Agent Latents | Differentiable Simulator | Behavior Imitation | Closed-loop Rollout | ❌ |
| [TrafficBots](https://arxiv.org/abs/2303.04116) | Personality Embeddings | Scene-Centric CVAE | ELBO Prediction | Conditioned Sampling | [code](https://github.com/zhejz/TrafficBots) |
| [TrafficBots V1.5](https://arxiv.org/abs/2406.10898) | Agent Tokens | CVAE and Transformer | Conditional Prediction | Closed-loop Simulation | [code](https://github.com/zhejz/TrafficBotsV1.5) |
| [CCE-MASAC](https://www.ecva.net/papers/eccv_2024/papers_ECCV/html/5085_ECCV_2024_paper.php) | Multi-Agent Game Latents | Markov Game Dynamics | Nash Equilibrium | Game Rollout | [code](https://github.com/qiaoguanren/Multi-agent-Competitive-Autonomous-Driving) |
| [CarFormer](https://arxiv.org/abs/2407.15843) | Latent Object Slots | Autoregressive Transformer | Trajectory Alignment | Slot Decoding | [code](https://github.com/Shamdan17/CarFormer) |
| [ProSim](https://arxiv.org/abs/2409.05863) | Prompted Agent States | Prompted Simulator | Behavior Imitation | Prompted Rollout | [code](https://github.com/Ariostgx/ProSim) |
| [AutoWorld](https://arxiv.org/abs/2603.28963) | Multi-Agent Latents | Self-Supervised WM | Self-Supervised Behavior | Simulation Rollout | ❌ |
| [MultiPath++](https://arxiv.org/abs/2111.14973)† | Object-Centric Latents | Interaction Graph | Trajectory Distance | Anchor Inference | ❌ |
| [Wayformer](https://arxiv.org/abs/2207.05844)† | Scene Tokens | Multi-Axis Attention | Trajectory Alignment | Scene Decoding | ❌ |
| [Forecast-MAE](https://openaccess.thecvf.com/content/ICCV2023/html/Cheng_Forecast-MAE_Self-supervised_Pre-training_for_Motion_Forecasting_with_Masked_Autoencoders_ICCV_2023_paper.html)† | Trajectory Context Tokens | Masked Autoencoder | Trajectory Reconstruction | Mask Decoding | [code](https://github.com/jchengai/forecast-mae) |

† indicates behavior-aligned LWM-related modules rather than full closed-loop LWMs.

## Applications

This section summarizes how LWMs are used across autonomous driving tasks, from latent dynamics modeling to anticipatory driving, predictive control, and safety verification.

<div align="center">
  <img src="./LWMs4AD.assets/chapter4_1.jpg"
       alt="Applications of LWMs in autonomous driving"
       width="80%"/>
</div>

| Method | Application Scenario | Key Contribution | Control Type | Open Source |
| :--- | :--- | :--- | :--- | :--- |
| [DriveWorld](https://openaccess.thecvf.com/content/CVPR2024/html/Min_DriveWorld_4D_Pre-Trained_Scene_Understanding_via_World_Models_for_Autonomous_CVPR_2024_paper.html) | Latent Dynamics | 4D spatiotemporal representation | Open-loop | ❌ |
| [Drive-OccWorld](https://doi.org/10.1609/aaai.v39i9.33010) | Latent Dynamics | Vision-centric 4D occupancy forecasting | Open-loop | [code](https://github.com/yuyang-cloud/Drive-OccWorld) |
| [OccLLaMA](https://arxiv.org/abs/2409.03272) | Latent Dynamics | Geometry-language-action latent representation | Open-loop | ❌ |
| [BYOL-Drive](https://www.mdpi.com/2075-1702/13/3/231) | Latent Dynamics | Probabilistic world modeling for representation learning | Open-loop | ❌ |
| [AdaWorld](https://arxiv.org/abs/2503.18938) | Latent Dynamics | Adaptable latent actions for world modeling | Open-loop | ❌ |
| [Iso-Dream](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9316769afaaeeaad42a9e3633b14e801-Abstract-Conference.html) | Anticipatory Driving | Separating controllable and noncontrollable dynamics | Open-loop | [code](https://github.com/panmt/Iso-Dream) |
| [PIWM](https://arxiv.org/abs/2509.12437) | Anticipatory Driving | Physical-world simulation prior | Open-loop | [code](https://github.com/TUM-AVS/physics-wm) |
| [TOKEN](https://arxiv.org/abs/2407.00959) | Safety Verification | Object-level tokens for long-tail events | Open-loop | [code](https://github.com/thomasrantian/TOKEN_MM-LLM_for_AutoDriving) |
| [Dreamer](https://arxiv.org/abs/1912.01603) | Predictive Control | Latent imagination for objective-driven control | Closed-loop | [code](https://github.com/danijar/dreamer) |
| [TD-MPC2](https://arxiv.org/abs/2310.16828) | Predictive Control | Latent-space policy optimization | Closed-loop MPC | [code](https://github.com/nicklashansen/tdmpc2) |
| [UniAD](https://openaccess.thecvf.com/content/CVPR2023/html/Hu_Planning-Oriented_Autonomous_Driving_CVPR_2023_paper.html) | Predictive Control | Planning-oriented end-to-end alignment | Closed-loop | [code](https://github.com/OpenDriveLab/UniAD) |
| [SafeDreamer](https://arxiv.org/abs/2307.07176) | Safety Verification | Risk costs integrated into latent imagination | Closed-loop | [code](https://github.com/PKU-Alignment/SafeDreamer) |
| [SoAD](https://ieeexplore.ieee.org/abstract/document/11516327) | Safety Verification  | Safety-oriented value estimation with world-model rollouts | Closed-loop           | ❌                                                            |
| [NVIDIA Cosmos](https://arxiv.org/abs/2501.03575) | Safety Verification | Generative simulation and scenario generation | Generative simulation | [code](https://github.com/nvidia-cosmos/cosmos-predict1) |

## Benchmarks

LWMs shift part of autonomous-driving evaluation from pixel-level reconstruction toward latent prediction, decision relevance, and closed-loop behavior. Therefore, evaluating LWMs requires metrics covering latent quality, open-loop accuracy, closed-loop robustness, and reasoning-oriented assessment.

### Benchmark Datasets

The following datasets and simulators support different aspects of LWM evaluation, including dynamics learning, video pretraining, closed-loop simulation, and VLA reasoning.

| Dataset | Year | Dataset Size | Input Modality | Key Annotations | Supported Evaluation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1) Dynamics Learning** | | | | | |
| [nuScenes](https://www.nuscenes.org/nuscenes) | 2020 | 40K frames | Camera, LiDAR, Radar | 3D BBox, Map, Ego Pose | Open-loop Planning |
| [Waymo Open](https://waymo.com/open/) | 2020 | 104K frames | Camera, LiDAR | 3D BBox, Map, Trajectories | Open-loop Planning |
| [Argoverse 2](https://github.com/argoverse/av2-api) | 2023 | 250K logs | Camera, LiDAR | HD Map, Multi-Agent Trajectories | Open-loop Planning |
| [WOMD-E2E](https://waymo.com/open/data/motion/) | 2024 | 4,021 clips | Camera, LiDAR | Multi-Agent Trajectories, Action | Reactive Closed-loop |
| **2) Video Pretraining** | | | | | |
| [OpenDV-2K](https://github.com/OpenDriveLab/DriveAGI) | 2024 | 65.1M frames | Camera Only | Pseudo Ego Trajectory | Latent Representation |
| [BDD100K](https://bair.berkeley.edu/blog/2018/05/30/bdd/) | 2020 | 100K videos | Camera Only | 2D BBox, Lane and Turn Actions | Domain Adaptation |
| [SHIFT](https://github.com/SysCV/shift-dev) | 2022 | 5M frames | Multimodal | Dense Depth, Segmentation | Domain Adaptation |
| [DrivePhysica](https://github.com/DrivePhysica) | 2024 | 10M frames | Camera Only | Unannotated Physics Evolution | Video Pretraining |
| **3) Closed-loop Simulators** | | | | | |
| [nuPlan](https://www.nuscenes.org/nuplan) | 2021 | 1,500 hours | Camera, LiDAR, Map | Human Trajectories, Ego Action | Reactive Closed-loop |
| [Bench2Drive](https://github.com/Thinklab-SJTU/Bench2Drive) | 2024 | 10K clips | Multimodal | Dense Action, Ego State | CARLA Closed-loop |
| [NAVSIM](https://github.com/autonomousvision/navsim) | 2024 | Over 1M frames | Camera, LiDAR | Action-Trajectory Alignment | Non-reactive Closed-loop |
| **4) VLA Reasoning** | | | | | |
| [DriveLM](https://github.com/OpenDriveLab/DriveLM) | 2024 | 445K QA pairs | Camera, LiDAR | Graph QA, Logical Reasoning | Instruction Fidelity |
| [LMDrive](https://github.com/opendilab/LMDrive) | 2024 | 120K trajectories | Camera, Text | Nav Prompts, Ego Action | Language-guided Control |
| [Rank2Tell](https://usa.honda-ri.com/rank2tell) | 2024 | 50K trajectories | Camera, LiDAR | Importance Ranking, Ego Action | Reasoning Interpretability |
| [AutoVLA](https://github.com/ucla-mobility/AutoVLA) | 2024 | 80K episodes | Multimodal | Multimodal QA, Policy Steps | VLA Reasoning |

### Evaluation Metrics

Evaluating LWMs requires multidimensional quantitative metrics that go beyond pixel-level reconstruction. The following table summarizes metrics for latent quality, open-loop accuracy, closed-loop robustness, and reasoning-oriented assessment.

| Category | Dir. | Metric | Full Name | Definition / Formula | Target Capability |
| :--- | :---: | :--- | :--- | :--- | :--- |
| **Latent Quality** | ↑ | **LP** | Linear Probing | Downstream task accuracy of frozen encoder | Semantic Disentanglement |
| | ↓ | **LPE** | Latent Prediction Error | `||z_{t+1} - zhat_{t+1}||_2^2` or `1 - cos(z_{t+1}, zhat_{t+1})` | Dynamics Consistency |
| | ↓ | **LHE** | Long-Horizon Error | Accumulated error over multi-step unrolling | Rollout Stability |
| | ↑ | **DS** | Disentanglement Score | Action--environment separability | Action-Conditioned Fidelity |
| | ↑ | **TCS** | Temporal Consistency Score | Inverse transition variance across adjacent frames | Motion Smoothness |
| | ↑ | **NMI** | Normalized Mutual Info. | Mutual information of latent clusters and labels | Feature Interpretability |
| | ↓ | **LPIPS-F** | Feature-level LPIPS | Perceptual similarity in feature space | Perceptual Preservation |
| **Open-loop Accuracy** | ↓ | **ADE / FDE** | Average / Final Disp. Error | Average and final displacement errors between predicted and target trajectories | Trajectory Accuracy |
| | ↓ | **CR** | Collision Rate | Percentage of predictions intersecting obstacles | Safety Awareness |
| | ↓ | **MR** | Miss Rate | Percentage of unpredicted ground-truth trajectories | Scenario Coverage |
| | ↑ | **PDMS** | Predictive Driver Score | Consistency with human driving patterns | Human-like Interaction |
| **Closed-loop Robustness** | ↑ | **DriS** | Driving Score | `Route Completion x (1 - Penalty)` | Comprehensive Policy |
| | ↑ | **SR** | Success Rate | Percentage of collision-free completed episodes | Safe Task Completion |
| | ↓ | **IS** | Infraction Score | Cumulative penalty for traffic violations | Long-tail Safety |
| | ↑ | **RC** | Route Completion | Percentage of planned route successfully traversed | Goal-directed Execution |
| | ↑ | **IF** | Instruction Fidelity | Alignment with natural language prompts | Language-guided Control |
| | ↑ | **RI** | Reasoning Interpretability | CoT consistency with human logic | Action Explainability |

## Citation

If you find this repository or our survey useful for your research, please consider citing our paper:

```bibtex
@article{liu2026latent,
  title={Latent World Models for Autonomous Driving: A Taxonomy and Survey},
  author={Liu, Changjie and Liu, Zhuolin and He, Dantong and Gong, Xun and Li, Nan and Chen, Hong},
  journal={Manuscript under review},
  year={2026}
}
```

## Contributing

Issues and pull requests are welcome for missing papers, datasets, code links, and corrections.

## Contact

Please use GitHub issues for paper updates, repository corrections, and requests.

## License

A license will be added after publication.
