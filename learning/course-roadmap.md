# Course Completion Roadmap

This roadmap is deliberately **project-driven**. Each course should produce a capability that feeds the research system rather than ending in disconnected beginner projects.

## Course → Research Capability Map

| Course / Skill | Research capability | Planned mini-project |
|---|---|---|
| Python | Modular research software | Robot-world simulation toolkit |
| Data Structures & Algorithms | State-space search and planning | Symbolic robot planner |
| AI Fundamentals | Agents, search, knowledge representation | Goal-directed planning environment |
| Machine Learning | Classification, confidence, model evaluation | Grounding confidence estimator |
| scikit-learn | Lightweight ML baselines | Intent/entity grounding baseline |
| SciPy | Numerical methods and optimization utilities | Planning/metric analysis toolkit |
| NLP / NLTK | Language preprocessing and semantic parsing | Natural-language task parser |
| Deep Learning | Learned representations | Optional learned grounding experiment |
| Computer Vision | Perception and visual grounding | Optional object/scene-state extractor |
| Robotics | Robot state, actions, execution | ROS 2 task execution interface |
| Data Analysis | Experimental methodology | Benchmark/evaluation pipeline |
| Matplotlib / Plotly / Dash | Research visualization | Interactive experiment dashboard |
| MySQL / Databases | Structured experiment/task storage | Task and experiment registry |
| Data Engineering | Reproducible data pipelines | Benchmark generation pipeline |
| Python Chatbot / Applied AI | Conversational interaction | Clarification interface prototype |

## Recommended Learning Order

### Phase 1 — Computational Foundation

- Python
- Data structures
- algorithms
- testing
- Git/GitHub workflow

**Output:** reusable state-space and experiment utilities.

### Phase 2 — Classical AI and Planning

Self-study alongside AI coursework:

- state-space representation
- search
- heuristics
- STRIPS
- PDDL
- HTN concepts
- knowledge representation

**Output:** first symbolic robot planner.

### Phase 3 — NLP Grounding

Study:

- tokenization
- named entities
- intent classification
- semantic representations
- ambiguity

**Output:** natural language → structured task representation.

### Phase 4 — Machine Learning

Study:

- supervised learning
- probability/confidence
- train/validation/test methodology
- calibration
- error analysis

**Output:** grounding confidence/ambiguity baseline.

### Phase 5 — Robotics + ROS 2

Connect the planner to:

- ROS 2 nodes
- actions/services
- robot state
- navigation/task execution
- Gazebo

**Output:** validated symbolic plans executed by a simulated mobile robot.

### Phase 6 — Computer Vision / Deep Learning

Only after the symbolic system is stable:

- object recognition
- scene representation
- visual grounding
- learned embeddings

**Output:** optional visual world-state input.

### Phase 7 — Research Extension

Investigate:

- uncertainty-aware grounding
- clarification policy
- constraint verification
- replanning
- optional LLM/VLM grounding

**Output:** candidate research contribution + evaluation.

## Completion Principle

Do not rush to the final project because a course is finished. A course is considered operationally completed for this project when its concepts have been used to build, test, or evaluate a component that can survive integration into the research stack.
