# Evaluation Protocol

The project will be evaluated as a research system rather than a demonstration.

## Primary metrics

- grounding accuracy
- valid-plan rate
- task success rate
- invalid-plan rate
- clarification rate
- unnecessary clarification rate
- replanning rate
- planning latency
- end-to-end latency
- execution failure rate

## Experimental controls

Vary at least:

- instruction ambiguity
- number of candidate objects
- number of candidate destinations
- environment complexity
- language-template variation
- unseen object/location combinations
- state/action failures

## Reporting

Experiments should report raw results, aggregate metrics, failure categories, and where appropriate confidence intervals/statistical tests.

Ablation studies should isolate the contribution of each proposed component.
