# Course Completion Roadmap

> **Status:** Operational syllabus  
> **Project:** Neural-Symbolic Robotic Task Planning  
> **Primary objective:** turn the enrolled courses into research-grade capabilities, mini-projects, and measurable evidence for the final robotic task-planning system.

---

## 1. How to use this roadmap

This is **not a watch-list**. A course is only considered useful when its concepts are converted into an implementation, experiment, evaluation, or documented research artifact.

The operating loop is:

```text
COURSE
  ↓
CONCEPTS
  ↓
TARGET CAPABILITY
  ↓
MINI-PROJECT
  ↓
TEST / METRICS
  ↓
DOCUMENTATION
  ↓
INTEGRATION INTO MAIN PROJECT
```

The roadmap deliberately prioritizes **research depth over course completion speed**. Existing knowledge should be reviewed rather than relearned, while project-critical topics should be studied deeply.

### Definition of done

For a course/topic to count as operationally complete:

- [ ] Core concepts are understood well enough to explain without the course.
- [ ] Relevant concepts have been implemented independently.
- [ ] The implementation is committed to GitHub.
- [ ] At least one measurable test/evaluation exists.
- [ ] Assumptions and limitations are documented.
- [ ] The resulting capability is connected to a mini-project or the final system.

---

# 2. Master learning sequence

| Phase | Capability | Main course cluster | Output |
|---|---|---|---|
| 0 | Research literacy | Git/GitHub + paper reading | MP0 Literature Matrix |
| 1 | Software + algorithms | Python + DSA | MP1 Symbolic Robot World + A* |
| 2 | Symbolic reasoning | AI Fundamentals + planning self-study | MP2 STRIPS-style Planner |
| 3 | Language grounding | NLTK + NLP + ML + scikit-learn | MP3 Natural Language → Task |
| 4 | Perception | Computer Vision + Deep Learning | MP4 Scene Graph / Visual Grounding |
| 5 | Embodied robotics | Robotics + ROS 2 + simulation | MP5 Planner → ROS 2 |
| 6 | Robustness | Planning + ML + experimentation | MP6 Failure-aware Replanning |
| 7 | Evidence | Data Analysis + SciPy + visualization + data engineering | MP7 Benchmark + MP8 Dashboard |
| 8 | Research integration | All previous phases | Final research system |
| 9 | Publication | Research methodology + technical writing | Paper + reproducibility package |

---

# 3. Phase 0 — Research foundation

## Objective

Learn how to work like a researcher before adding complexity to the system.

### Required capabilities

- Git branches, commits, issues and pull requests
- Reading papers efficiently
- Identifying baselines and evaluation metrics
- Separating an existing method from a genuine research contribution
- Reproducible experiment logging
- Maintaining a literature matrix

## Mini-project MP0 — Research Literature Matrix

Create a structured record of approximately **20–30 relevant papers** covering:

- neural-symbolic robotics
- robotic task planning
- LLM/LM-guided task planning
- semantic grounding
- classical symbolic planning
- uncertainty-aware planning
- failure-aware/replanning systems
- scene graphs for robotics

Each paper should record:

```text
Problem
Method
Representation
Planner
Learning component
Simulator / dataset
Baseline
Metrics
Main result
Limitation
Research gap
Potential relevance to this project
```

### Completion criteria

- [ ] 20+ relevant papers reviewed
- [ ] At least 5 strong baselines identified
- [ ] Recurring limitations grouped
- [ ] Candidate research gaps written as testable hypotheses
- [ ] References stored in a reproducible format

**GitHub issue:** `#0 Research framing / literature matrix`

---

# 4. Phase 1 — Python + Data Structures & Algorithms

This phase is the computational foundation. Do **not** spend excessive time on beginner syntax if it is already comfortable.

## Course: Python Programming Zero to Hero — Introduction to Python

**Priority:** CORE  
**Action:** Accelerate / review fundamentals, then implement.

### Study deeply

- functions and clean interfaces
- modules/packages
- object-oriented programming
- dataclasses
- exceptions
- file I/O
- virtual environments
- testing
- type hints
- basic software architecture

### Minimize

