# ML Foundations Map (Lifecycle)

```mermaid
flowchart TB
    S1["1. Define the problem<br/>goal, constraints, success criteria"] --> S2["2. Understand the data<br/>samples, features, labels, quality"]
    S2 --> S3["3. Select an approach<br/>rule-based | supervised | unsupervised | reinforcement"]
    S3 --> S4["4. Prepare and train<br/>data preparation, model selection, training"]
    S4 --> S5["5. Evaluate<br/>validation, test data, metrics, generalisation"]
    S5 --> S6["6. Use the model<br/>INFERENCE: predictions for new inputs"]
    S6 --> S7["7. Monitor and improve<br/>failures, bias, changing data, human oversight"]
    S7 -. "return to earlier stages" .-> S1
    S5 -. "problem found" .-> S2

    T["TASK TYPES (what the model outputs)<br/>classification, regression, clustering,<br/>anomaly detection, dimensionality reduction, ranking"] -.-> S1
    P["LEARNING PARADIGMS (how it learns)<br/>supervised, unsupervised, reinforcement<br/>(self-supervised: related)"] -.-> S3

    F1["FAILURE 1: poor or unrepresentative data"] -.-> S2
    F2["FAILURE 2: data leakage makes evaluation misleading"] -.-> S5
    F3["FAILURE 3: drift after deployment"] -.-> S7

    SEMI["SEMICONDUCTOR APPLICATION: coverage-directed test selection (DV)<br/>supervised binary classification<br/>Limits: one design, pre-simulated data, research demonstration only"] -.-> S3
```

## How to read the map

- **Paradigms vs task types.** Task types describe what the model must output, so they are chosen when the problem is defined. Learning paradigms describe how it learns, so they are chosen when selecting the approach. They are different levels and must not be mixed up.
- **Where things happen.** Data preparation and training happen in stage 4, evaluation in stage 5, and inference in stage 6.
- **Three failure points.** (1) Poor or unrepresentative data enters at stage 2. (2) Data leakage makes the stage 5 evaluation look better than it is. (3) Drift appears after deployment, at stage 7.
- **Semiconductor application.** Coverage-directed test selection (Mission 9) is supervised binary classification. Its limits are that it was tested on one design, used pre-simulated data, and is a research demonstration, not a proven deployed tool.
- **Not a straight line.** Real projects loop back to earlier stages when evaluation or monitoring uncovers a problem.
