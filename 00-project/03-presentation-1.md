---
project_outline: "[[00-project/01-project-outline]]"
---

<!-- 5xl -->
# Emergent Behavior in a Multi-Agent Simulation

Investigation of Emergent Behavioral Patterns in a Multi-Agent Simulation Based on Simple Rules

Author: Nevzat Kayıkçı  
Neptun: JWM27Z  
Supervisor: Sari David  
Project ID: 2026-SD-02  

---

## Problem

- Agents can follow simple rules using only nearby information.
- Local interactions may produce **collective movement, clustering or fragmentation**.
- Global behavior is difficult to predict from the individual rules alone.
- A visually interesting run does not explain which rules caused the pattern.

**How do simple local rules influence collective behavior?**

---

## Problem: why comparison matters

- Different initial states may produce different outcomes.
- Changing several parameters together makes effects difficult to interpret.
- A single animation gives limited evidence.
- Measurements and repeated runs are needed for a meaningful comparison.

**Observe the pattern, measure it, then compare controlled conditions.**

---

## Proposed idea

A configurable **two-dimensional multi-agent simulation**:

- **Separation:** steer away from nearby agents.
- **Alignment:** adjust movement toward neighboring velocities.
- **Cohesion:** steer toward the local group.
- Optional **directional noise** introduces random variation.
- Agents use local information without centralized movement control.

These rules form the proposed initial model, subject to the assigned brief and supervisor feedback.

---

## Main goal: compare rules and parameters

| Condition | What it investigates |
| --- | --- |
| **All three rules enabled** | Baseline collective behavior |
| **One rule disabled at a time** | Contribution of each rule |
| **Selected parameter sweeps** | Effects of noise, interaction radius or density |

Use shared seeds and keep non-tested settings fixed across comparisons.

---

## Target users

| Role | Needs | Interaction |
| --- | --- | --- |
| **Researcher / user** | Explore how local rules affect collective patterns | Configure, observe, compare and export |
| **Students studying emergence** | Understand local interactions and group behavior | Inspect movement and measurements |
| **Supervisor / examiner** | Assess methods and supported conclusions | Review configurations, results and limitations |

Simulated agents are model entities, not application users or language-model agents.

---

## Planned scope

**In scope**

- Two-dimensional agents, local rules and periodic boundaries.
- Configurable settings, visualization and run controls.
- Quantitative metrics and JSON/CSV export.
- Repeated seeded runs, rule comparisons and selected parameter sweeps.

**Out of scope**

- Camera-based tracking and real-animal observation.
- Three-dimensional environments and physical robots.
- Learning algorithms, language-model agents and cloud-scale execution.
- Direct prediction of real human or animal behavior.

---

## User journey 1: configure a simulation

1. User selects population, rule weights, interaction radius and noise.
2. User sets run duration and a random seed.
3. The system validates the configuration.
4. Invalid settings produce field-specific errors.
5. Valid settings create the initial state at **step zero**.

**Result:** a configured and reproducible starting point.

---

## User journey 2: observe and control a run

1. User starts the simulation.
2. Agents move according to their local rules.
3. The interface shows movement, simulation time and sampled metrics.
4. User pauses and resumes from the same state.
5. User can reset to the seeded initial state.

**Result:** an interactive view of collective behavior.

---

## User journey 3: investigate a rule

1. User runs the baseline with all three rules enabled.
2. User defines a condition with **alignment disabled**.
3. Other settings, duration and sampling remain the same.
4. Both conditions run with the **same seed set**.
5. User compares metrics and variability across runs.

**Result:** evidence about alignment's contribution, even if the difference is small.

---

## User journey 4: compare and reproduce results

1. User selects values for one parameter and a seed set.
2. The system validates and executes a batch.
3. Completed and failed runs remain distinguishable.
4. User exports configurations and metric time series.
5. User reloads a configuration to reproduce a selected run.

**Result:** traceable comparisons supported by saved data.

---

## What will be measured?

| Metric | What it describes |
| --- | --- |
| **Polarization** | Directional agreement |
| **Cluster count** | Number of connected groups |
| **Largest-cluster fraction** | Share of agents in the largest group |
| **Mean nearest-neighbor distance** | Local spacing |

Use a declared, fixed cluster threshold across compared conditions.

Combine metrics with visualization and report variability and limitations.

---

## Expected deliverable and success

- A working application with configuration and run controls.
- Saved settings, seeds and measurements for completed runs.
- A baseline and three single-rule ablation conditions.
- Selected parameter sweeps repeated across recorded seeds.
- Reproduction within documented tolerance in the same environment.

Success means a supported analysis; a particular emergent pattern is not guaranteed.

---

## Next steps

- Confirm the assigned brief, supervisor and proposed MVP.
- Review background literature on emergence and agent-based modeling.
- Refine use cases, measurement definitions and experiment settings.
- Prepare the technical proposal and **Presentation 2**.
- Begin implementation in **Semester 2**.

[Project outline](01-project-outline.md) · [Specification](02-specification.md) · [Repository](https://github.com/nevzatkay/project-work)