- repetitive syntax drills
- trivial calculator/to-do style exercises
- generic beginner projects

### Research output

A modular Python package for robot-world state representation, actions, planning utilities and experiment logging.

---

## Course: Python Programming Course Beginner — Introduction to Python & Features of Python

**Priority:** OPTIONAL  
**Action:** Review only.

Use this as a reference when a Python gap appears. Do not duplicate the main Python course.

---

## Course: Data Structures and Algorithms — What are algorithms and data structures?

**Priority:** CORE / DEEP STUDY

### Study deeply

- graphs
- trees
- queues and priority queues
- heaps
- hash maps/sets
- graph representations
- BFS
- DFS
- Dijkstra
- A*
- heuristics
- time/space complexity
- state-space search

### Research relevance

Robotic task planning can be represented as search over a state/action space. Understanding classical search is essential because it provides transparent and defensible baselines for any learned/neural planner.

## Mini-project MP1 — Symbolic Robot World + A* Planner

Build a small symbolic world containing objects, locations and robot actions.

Example state:

```text
Robot(at=lab)
Object(cup, at=table)
Object(tool, at=shelf)
Door(lab, corridor, open=True)
```

Actions should have:

```text
preconditions
 effects
 cost
```

Implement a search planner and compare at least two strategies where practical.

### Metrics

- plan success rate
- planning time
- nodes expanded
- plan length/cost
- failure cases

### Completion

- [ ] Independent A* implementation
- [ ] Valid state transition model
- [ ] Unit tests
- [ ] Benchmark with increasing problem complexity
- [ ] README with algorithm assumptions

**GitHub issues:** `#1 Foundations`, `#2 Planning Baseline`

---

# 5. Phase 2 — AI Fundamentals + Symbolic Planning

## Course: AI Fundamentals Course — Course Introduction

**Priority:** CORE

### Study deeply

- intelligent agents
- problem formulation
- state-space search
- knowledge representation
- logical reasoning
- planning
- decision making
- uncertainty concepts

The historical overview is lower priority than the reasoning and planning mechanisms.

## Required self-study: Classical task planning

The enrolled AI material should be supplemented with:

- STRIPS representation
- predicates
- preconditions
- effects
- goal states
- PDDL concepts
- partial-order planning concepts
- HTN concepts
- planning vs motion planning

This distinction is critical:

```text
Task planning:
"Pick up cup → place cup on table"

Motion planning:
"Move robot arm through collision-free joint trajectory"
```

The current research project focuses primarily on **task-level planning**, while the existing 6-DOF evolutionary trajectory-planning project is a separate motion-planning track.

## Mini-project MP2 — STRIPS-style Robot Task Planner

Extend MP1 from graph navigation to symbolic task planning.

Represent:

```text
Predicates
Actions
Preconditions
Effects
Goals
```

Example:

```text
Action: pick(cup)
Preconditions:
    robot_at(cup_location)
    hand_empty
Effects:
    holding(cup)
    not hand_empty
```

### Metrics

- valid-plan rate
- impossible-goal rejection
- plan length
- planning time
- state-space size

### Completion

- [ ] Formal state representation
- [ ] Action schema representation
- [ ] Goal checking
- [ ] Valid plan generation
- [ ] Invalid goal detection
- [ ] Benchmark scenarios

**GitHub issues:** `#3 Research Framing`, `#4 Symbolic Planner`

---

# 6. Phase 3 — NLP + Machine Learning + Semantic Grounding

This is where the project begins moving from a purely symbolic system toward the **neural-symbolic boundary**.

## Course: NLTK — Introduction to NLP & NLTK Ecosystem

**Priority:** CORE

### Study

- tokenization
- part-of-speech tagging
- named entities
- chunking
- parsing
- syntactic structure
- linguistic ambiguity

NLTK itself is a learning tool; do not assume it is necessarily the final production NLP stack.

---

## Course: Introduction to Machine Learning

**Priority:** CORE

### Study deeply

- supervised learning
- feature engineering
- train/validation/test splits
- overfitting
- classification
- evaluation metrics
- confidence scores
- error analysis
- probability/calibration concepts

