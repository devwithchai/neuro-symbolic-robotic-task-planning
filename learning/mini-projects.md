# Research-Aligned Mini-Projects

These mini-projects are capability-building experiments. They should be small enough to finish, but each must produce an artifact that can later be reused in the main research project.

## M01 — Symbolic Robot World

**Goal:** Represent a robot, objects, locations, and relations as structured state.

**Skills:** Python, data structures, classes, graphs.

**Deliverable:** State representation + transition engine.

**Feeds into:** symbolic world model.

---

## M02 — Robot State-Space Search

**Goal:** Implement BFS, Dijkstra/UCS, and A* over a toy robot world.

**Skills:** algorithms, graphs, heuristics.

**Deliverable:** planner with metrics for path cost and search effort.

**Feeds into:** symbolic task planner baseline.

---

## M03 — Action Preconditions and Effects

**Goal:** Implement STRIPS-like actions with explicit preconditions and effects.

Example:

```text
PICK(robot, object)
Preconditions:
  near(robot, object)
  gripper_empty(robot)
Effects:
  holding(robot, object)
  not gripper_empty(robot)
```

**Deliverable:** symbolic action library + state transition system.

**Feeds into:** planning domain.

---

## M04 — Natural Language → Task Representation

**Goal:** Convert constrained natural-language instructions into structured task representations.

**Example:**

```text
"Take the red cup to the kitchen."

→

transport(
    object=red_cup,
    destination=kitchen
)
```

**Skills:** NLP, parsing, entity extraction.

**Feeds into:** semantic grounding baseline.

---

## M05 — Ambiguity Detector

**Goal:** Detect ambiguous references in instructions.

Example:

```text
"Put the bottle on the table."

Bottle candidates: red, blue
Table candidates: A, B

→ ambiguous
```

**Deliverable:** ambiguity detector + benchmark cases.

**Feeds into:** uncertainty-aware grounding.

---

## M06 — Grounding Confidence Model

**Goal:** Predict confidence for candidate interpretations.

Compare at least one simple baseline such as:

- rule-based score
- TF-IDF + classifier
- embedding similarity

**Deliverable:** confidence estimator + calibration/error analysis.

**Feeds into:** clarification policy.

---

## M07 — Clarification Policy

**Goal:** Decide when the robot should execute, choose an interpretation, or ask a human.

Possible policy:

```text
high confidence → execute
medium confidence → verify / seek context
low confidence → clarify
```

**Deliverable:** policy + controlled experiment measuring task success vs clarification overhead.

**Feeds into:** proposed research mechanism.

---

## M08 — Constraint-Aware Planner

**Goal:** Reject plans that violate symbolic constraints even if the language grounding is plausible.

**Deliverable:** verifier + invalid-plan test suite.

**Feeds into:** safety/reliability layer.

---

## M09 — Replanning Under Failure

**Goal:** Introduce state changes or failed actions and recover without restarting from scratch.

**Deliverable:** replanning benchmark + recovery metrics.

**Feeds into:** robust execution.

---

## M10 — ROS 2 Task Executor

**Goal:** Translate a validated symbolic task plan into ROS 2 actions for a simulated mobile robot.

**Deliverable:** ROS 2 package + Gazebo demonstration.

**Feeds into:** embodied validation.

---

## M11 — Experimental Benchmark

**Goal:** Build a controlled task suite varying:

- instruction ambiguity
- object count
- distractors
- environment constraints
- unseen language templates
- failure events

**Deliverable:** versioned benchmark + evaluation scripts.

**Feeds into:** research experiments.

---

## M12 — LLM/VLM Extension (Optional)

Only after the non-LLM baseline is strong.

**Goal:** Compare an LLM/VLM semantic grounding component against lightweight baselines while keeping symbolic verification in the loop.

**Deliverable:** controlled comparison, not an API demo.

**Feeds into:** future research direction.

## Quality Gate

A mini-project is complete only when it has:

- reproducible code;
- a short technical note;
- tests or evaluation;
- documented limitations;
- a clear interface to the next project stage.
