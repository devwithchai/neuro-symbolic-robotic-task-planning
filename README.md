# Neural-Symbolic Robotic Task Planning

> **Research project:** Uncertainty-aware neural-symbolic task planning for mobile robots.

This repository investigates how a robot can transform natural-language instructions into **structured, verifiable, and executable task plans** by combining learned semantic grounding with symbolic reasoning and ROS 2-based robotic execution.

The project is intentionally designed as a **research track**, not a tutorial implementation of an LLM controlling a robot.

## Research Direction

The working direction is:

> **Uncertainty-Aware Neural-Symbolic Task Planning for Mobile Robots**

The core idea is to combine:

```text
Human instruction
       ↓
Semantic / neural grounding
       ↓
Structured task representation
       ↓
Symbolic world model
       ↓
Task planning / search
       ↓
Constraint verification
       ↓
Execute / clarify / replan
       ↓
ROS 2 + robot simulation
```

The exact research question and novelty claim will be finalized only after a systematic literature review and baseline implementation.

## Why this project?

The project sits at the intersection of several areas in Robotics & Automation Engineering:

- Natural Language Processing
- Machine Learning
- Artificial Intelligence
- Data Structures & Algorithms
- Computer Vision
- Deep Learning
- Knowledge Representation
- Automated Planning
- Robot Operating System (ROS 2)
- Robot simulation

It also provides a longer-term path toward **LLM/VLM-guided robotics**, while keeping the first research system computationally realistic for an 8 GB CPU-only development machine.

## Research Principles

This project follows a few strict principles:

1. **No "GPT API + robot" demo as the research contribution.**
2. **Established algorithms will be treated as baselines, not claimed as novel.**
3. Novelty must be supported by literature review, experiments, ablations, and measurable improvement.
4. Simulation-first development is preferred; physical hardware is optional.
5. Every major design decision should have an experimental or literature-based justification.
6. The project should remain reproducible on modest hardware wherever possible.

## Initial Scope

### Target platform

- Ubuntu 22.04 LTS
- ROS 2 Humble
- Gazebo-compatible mobile robot simulation
- TurtleBot3-class robot as the initial target
- Python-based research components

### Initial computational strategy

The first system will avoid requiring local large language models or large vision-language models. Lightweight NLP/ML components, symbolic planning, graph search, and simulation will form the core experimental stack.

LLM/VLM components can later be introduced as an **optional research extension** once the symbolic baseline and evaluation protocol are stable.

## Repository Structure

```text
neuro-symbolic-robotic-task-planning/
│
├── README.md
│
├── docs/
│   ├── project-blueprint.md
│   ├── research-question.md
│   ├── system-architecture.md
│   ├── prerequisites.md
│   ├── datasets-and-simulators.md
│   ├── evaluation-protocol.md
│   └── literature-review.md
│
├── learning/
│   ├── course-roadmap.md
│   ├── prerequisite-roadmap.md
│   └── mini-projects.md
│
├── experiments/
│   └── README.md
│
├── simulation/
│   └── README.md
│
├── src/
│   └── README.md
│
├── data/
│   └── README.md
│
├── results/
│   └── README.md
│
├── notebooks/
│   └── README.md
│
└── references/
    └── README.md
```

## Development Philosophy

The project will progress through increasing levels of embodiment:

```text
Level 0 — Abstract symbolic world
        ↓
Level 1 — Language → symbolic task representation
        ↓
Level 2 — Planner + uncertainty / clarification
        ↓
Level 3 — ROS 2 integration
        ↓
Level 4 — Gazebo execution
        ↓
Level 5 — Optional vision grounding
        ↓
Level 6 — Optional LLM/VLM extension
```

This keeps the research question separable from simulator complexity and allows thousands of lightweight planning experiments before expensive robotic validation.

## Status

**Phase:** Research framing and prerequisite planning.

No novelty claim has been finalized yet.

## Author

**Chaitanya** — Undergraduate Student, Robotics & Automation Engineering

GitHub: [@devwithchai](https://github.com/devwithchai)