The goal is not to build a huge model. The goal is to understand how a learned component can provide **uncertain semantic information** to a symbolic planner.

---

## Course: Scikit-Learn for Machine Learning — Introduction

**Priority:** CORE

Use it to establish lightweight, interpretable ML baselines.

### Focus

- preprocessing pipelines
- classifiers
- train/test evaluation
- confusion matrices
- precision/recall/F1
- cross-validation
- baseline comparison

Avoid turning this phase into a generic ML competition project.

## Mini-project MP3 — Natural Language → Robot Task Representation

Build a small dataset of natural-language robot commands.

Examples:

```text
"Take the red cup from the kitchen to the table."
"Move the toolbox next to the robot."
"Put the blue object on the shelf."
```

Convert commands into a structured representation:

```text
{
  "action": "move",
  "object": "toolbox",
  "source": "storage_area",
  "destination": "robot"
}
```

Then introduce ambiguity/confidence:

```text
candidate_1: confidence = 0.82
candidate_2: confidence = 0.14
```

### Research direction

The important question is not simply **"Can NLP parse a command?"**

It is:

> **How should uncertain semantic grounding interact with symbolic task planning?**

That question can become part of the eventual research contribution.

### Metrics

- exact-match accuracy
- action accuracy
- object/entity accuracy
- slot accuracy
- ambiguity detection
- confidence calibration

### Completion

- [ ] Dataset created and documented
- [ ] Rule-based baseline
- [ ] ML baseline
- [ ] Evaluation script
- [ ] Error analysis
- [ ] Confidence/ambiguity mechanism

**GitHub issue:** `#5 NLP Grounding`

---

# 7. Phase 4 — Computer Vision + Deep Learning

This phase is intentionally **secondary**. The project should not become an enormous computer-vision project before the symbolic planner works.

## Course: Computer Vision Project — Introduction

**Priority:** CORE

### Study

- image representation
- object detection concepts
- coordinate systems
- object localization
- scene representation
- spatial relationships

## Course: Deep Learning Fundamentals: Neural Networks — Introduction to Deep Learning

**Priority:** CORE

### Study

- neural-network fundamentals
- representation learning
- CNN concepts
- embeddings
- transfer learning
- inference/evaluation

Do not spend project time training large networks from scratch. The available Intel UHD integrated graphics make lightweight models and CPU-friendly experimentation the sensible default.

## Mini-project MP4 — Semantic Scene Extractor / Scene Graph

Convert a simple visual scene into symbolic facts.

Conceptually:

```text
Image
  ↓
Object detection / recognition
  ↓
Object representations
  ↓
Spatial relations
  ↓
Scene graph
  ↓
Symbolic world model
```

Example:

```text
(red_cup, on, table)
(robot, near, table)
(toolbox, left_of, robot)
```

### Metrics

- object recognition accuracy
- relation accuracy
- scene consistency
- inference time

### Completion

This mini-project is sufficient when it can produce a reliable small-scale symbolic scene representation. It does **not** need production-grade computer vision.

**GitHub issue:** `#6 Vision Grounding`

---

# 8. Phase 5 — Robotics + ROS 2

## Course: Robotics — Introduction to Robotics

**Priority:** CORE

### Study deeply

- robot architecture
- sensing and actuation
- coordinate frames
- robot state
- actions
- planning hierarchy
- mobile robotics concepts
- simulation

The focus should be on the interface between **planning and execution**.

## ROS 2 self-study

Because ROS 2 is central to the embodiment stage, maintain competence in:

- nodes
- topics
- services
- actions
- parameters
- launch files
- packages
- TF2
- simulation interfaces

The target environment is ROS 2 Humble on Ubuntu 22.04.

## Mini-project MP5 — Planner → ROS 2 Execution

Take a symbolic plan such as:

```text
navigate(kitchen)
pick(cup)
navigate(table)
place(cup, table)
```

and translate executable actions into ROS 2 interfaces.

The first implementation can use a simplified simulated robot and abstract actions. Do not introduce unnecessary manipulation complexity early.

### Metrics

- execution success rate
- action latency
- failed actions
- plan completion rate

### Completion

