# Research Question

## Working Research Question

> **How can uncertainty-aware semantic grounding be integrated with symbolic robotic task planning so that ambiguous natural-language instructions are handled through clarification, verification, or replanning rather than silently producing invalid plans?**

## Supporting Questions

1. Which forms of ambiguity most frequently cause failures in language-to-task grounding?
2. Can a lightweight confidence model identify cases where deterministic grounding is unsafe?
3. Does symbolic verification reduce invalid task plans produced by learned semantic components?
4. When should a robot ask for clarification versus selecting the highest-confidence interpretation?
5. What is the trade-off between task success, planning latency, and clarification frequency?
6. How well does the approach generalize to unseen instruction templates and object/location combinations?

## Hypothesis Template

> Compared with deterministic language grounding followed by symbolic planning, an uncertainty-aware grounding and verification mechanism will reduce invalid plans and increase task success on ambiguous instructions while keeping clarification overhead within an acceptable range.

The numerical hypothesis and statistical test plan will be finalized after baseline construction.

## Research Gap Policy

Do not state that a gap exists solely because a paper does not solve it. A defensible gap requires:

- evidence from multiple relevant papers/benchmarks;
- a clearly bounded failure mode;
- a measurable baseline;
- a feasible intervention;
- an evaluation protocol that can distinguish the proposed method from existing methods.
