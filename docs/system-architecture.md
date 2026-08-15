# System Architecture

## Initial Research Architecture

```text
                         HUMAN
                           │
                           ▼
                Natural-language task
                           │
                           ▼
                 Semantic Grounding
                           │
              ┌────────────┴────────────┐
              │                         │
       candidate meanings         confidence
              │                         │
              └────────────┬────────────┘
                           ▼
                    World Model
                           │
                           ▼
                  Symbolic Planner
                           │
                           ▼
                 Constraint Verifier
                           │
              ┌────────────┴────────────┐
              │                         │
            valid                    invalid
              │                         │
              ▼                         ▼
           Execute                  Replan / clarify
              │
              ▼
            ROS 2
              │
              ▼
      Mobile robot / Gazebo
```

## Design Principle

The learned component should not be trusted as the final authority over robot execution. The symbolic layer provides explicit state/action structure and a verification boundary.

## Separation of Concerns

| Component | Responsibility |
|---|---|
| Grounder | Interpret language into candidate symbolic meanings |
| Uncertainty module | Estimate confidence/ambiguity |
| World model | Represent current symbolic state |
| Planner | Find an action sequence satisfying the goal |
| Verifier | Check action/state constraints |
| Recovery policy | Clarify or replan |
| ROS 2 adapter | Map validated tasks to executable robot actions |
| Simulator | Evaluate embodied execution |

## Future Extensions

The architecture is intentionally modular so that later experiments can replace the semantic grounding layer with:

- transformer-based encoders
- retrieval-assisted grounding
- LLM-based structured output
- vision-language models

without removing symbolic verification and evaluation infrastructure.