- [ ] Planner publishes/returns task plan
- [ ] ROS 2 execution layer consumes it
- [ ] Robot/simulator executes actions
- [ ] Execution logs are captured
- [ ] Failure scenarios exist

**GitHub issue:** `#9 ROS2 Integration`

---

# 9. Phase 6 — Failure-aware replanning

This phase begins turning the project from a simple demo into a more research-oriented system.

## Mini-project MP6 — Failure-Aware Replanning

Introduce execution failures deliberately.

Example:

```text
Plan:
A → B → C → D

A succeeds
B fails

World state updated
       ↓
Planner invoked again
       ↓
Alternative plan
```

Study the distinction between:

- perception uncertainty
- semantic uncertainty
- execution failure
- world-state inconsistency

### Potential research mechanism

A useful research direction is an explicit decision between:

```text
HIGH CONFIDENCE
      ↓
EXECUTE

LOW CONFIDENCE
      ↓
CLARIFY / RE-GROUND

EXECUTION FAILURE
      ↓
UPDATE STATE → REPLAN
```

### Metrics

- recovery success
- replanning time
- number of replans
- task completion after failure
- clarification cost

---

# 10. Phase 7 — Data Analysis, SciPy and Visualization

## Course: Data Analysis and Processing — Course Overview

**Priority:** CORE

### Study

- data cleaning
- exploratory analysis
- distributions
- metric aggregation
- error analysis
- experiment reproducibility

This is research infrastructure, not generic business analytics.

---

## Course: Python SciPy — Introduction

**Priority:** SUPPORTING

Use selectively for:

- numerical analysis
- statistics
- optimization utilities
- scientific computing

Do not study unrelated SciPy functionality just for course completion.

---

## Course: Data Visualization with Matplotlib — Introduction to Data Visualization

**Priority:** CORE

This should be treated as a research skill.

Focus on:

- comparison plots
- distributions
- error plots
- ablation plots
- scaling curves
- confidence intervals where appropriate

---

## Course: Introduction to Data Visualization: Python — Introduction to Data Visualization

**Priority:** SUPPORTING

Use it to reinforce Python-based visualization. Avoid repeating material once Matplotlib competence is established.

---

## Course: Data Visualization with Plotly Dash — Course Introduction

**Priority:** SUPPORTING

Use only enough to create an experiment dashboard.

## Mini-project MP7 — Robot Planning Benchmark

Build a reproducible benchmark generator varying:

- number of objects
- number of actions
- task length
- ambiguity
- world complexity
- execution failures
- semantic confidence

Compare baseline and proposed approaches.

### Core metrics

- task success rate
- planning time
- execution time
- plan length
- replanning frequency
- clarification frequency
- failure recovery rate
- generalization to unseen task configurations

---

## Mini-project MP8 — Research Experiment Dashboard

Create a dashboard that loads saved experiment data and displays:

- baseline vs proposed method
- task success
- planning time
- failure recovery
- ambiguity handling
- ablation results

The dashboard is a **research communication tool**, not the research contribution itself.

**GitHub issue:** `#8 Evaluation`

---

# 11. Phase 8 — Database and Data Engineering courses

## Course: Mastering Databases with Python — Introduction

**Priority:** SUPPORTING

Learn enough SQLite/SQL to store:

- task definitions
- experiment configurations
- run IDs
- metrics
- failure cases

## Course: Mastering MySQL — Relational DB Theory and Design Deep Dive

**Priority:** OPTIONAL / DEFER

Learn relational modeling and normalization only if the project needs a larger experiment registry. Advanced database administration is outside the core research scope.

## Course: Introduction to Data Engineering — Introduction to Course

**Priority:** SUPPORTING

Focus on:

- data pipelines
- validation
- structured datasets
- reproducibility
- experiment-data organization

Avoid enterprise cloud/data-platform depth unless required later.

---

# 12. Visualization / BI courses

## Course: Data Visualization Using Excel — Introduction to Excel Data Visualization

**Priority:** OPTIONAL

Useful for quick inspection of experiment tables. Not a core research dependency.

## Course: Microsoft Power BI — Introduction of Power BI

**Priority:** OPTIONAL / DEFER

## Course: Build Dashboards in Power BI — Concept Overview with AI

