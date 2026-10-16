# Mission 7: Understand Why ML Systems Fail

**Research question:** Even if a model works during testing, why might it fail in reality?

## 1. Objective

To understand the main reasons an ML system can look good in testing but disappoint in real use, to analyse three hypothetical failures (likely cause, evidence that would confirm it, possible mitigation), and to explain why human oversight matters when predictions can be wrong.

All scenarios here are **hypothetical** and made up for learning. They are not reports of real events or real tools.

## 2. Main Ways ML Systems Fail

| Failure source | What it means | Simple example |
|---|---|---|
| **Poor-quality data** | Wrong, noisy or inconsistent values in the data | A sensor glitch records a delay of 9.5 ns instead of 0.95 ns |
| **Unrepresentative data** | Training data does not cover the situations the model will meet | A model trained only on small designs is used on large ones |
| **Label errors** | The "correct answers" in the data are sometimes wrong | A run that really failed timing is labelled PASS |
| **Missing values and noise** | Gaps or random variation in measurements | Power readings missing for a whole group of runs |
| **Data bias** | The data over- or under-represents some groups, so the model works better for some than others | Most training examples come from one design style |
| **Data leakage** | Information that would not be available in real use (or that gives away the answer) slips into training or testing | The same wafer appears in both the training and test sets |
| **Changing real-world data (drift)** | The real data changes over time, so the learned pattern gets out of date | A manufacturing process change shifts the measurements |
| **Over-trusting predictions** | People accept outputs without checking | An engineer skips a check because the model said "low risk" |

### Bias and subsets: why one overall score can hide a problem

A single overall number can look good while a subset does badly. A small made-up example:

| Group | Samples | Correct predictions | Accuracy |
|---|---:|---:|---:|
| Group A (common design type) | 800 | 784 | 98% |
| Group B (rare design type) | 200 | 116 | 58% |
| **Overall** | **1000** | **900** | **90%** |

The overall accuracy of 90% looks fine, but the model is little better than guessing for Group B. Checking performance **separately for each subset** reveals this.

### Data leakage: why it makes evaluation misleading

If information that gives away the answer is present during evaluation, the test score becomes unrealistically good, because the model is partly "cheating". The test then no longer shows how it will do on genuinely new data. Typical forms are: the same item appearing in both training and test sets, a feature that is only known *after* the outcome, or an ID or label-like field that correlates with the answer.

## 3. Three Hypothetical Failures

### Failure 1: Great in testing, poor on a new kind of design

**Scenario.** A timing pass/fail model scores 96% on its test set. When engineers use it on a new, larger design family, it keeps predicting PASS for runs that later fail.

| | |
|---|---|
| **Likely cause** | **Unrepresentative training data** and a shift between training data and the new designs. The training runs were mostly small, low-complexity designs, so the model never learned what failures look like for large ones. |
| **Evidence that would help confirm it** | (1) Measure accuracy **separately by design type or size**. If it is high for small designs and low for large ones, that points to this cause. (2) Compare the feature ranges (delay, power, complexity) of the training data with the new designs. If the new runs fall in areas with few or no training examples, that supports it. (3) Count how many training samples exist for the new design family. |
| **Possible mitigation** | Collect and label examples from the new design family and retrain; make sure the test set covers all design types, not just the common one; flag inputs that look unlike the training data for human review instead of trusting the prediction; document which design types the model was validated on. |

### Failure 2: Almost perfect test score, collapses in real use

**Scenario.** A model that classifies inspection images as "defect" or "no defect" gets 99% on its test set, but its accuracy drops sharply when it is used on images from new wafers.

