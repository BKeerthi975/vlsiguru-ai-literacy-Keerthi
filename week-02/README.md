# Week 02 - Machine Learning Foundations

VLSIGuru AI Literacy Layer - Week 02 assignment.

**Theme:** how machines learn from data. All nine research missions are written up below, with diagrams, synthetic worked examples and a semiconductor case study.

## Progress

| Item | Status |
|---|---|
| Mission 1: AI and ML landscape | Done |
| Mission 2: Data | Done |
| Mission 3: Learning approaches | Done |
| Mission 4: ML task types | Done |
| Mission 5: Anatomy of an ML model | Done |
| Mission 6: Evaluation and generalisation | Done |
| Mission 7: Why ML systems fail | Done |
| Mission 8: When to use ML | Done |
| Mission 9: Semiconductor case study | Done |
| ML Foundations lifecycle map (final synthesis) | Done |
| Reflection | Done |

## Missions at a glance

| Mission | File | Main deliverable |
|---|---|---|
| 1 | [`mission_01_ai_ml_landscape.md`](mission_01_ai_ml_landscape.md) | Concept map, five distinctions, three classified examples |
| 2 | [`mission_02_data.md`](mission_02_data.md) | 8-row synthetic dataset with features and target, two data-quality effects |
| 3 | [`mission_03_learning_approaches.md`](mission_03_learning_approaches.md) | Comparison table and a diagram for each learning approach |
| 4 | [`mission_04_ml_tasks.md`](mission_04_ml_tasks.md) | Ten problems classified by task type, including four semiconductor ones |
| 5 | [`mission_05_model_anatomy.md`](mission_05_model_anatomy.md) | Training-to-inference flow diagram and a linear regression explanation |
| 6 | [`mission_06_evaluation.md`](mission_06_evaluation.md) | Worked example of accuracy misleading on imbalanced classes |
| 7 | [`mission_07_failure_modes.md`](mission_07_failure_modes.md) | Three hypothetical failures with cause, evidence and mitigation |
| 8 | [`mission_08_when_to_use_ml.md`](mission_08_when_to_use_ml.md) | Rule-based vs ML comparison for the same problem |
| 9 | [`mission_09_semiconductor_case_study.md`](mission_09_semiconductor_case_study.md) | Case study on ML test selection in design verification |
**Final synthesis:** the full lifecycle is in [`ml_lifecycle_map.md`](ml_lifecycle_map.md), and my reflection is in [`reflection.md`](reflection.md).

## Files in this folder

| File | Description |
|---|---|
| [`ml_mental_map.png`](ml_mental_map.png) | Concept map of AI, ML, deep learning, generative AI and LLMs |
| [`learning_paradigms.png`](learning_paradigms.png) | Diagrams of the four learning processes |
| [`ml_model_flow.png`](ml_model_flow.png) | Flow from examples through training to a trained model and inference |
| [`linear_regression_idea.png`](linear_regression_idea.png) | Linear regression: guessed line vs fitted line |
| [`accuracy_vs_recall.png`](accuracy_vs_recall.png) | Accuracy vs recall on an imbalanced example |
| [`mission_02_dataset.csv`](mission_02_dataset.csv) | The synthetic dataset used in Mission 2 |
| [`sources.md`](sources.md) | Every source, what each supports, and a claim map for each mission |
| [`ml_lifecycle_map.md`](ml_lifecycle_map.md) | ML Foundations Map: 7-stage lifecycle with paradigms, task types, failures and a semiconductor application |
| [`ml_lifecycle_map.png`](ml_lifecycle_map.png) | Image export of the lifecycle map |
| [`reflection.md`](reflection.md) | Final reflection answers |

## Case study at a glance (Mission 9)

The case study looks at **coverage-directed test selection** in design verification: using supervised learning on coverage feedback to choose which simulation tests to run. It rests on a primary research paper from the University of Bristol and Infineon Technologies. The evidence supports it as a **research demonstration**, not a deployed tool, and the file separates what was measured from what the authors only projected.

## Notes on data, sources and AI use

- All datasets and numerical examples are **synthetic** and made up to illustrate concepts. They are not real chip-design data.
- All semiconductor ideas outside the Mission 9 case study are illustrative and make no claim that a tool already does this.
- Technical claims are mapped to sources in [`sources.md`](sources.md), which also lists the claims that are my own explanation and not tied to a checked source.
- AI tools were used as a learning aid, and technical claims were checked against the sources listed.