**Priority:** OPTIONAL / DEFER

These can improve presentation capability but should **not interrupt the robotics/research pipeline**.

The Python + Matplotlib + Plotly stack is more directly aligned with reproducible research workflows.

---

# 13. Conversational AI / Applied AI courses

## Course: Building a Chatbot Using Python — Introduction

**Priority:** SUPPORTING

Do not build a generic chatbot.

Use the material to understand:

- dialogue flow
- intent routing
- clarification questions
- conversational interfaces

Its relevant output is a **robot-task clarification interface**.

## Course: Certificate Program in Applied AI — Course Introduction

**Priority:** SUPPORTING / STRATEGIC

Use modules selectively when they directly support:

- semantic grounding
- ML pipelines
- AI system design
- evaluation

Avoid duplicating material already mastered through the core courses.

## Course: YUVA AI for ALL in Hindi — Introduction to AI & Machine Learning

**Priority:** OPTIONAL / REFERENCE

Use for conceptual revision only. It is not a core technical dependency.

---

# 14. Main project architecture

The final system should evolve toward:

```text
                  Human Instruction
                         │
                         ▼
              ┌────────────────────┐
              │ Semantic Grounding │
              │ NLP / learned     │
              │ representation    │
              └─────────┬──────────┘
                        │
                  candidates
                  + confidence
                        │
                        ▼
              ┌────────────────────┐
              │   Symbolic World   │
              │      Model         │
              └─────────┬──────────┘
                        │
              state + goal + facts
                        │
                        ▼
              ┌────────────────────┐
              │ Symbolic Planner   │
              │ STRIPS / search /  │
              │ selected baseline  │
              └─────────┬──────────┘
                        │
                     plan
                        │
                        ▼
              ┌────────────────────┐
              │ Constraint /       │
              │ Validity Checking  │
              └─────────┬──────────┘
                        │
                  valid / invalid
                    │          │
                    │          └──────► Clarify
                    ▼
              ┌────────────────────┐
              │    ROS 2           │
              │    Execution       │
              └─────────┬──────────┘
                        │
                    robot state
                        │
                        ▼
              ┌────────────────────┐
              │ Failure Detection  │
              └─────────┬──────────┘
                        │
                     failure
                        │
                        ▼
                     REPLAN
```

This architecture intentionally preserves a **symbolic, inspectable planning layer** rather than making the project simply "put an LLM in front of a robot."

---

# 15. Final research project

## Working title

**Uncertainty-Aware Neural-Symbolic Task Planning for Robotic Agents**

The exact title should remain provisional until the literature review establishes the strongest defensible research gap.

## Core components

| Component | Baseline | Potential research direction |
|---|---|---|
| Language grounding | Rule/ML parser | Uncertainty-aware semantic grounding |
| World model | Static symbolic state | Dynamically updated state |
| Task planner | A*/STRIPS/HTN baseline | Planning informed by learned uncertainty/constraints |
| Verification | Preconditions | Explicit constraint/failure reasoning |
| Ambiguity | Execute best guess | Clarify vs re-ground decision |
| Execution | Open-loop | Closed-loop ROS 2 execution |
| Failure | Stop | State update + replanning |
| Evaluation | Demo scenarios | Controlled benchmark + ablations |

---

# 16. Research evaluation strategy

A research claim should never be supported by a single successful demonstration.

The evaluation should eventually include:

### Baselines

At minimum, compare against appropriate simpler systems such as:

1. deterministic symbolic planner
2. symbolic planner + deterministic parser
3. learned grounding + symbolic planner
4. proposed uncertainty-aware / neural-symbolic method

The exact baseline set will be finalized after literature review.

### Ablations

Possible ablations:

- without confidence estimation
- without clarification
- without replanning
- without constraint verification
- different grounding models
- different planning strategies

### Evaluation dimensions

```text
Task Success
Planning Time
Execution Time
Plan Length
Failure Recovery
Replanning Frequency
Clarification Cost
Semantic Accuracy
Confidence Calibration
Generalization
```

The objective is to produce **numbers that support or falsify a hypothesis**, not merely numbers that make the project look impressive.

---

