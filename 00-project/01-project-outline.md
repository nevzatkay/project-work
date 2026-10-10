---
name: Nevzat Kayıkçı
neptun: JWM27Z
id: 2026-SD-02
github: https://github.com/nevzatkay/project-work
---
# Investigation of Emergent Behavioral Patterns in a Multi-Agent Simulation Based on Simple Rules

Repository: [project-work](https://github.com/nevzatkay/project-work) · [Project documentation](./)

Simple local interactions between agents can produce collective patterns that are difficult to predict from the individual rules alone. This project develops a configurable two-dimensional multi-agent simulation to investigate how rule combinations and parameter settings affect collective movement, clustering and group fragmentation without centralized control. The proposed initial model uses separation, alignment and cohesion, with optional directional noise. Visual observations will be supported by quantitative measurements and repeated runs with recorded random seeds, allowing the findings and their limitations to be compared reproducibly.

## Objectives

- **Primary objective:** Develop a working multi-agent simulation and investigate the relationship between simple local rules and emergent collective behavioral patterns.
- **Target users / stakeholders:** Researchers and students exploring agent-based modeling and emergence; the thesis supervisor and examiners reviewing the methods and findings.
- **Measurable success criteria:**
  - The user can configure the agent population, rule weights, interaction radius, noise level, run duration and random seed, and start, pause, resume and reset the simulation.
  - Each completed run saves its configuration and sampled measurements of polarization, cluster count, largest-cluster fraction and mean nearest-neighbor distance.
  - A baseline with all three rules enabled is compared with three conditions in which one rule is disabled at a time, using the same other settings and seed set.
  - Selected parameter sweeps are repeated across multiple recorded seeds, and results show variability rather than relying on a single visual example.
  - The same configuration and seed reproduce the run within a documented numerical tolerance in the same software environment; conclusions state the model assumptions and limitations.
- **Constraints:** A two-dimensional simulated environment; local interactions only; execution on a standard laptop; bounded project scope; explicit handling of numerical edge cases. The proposed model, experiment ranges and repetition counts will be finalized against the assigned brief and supervisor feedback.

## Scope

### In scope

- A two-dimensional environment with periodic boundaries and agents represented by positions and velocities.
- Simple local movement rules, initially separation, alignment and cohesion, with optional directional noise.
- Configurable simulation settings, real-time visualization and basic run controls.
- Quantitative measurements of directional agreement, group formation and local spacing.
- Seeded batch experiments, baseline comparisons, individual rule ablations and selected parameter sweeps.
- Configuration and time-series export in JSON/CSV, with documented settings and reproducibility checks.
- Analysis and documentation of observed patterns, variability and model limitations.

### Out of scope

- Camera-based tracking, real-animal observation and biological validation.
- Three-dimensional environments, physical robots and physical control systems.
- Reinforcement learning, neural networks and language-model agents.
- Distributed execution and large-scale cloud infrastructure.
- Direct prediction of real human or animal behavior from simulation outcomes.