| | |
|---|---|
| **Likely cause** | **Data leakage.** Suppose many images come from the same wafers, and the random split put images from the same wafer in both the training and test sets. The model can then recognise wafer-specific patterns instead of real defect patterns, so the test score is inflated. |
| **Evidence that would help confirm it** | (1) Check how the data was split: do the training and test sets share wafers or lots? (2) **Re-split by wafer** (all images of a wafer go into only one set) and re-evaluate. If the score drops a lot, leakage is the likely cause. (3) Look for features or fields that are suspiciously predictive, such as an ID, a timestamp or a field that is only filled in after inspection. |
| **Possible mitigation** | Split the data so related items stay together (for example by wafer or lot, or by time); remove features that would not exist at prediction time; re-run the evaluation on the clean split and report that result; keep a final test set that is only used once. |

### Failure 3: Worked well for months, then slowly got worse

**Scenario.** A model that estimates a block's power from early design features gave good estimates at first. Over several months its errors grow, although the model itself has not been changed.

| | |
|---|---|
| **Likely cause** | **Changing real-world data (drift).** For example, the design flow, a tool version or the process technology changed, so today's inputs and results no longer follow the patterns in the original training data. |
| **Evidence that would help confirm it** | (1) Track the model's error **over time** and see when it started rising. (2) Compare the distribution of today's inputs with the training inputs. (3) Check whether the rise lines up with a known change, such as a new tool version or a flow update. (4) Check whether re-training on recent data lowers the error. |
| **Possible mitigation** | Monitor error against real analysis results on a regular basis, with an alert level; retrain or update the model on recent data when it degrades; keep a fallback (the conventional analysis) and use the model only as a quick estimate; record the data period the model was trained on. |

### Summary of the three failures

| # | Failure | Likely cause | Key confirming evidence | Mitigation (short) |
|---|---|---|---|---|
| 1 | Good test, poor on new designs | Unrepresentative data / shift | Accuracy by design type; feature ranges | Add data, subset testing, flag unfamiliar inputs |
| 2 | Near-perfect test, poor in use | Data leakage | Re-split by wafer, score drops | Group-aware split, remove leaking features |
| 3 | Gradual decline over months | Data drift | Error over time, input distribution change | Monitoring, retraining, fallback |

## 4. Human Oversight and the Cost of Wrong Predictions

Predictions can be wrong, and the cost of being wrong depends on the use. For a model that suggests which tests to prioritise (illustrative):

| Wrong prediction | What could happen |
|---|---|
| Model says "low risk, skip" but a real problem exists (a miss) | A bug or failure could go unnoticed, which may be expensive later |
| Model says "high risk" but it is actually fine (a false alarm) | Engineer time is wasted checking it |

Because the two mistakes have different costs, engineers need to decide which matters more and measure it (Mission 6).

Human oversight means:
- treating the prediction as an **input to a decision**, not the decision itself;
- having an engineer review **high-impact** cases;
- keeping a **fallback** (conventional checks) that the model does not replace;
- **monitoring** results so a failing model is noticed;
- **recording** what data the model was built and tested on, and where it should not be used.

## 5. Connection to Semiconductor / Design Verification Work

In design verification, results come from tools and tests that engineers already trust. If an ML model is ever used to guide effort (for example, which tests to run first), the risks above apply directly: unrepresentative training designs, leaked information in the split, and drift when the flow or design style changes. Such a model should support, and not replace, the established checks. These are possible risks to investigate, not claims about specific existing tools.

## 6. What Is Still Unclear

- How to detect drift automatically in practice, and how often to retrain.
- How to choose the right split (random, by group or by time) for a given engineering dataset.
- How much bias is "acceptable" and how it is measured in a technical setting.

## 7. Conclusion

An ML system can fail even when it tests well: the data may not represent real use, labels may be wrong, information may leak into the evaluation, or the world may change after training. Each cause leaves different evidence (subset scores, a re-split result, error over time), which helps identify it. Because predictions can be wrong and mistakes have different costs, human oversight, monitoring and a fallback remain essential. A prediction is an output to assess, not automatically the truth.

## 8. Sources

Full list with the claims each one supports is in [`sources.md`](sources.md) (Mission 7 section).
