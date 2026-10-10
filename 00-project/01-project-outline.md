---
name: Nevzat Kayıkçı
neptun: "JWM27Z"
id: "2026-SD-02"
github: "https://github.com/nevzatkay/project-work"
---
# Investigation of Emergent Behavioral Patterns in a Multi-Agent Simulation Based on Simple Rules

This project investigates how complex collective behavior can emerge from simple local interactions between autonomous agents. A two-dimensional simulation will be developed in which agents follow separation, alignment and cohesion rules without centralized control. By varying rule weights, population size, neighborhood radius and noise, the project will examine when collective movement, clustering or fragmented groups appear. Visual observations will be supported by quantitative measurements and repeated experiments with recorded random seeds. The intended outcome is a reproducible simulation and an analysis of how local rules influence global behavioral patterns.

## Objectives
- **Primary objective:** Build a configurable multi-agent simulation and investigate the relationship between simple local rules and emergent collective behavior.
- **Target users / stakeholders:** The student, thesis supervisor, examiners and researchers or students interested in agent-based modeling.
- **Research questions:**
  - How do separation, alignment and cohesion weights affect collective movement and group formation?
  - How do agent density, interaction radius and random noise influence the stability of these patterns?
  - Which patterns disappear or change when individual rules are disabled?
- **Measurable success criteria:**
  - A working simulation supports configurable populations, rule weights, interaction radius, duration and random seed.
  - Users can start, pause, resume, reset and inspect the simulation.
  - Each run exports its configuration and time-series metrics.
  - A baseline, three single-rule ablations and selected parameter sweeps are evaluated using at least 10 seeds per experimental condition.
  - Results include polarization, cluster statistics and nearest-neighbor distance, with variability across seeds.
  - Conclusions distinguish measured outcomes from visual impressions and do not require a particular pattern to appear.
- **Constraints:** A standard laptop; a two-dimensional bounded environment; simple local rules; no large language models or machine learning training; documented experiment settings and reproducible outputs.

## Scope
### In scope
- A continuous two-dimensional environment with periodic boundaries.
- Agents with position and velocity, observing only neighbors within an interaction radius.
- Separation, alignment, cohesion and optional random directional noise.
- Configurable parameters and real-time visualization.
- Simulation controls and configuration validation.
- Batch experiments, fixed seeds, metric calculation and CSV/JSON export.
- Baseline comparisons, rule ablations and parameter sweeps.
- Documentation of methods, findings and limitations.

### Out of scope
- Three-dimensional environments and physical robots.
- Human behavior prediction or validation against real animal populations.
- Reinforcement learning, neural networks or language-model agents.
- Distributed execution and large-scale cloud infrastructure.
- Claims that observed simulation patterns automatically generalize to real systems.

## Notes
The proposed initial implementation uses Python, NumPy, Matplotlib and a proposed Pygame visual interface. The first prototype will focus on flocking-style agents; other behavior models are optional extensions. This document describes planned work, not completed experiments. Project ID: 2026-SD-02. Neptun: JWM27Z. The repository is https://github.com/nevzatkay/project-work. The supervisor name has not yet been provided. The proposed flocking model and tools require confirmation against the assigned project brief and supervisor feedback; the title alone does not prescribe these choices.
