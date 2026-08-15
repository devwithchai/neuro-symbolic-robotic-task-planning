# Project Blueprint

## Working Title

**Uncertainty-Aware Neural-Symbolic Task Planning for Mobile Robots**

## 1. Problem Context

Natural-language robot instructions are semantically flexible but operationally underspecified. A robot needs more than language understanding: it must represent the world, reason about action preconditions/effects, satisfy constraints, detect ambiguity, and produce an executable sequence.

This project investigates a hybrid architecture in which learned semantic components provide flexibility while symbolic planning and verification provide explicit structure and constraints.

## 2. Working Research Problem

> How can uncertainty-aware semantic grounding be integrated with symbolic robotic task planning so that ambiguous or weakly grounded natural-language instructions are handled through clarification, verification, or replanning rather than silently producing invalid plans?

This is a **working research problem**, not a final novelty claim. It must be refined after literature review and baseline experiments.

## 3. Core Architecture

```text
Natural-language instruction
            │
            ▼
   Semantic grounding layer
            │
            ▼
 Candidate task representations
            │
            ▼
 Confidence / uncertainty estimation
            │
       ┌────┴────┐
       │         │
   confident   ambiguous
       │         │
       ▼         ▼
 Symbolic     Clarification /
 world model  alternative grounding
       │         │
       └────┬────┘
            ▼
      Symbolic planner
            │
            ▼
     Constraint checking
            │
       ┌────┴────┐
       │         │
     valid    invalid
       │         │
       ▼         ▼
    execute    replan
       │
       ▼
 ROS 2 action layer
       │
       ▼
 TurtleBot3 / Gazebo
```

## 4. Research Layers

### Layer A — Representation

Define a compact symbolic representation of:

- robot state
- objects
- locations
- relations
- capabilities
- action preconditions
- action effects
- task goals

### Layer B — Semantic Grounding

Convert natural-language instructions into candidate symbolic representations.

Initial implementations should use lightweight NLP/ML methods before considering LLM/VLM components.

### Layer C — Uncertainty

Represent uncertainty arising from:

- ambiguous object references
- ambiguous destinations
- incomplete instructions
- conflicting world-state information
- low-confidence semantic mappings

### Layer D — Symbolic Planning

Generate valid action sequences using established planning/search methods.

Potential baselines:

- BFS
- Dijkstra / uniform-cost search
- A*
- STRIPS-style planning
- PDDL-compatible planners
- HTN planning where justified

### Layer E — Verification and Recovery

Before execution, verify:

- action preconditions
- object availability
- robot capabilities
- goal consistency
- known environmental constraints

When a plan is invalid or grounding is uncertain, the system should clarify or replan rather than silently execute.

### Layer F — Robotic Execution

Expose validated task plans to ROS 2 and execute them in a lightweight simulated environment.

## 5. Baselines

The project should establish baselines before proposing improvements.

Potential baselines:

1. deterministic rule-based language grounding
2. deterministic semantic parser + symbolic planner
3. symbolic planner without uncertainty handling
4. learned grounding + symbolic planner
5. proposed uncertainty-aware architecture
6. optional LLM-assisted grounding + symbolic verification

The exact baseline set will be fixed after literature review.

## 6. Evaluation Dimensions

Primary metrics may include:

- task success rate
- valid-plan rate
- invalid-plan rate
- grounding accuracy
- clarification accuracy
- unnecessary clarification rate
- replanning rate
- planning time
- end-to-end latency
- execution failure rate
- generalization to unseen instruction templates

Where appropriate, report confidence intervals and statistical comparisons rather than only single aggregate scores.

## 7. Novelty Gate

A feature is not considered novel merely because it combines existing technologies.

A candidate contribution should demonstrate at least one of:

- a new algorithm or decision mechanism
- a meaningful adaptation with a measurable advantage over established baselines
- a new uncertainty/clarification formulation
- a new benchmark or dataset of an under-evaluated failure mode
- a new evaluation protocol that reveals a meaningful limitation
- a strong empirical finding about when a neural-symbolic architecture succeeds or fails

## 8. Scope Boundaries

Initially out of scope:

- training a large foundation model from scratch
- end-to-end vision-language-action control
- large-scale physical robot deployment
- replacing motion planning with the task planner
- claiming novelty from simple API integration

## 9. Research Evolution

```text
Symbolic baseline
      ↓
Language grounding baseline
      ↓
Uncertainty-aware grounding
      ↓
Verification + clarification
      ↓
ROS 2 / Gazebo validation
      ↓
Optional visual grounding
      ↓
Optional LLM/VLM extension
```

## 10. Expected Final Deliverables

- reproducible software implementation
- documented symbolic world representation
- benchmark/task suite
- baseline implementations
- proposed method
- quantitative evaluation
- ablation studies
- failure analysis
- ROS 2/Gazebo demonstration
- technical report / paper-style manuscript
- research documentation
