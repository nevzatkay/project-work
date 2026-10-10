---
name: Nevzat Kayıkçı
neptun: JWM27Z
id: 2026-SD-02
github: https://github.com/nevzatkay/project-work
---
# Investigation of Emergent Behavioral Patterns in a Multi-Agent Simulation Based on Simple Rules

This project develops a configurable two-dimensional multi-agent simulation to investigate how collective behavioral patterns emerge from simple local interactions without centralized control. The proposed initial model uses separation, alignment and cohesion rules. By varying rule weights, agent density, interaction radius and random noise, the study will examine collective movement, clustering and group fragmentation. Repeated runs with recorded random seeds and quantitative measurements will support reproducible comparisons of rule combinations and parameter settings.

## Objectives
- **Primary objective:** Build a multi-agent simulation and investigate how simple local rules influence emergent collective behavior.
- **Target users / stakeholders:** Researchers and students studying agent-based modeling and emergence; the thesis supervisor and examiners.
- **Measurable success criteria:** The application supports configurable rules and simulation parameters, visualizes agent movement, saves run configurations and metric time series, and reports comparisons of a baseline, individual rule ablations and selected parameter settings across repeated seeded runs. Measurements include polarization, cluster statistics and nearest-neighbor distance, with variability and limitations reported.
- **Constraints:** A two-dimensional simulated environment; local interactions; execution on a standard laptop; reproducible random initialization; explicit model assumptions and numerical edge-case handling. The initial model and detailed experimental settings remain subject to the assigned brief and supervisor agreement.

## Scope

### In scope
- A two-dimensional environment with periodic boundaries and agents with positions and velocities.
- Simple local movement rules, initially separation, alignment and cohesion, with optional directional noise.
- Configurable population, rule weights, interaction radius, run duration and random seed.
- Real-time visualization and start, pause, resume and reset controls.
- Recorded configurations and time-series measurements, with CSV/JSON export.
- Repeated seeded experiments, baseline comparisons, individual rule ablations and selected parameter sweeps.
- Quantitative analysis of collective movement, clustering and fragmentation, including variability and model limitations.

### Out of scope
- Real-animal tracking, camera-based observation and biological validation.
- Three-dimensional environments, physical robots and physical control systems.
- Reinforcement learning, neural networks and language-model agents.
- Distributed or large-scale cloud execution.
- Claims that simulation outcomes directly predict real human or animal behavior.