# 17. Course → GitHub issue mapping

| Issue | Purpose |
|---|---|
| #0 | Research framing + literature matrix |
| #1 | Python/software foundations |
| #2 | DSA + search baseline |
| #3 | AI/planning research framing |
| #4 | Symbolic planner |
| #5 | NLP/semantic grounding |
| #6 | Vision grounding |
| #7 | Benchmark/data pipeline |
| #8 | Evaluation/visualization |
| #9 | ROS 2 integration |
| #10 | Research integration |
| #11 | Failure-aware replanning |
| #12 | Publication/reproducibility package |

Issue numbers are a planning convention; update them if the repository already uses conflicting issue numbers.

---

# 18. Weekly operating cycle

A sustainable week should contain six blocks:

| Block | Activity | Expected output |
|---|---|---|
| 1 | Course learning | Concept notes + implementation |
| 2 | Research reading | 1–3 paper cards |
| 3 | Implementation | GitHub commit |
| 4 | Evaluation | At least one measurable result |
| 5 | Documentation | README / experiment note |
| 6 | Review | Next-week task list |

### Suggested allocation

```text
40%  Course + technical learning
30%  Project implementation
15%  Research papers
10%  Evaluation / experiments
 5%  Documentation / planning
```

During a research-experiment phase, shift more time toward implementation and evaluation.

---

# 19. What NOT to do

To preserve research scope:

- Do not build generic beginner projects merely for certificates.
- Do not start with an LLM before the symbolic baseline exists.
- Do not make computer vision the project unless it becomes scientifically necessary.
- Do not train huge models on limited hardware just to claim deep learning.
- Do not optimize the dashboard before the experiment is scientifically valid.
- Do not claim novelty before systematic literature review.
- Do not compare methods using only one hand-crafted scenario.
- Do not confuse a visually impressive robot demo with a research contribution.

---

# 20. Hardware / compute strategy

The development environment is designed around:

- Ubuntu 22.04 LTS
- ROS 2 Humble
- Intel UHD integrated graphics
- CPU-first experimentation

Therefore:

- prefer lightweight models
- use pretrained models where appropriate
- keep simulation environments computationally controlled
- design experiments that can run reproducibly without a dedicated GPU
- use cloud/GPU resources only if a later research experiment genuinely requires them

The research contribution should come from **system design, reasoning, grounding, uncertainty handling and rigorous evaluation**, not from brute-force compute.

---

# 21. Relationship to the 6-DOF evolutionary trajectory-planning project

The existing **6-DOF robotic-arm trajectory-planning project using evolutionary algorithms** should remain a separate project track.

It provides valuable complementary knowledge in:

- optimization
- search
- objective functions
- trajectory generation
- robotics kinematics
- evolutionary algorithms

However, it should not be unnecessarily merged into this project.

The distinction is:

```text
This project:
Natural language / semantic state
        ↓
Task planning
        ↓
Action sequence
        ↓
Robot execution

6-DOF project:
Goal pose
   ↓
Motion / trajectory planning
   ↓
Joint trajectory
   ↓
Robot motion
```

A future integrated architecture could connect the two, but that is **future scope**, not a prerequisite for the current research project.

---

# 22. Final completion gate

The project should not be considered research-ready until the following are true:

- [ ] Literature gap is supported by relevant papers.
- [ ] Classical baseline is implemented and measured.
- [ ] Neural/semantic grounding baseline is implemented and measured.
- [ ] Proposed mechanism is clearly isolated.
- [ ] ROS 2 execution is reproducible.
- [ ] Failure scenarios are systematically tested.
- [ ] Benchmark contains controlled variations.
- [ ] Ablation study exists.
- [ ] Results are statistically/research-methodologically defensible where appropriate.
- [ ] Limitations are explicitly documented.
- [ ] Experiments can be reproduced from the repository.
- [ ] Only then should the work be positioned as a potential paper contribution.

---

## Guiding principle

> **Learn only what the research system needs, build what you learn, measure what you build, and document what you discover.**

The end goal is not to finish 24 courses. The end goal is to emerge from those courses with a **credible research-grade robotic planning system and a defensible evidence trail for a future publication.**
