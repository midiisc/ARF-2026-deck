# Knowledge Base-Enhanced Vision-Language-Action Models for Robotic Task Planning

**Category:** Mid-long term theme

**Tech. Field:** Embodied AI, Robotic Task Planning, Vision-Language-Action (VLA) Models, Knowledge Base (KB) Integration

## Proposal Background

### Difficulties to be solved

Current Vision-Language-Action (VLA) models lack structured world knowledge, context-awareness, and reasoning capabilities. This leads to high failure rates in multi-step tasks, unsafe actions (e.g., improper tool handling), and an inability to generalize to unseen objects or apply task-specific constraints. Baseline performance in complex tasks is often low (e.g., 45-55% success).

### Expected result

By integrating a Knowledge Base (KB), the VLA model will become context-aware, enabling it to perform complex, multi-step tasks more effectively and safely. We expect to achieve:

- A >15% improvement in task-planning success over baseline models.
- A >70% success rate on multi-step planning tasks involving unseen objects.
- A >10% improvement on reasoning benchmarks like PhysBench.
- Explainable decisions through reasoning traces anchored in the KB.

## Deliverables

- **Software**: An open-source, scalable Knowledge Base framework (using Neo4j/GNNs) populated with >10,000 entities and relations from video, text, and simulation sources.
- **Software**: A VLA-KB integration architecture with a low-latency query interface (<10ms) and cross-modal fusion modules. This includes a Chain-of-Thought (CoT) reasoning system implemented on the OpenVLA model.
- **Data/API**: A unified API and dataset of 50,000+ labeled robotic task episodes, including multi-camera RGB recordings, CoT reasoning traces, and KB query logs.
- **IP/Publications**: Comprehensive benchmark results on PhysBench and ManipBench and 3-4 publications at top-tier robotics conferences (e.g., ICRA, CoRL, RSS).

## Proposed solution

We propose a neurosymbolic architecture that integrates the OpenVLA model with a structured Knowledge Base. This integration is achieved via a Graph Neural Network (GNN) encoder and cross-attention mechanisms and enables three core functionalities:

- **Property Lookup**: The VLA will query the KB to augment visual understanding with non-visual properties (e.g., object material, fragility, weight).
- **Constraint Retrieval**: The VLA will query the KB to validate actions against physical and safety constraints (e.g., max_force = 2N for a fragile object, or cut flat side first for an unstable vegetable).
- **Prior Knowledge Access**: The VLA will query the KB for similar, previously successful tasks to generalize and adapt to novel scenarios or ingredients.

The model will be trained in a 4-phase pipeline, including foundation, domain adaptation, KB-augmented joint training, and Chain-of-Thought (CoT) fine-tuning, further refined by RLHF.

## Proposed Tech. 1st Priority Tech.

**1st Priority Tech**: The foundational VLA-KB integration architecture, including the KB schema design and the VLA-KB query interface.

**PoC Plan (first 3 months)**: Yes. The Q1 (Months 1-3) plan is to establish this foundation. This includes:

- Setup and calibration of the Rainbow Robotics RBY-1 platform.
- Deployment of the baseline pre-trained OpenVLA model and validation.
- Initial design and S/W implementation of the KB schema (e.g., using OWL/RDF).

**Expected Product / Service**: The technology enables highly reliable, explainable robotic systems for complex manipulation.

**Industrial Scenario (Factory QC)**: An intelligent inspection robot. It queries a KB of IPC standards and defect patterns to identify and sort components (e.g., "cold_solder"), achieving high accuracy (86-89%) and providing explainable rejection reports.

**Service Scenario (Kitchen Assistant)**: A context-aware service robot. It queries a KB for recipe steps, tool specifications (e.g., chef_knife, 3N force), and physics-based safety rules (e.g., "cut flat base first") to safely and correctly prepare a meal.

## Resources

- **Duration**: 1 Year (12 Months)
- **Team**: 3 Members (Researchers)

### Hardware

- 1x Rainbow Robotics RBY-1 platform (dual 7-DOF arms, mobile base, 3x RGB cameras, F/T sensors)
- 1x Training Workstation with 4x NVIDIA A100 (40GB) or 8x V100 GPUs
- 1x SpaceMouse Pro for human interface

### Compute/Storage

- Total training budget: ~1,300 GPU-hours (A100-equivalent)
- Total storage: ~5TB (for 3TB processed dataset and 15TB raw demos)

## Plan for utilizing GRC's competency

### Correlation between GRC's competency and proposed technology

GRC's active projects and existing infrastructure directly map to the proposal's core technical requirements: Knowledge Base (KB) population and Vision-Language-Action (VLA) integration.

### KB Population (Primary Requirement)

The proposal's primary technical need is an automated pipeline to populate the KB. GRC's Advanced Research group has existing projects in 3D vision algorithms (scene understanding, hand/head tracking), which are also leveraged for XR applications. This established expertise provides the specific, necessary mechanism to parse video demonstrations and simulation logs to extract the entities, relations, and physical constraints required for the KB.

### VLA Integration (Balancing Component)

The proposal requires integrating this KB with a VLA. GRC has a parallel, active project to adapt the $\pi_0$ VLA for the Rainbow Robotics RBY-1 platform. This existing work on the proposal's target hardware and VLA model provides a validated baseline, allowing the project to focus on the KB-integration task rather than initial platform bring-up.

### Data & Algorithm Infrastructure

GRC's supporting infrastructure and algorithms are already in place:

- **Data Generation**: An active project utilizes Nvidia COSMOS to collect and diversify humanoid task demonstrations for both the RBY-1 and Unitree G1 platforms, directly supporting the proposal's 50,000+ episode data requirement.

- **Related Algorithms**: A separate GRC project focuses on Human-in-the-Loop Sample-Efficient Reinforcement Learning (HIL SERL) for complex manipulations (e.g., pick-and-place, cable assembly, screwing), providing complementary expertise.

- **Facilities**: In-house labs are equipped with Optitrack motion capture (submillimeter tracking) and multi-camera calibration systems, fulfilling the proposal's validation infrastructure needs.

### Reason why the GRC should carry out this project

GRC is positioned to execute this project due to the direct alignment of existing, funded work, all of which is in active collaboration with the Future Robotics Office (FRO).

### Project Synergy

This proposal unifies three separate, active FRO-aligned projects: 1) the $\pi_0$-RBY1 VLA adaptation, 2) the 3D vision/perception research, and 3) the COSMOS-based data generation pipeline. It bridges these efforts by adding the missing component: a symbolic KB reasoning layer.

### Risk Mitigation

The project risk is substantially mitigated. GRC has already solved the foundational hardware (RBY-1) and VLA-adaptation ($\pi_0$) challenges. This eliminates the initial 6-9 month setup and integration phase typical of new robotics projects, allowing this team to focus immediately on the core research objective: the KB-VLA integration.

### Commercialization Path

GRC is a center for commercialization. The established collaboration with FRO and existing projects in industrial-relevant tasks (HIL SERL for assembly) provide a defined path to translate this proposal's research from a baseline (Year 1) to the stated Year 3 goals of TRL 7 and industrial pilots.

