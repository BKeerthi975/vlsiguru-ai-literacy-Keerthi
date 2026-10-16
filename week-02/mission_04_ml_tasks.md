# Mission 4: Understand ML Task Types

**Research question:** What kinds of problems can machine learning solve?

## 1. Objective

To recognise the main ML *task types* (classification, regression, clustering, anomaly detection, dimensionality reduction and recommendation/ranking), to identify the likely input and output of each, and to explain why a task type is a different idea from a learning paradigm.

## 2. What Is a Task Type?

A task type describes **what the model is asked to produce**, meaning the kind of output. The learning paradigms from Mission 3 describe **how the model learns** (which training signal is used). So:

- *Task type* = "What is the question?" (predict a category, predict a number, find groups ...)
- *Learning paradigm* = "How does the model get its training signal?" (answers, no answers, rewards ...)

## 3. The Six Task Types

| Task type | What it does | Likely input | Expected output | Illustrative semiconductor example |
|---|---|---|---|---|
| **Classification** | Predicts a category | Features describing one sample | A class label (e.g. PASS / FAIL) | Predict whether a timing run passes |
| **Regression** | Predicts a number | Features describing one sample | A numerical value | Estimate delay or power of a block |
| **Clustering** | Groups similar observations | Many samples, usually without labels | A group (cluster) ID for each sample | Group design runs with similar characteristics |
| **Anomaly detection** | Flags unusual observations | Measurements or records | An "unusual or normal" flag, or a score | Identify an unusual measurement pattern |
| **Dimensionality reduction** | Represents data with fewer dimensions | Data with many features | The same data described by fewer features | Simplify many measurements so they can be explored or plotted |
| **Recommendation / ranking** | Orders or suggests candidates | A set of candidate items, plus context or history | An ordered list or scores | Rank configurations or tests for further investigation |

## 4. Six or More Real-World Problems Classified

Each row gives the task type, the input and the output. Rows 7 to 10 are semiconductor-related (illustrative ideas, not claims about existing tools).

| # | Problem | Task type | Input | Output |
|---|---|---|---|---|
| 1 | Filtering spam emails | Classification | Email text and sender details | Label: spam / not spam |
| 2 | Estimating the price of a house | Regression | Area, location, number of rooms | A price (number) |
| 3 | Grouping shop customers by buying behaviour | Clustering | Purchase history of many customers | A group ID for each customer |
| 4 | Spotting suspicious credit-card transactions | Anomaly detection | Transaction amount, time, place | A flag or score for how unusual it is |
| 5 | Suggesting films to watch | Recommendation / ranking | A user's watch history and a catalogue of films | A ranked list of films |
| 6 | Reducing hundreds of sensor readings to a few values for plotting | Dimensionality reduction | Many sensor readings per sample | A small number of combined features per sample |
| 7 | **Semiconductor:** predicting whether a timing run will pass | Classification | Delay, power, design type (as in the Mission 2 table) | PASS / FAIL |
| 8 | **Semiconductor:** estimating the power of a design before full analysis | Regression | Design parameters such as size and activity | Estimated power in mW (a number) |
| 9 | **Semiconductor:** flagging an unusual measurement pattern in test data | Anomaly detection | Measurement values from many units | A flag or score for unusual units |
| 10 | **Semiconductor:** ordering test cases or configurations to look at first | Recommendation / ranking | A list of candidate tests or configurations with their features | An ordered list, highest priority first |

## 5. Task Type Is Different from Learning Paradigm

A task type does **not**, by itself, tell you how a model was trained. The same task can often be approached with different paradigms, and the same paradigm can be used for different tasks.

| Task type | Paradigm it is **commonly** associated with | But it can also be... |
|---|---|---|
| Classification | Supervised (needs labelled examples) | The labels could be created some other way, e.g. derived from the data |
| Regression | Supervised (needs known numerical outcomes) | The target could also be derived from the data |
| Clustering | Unsupervised | Used as a step before other tasks |
| Anomaly detection | Often unsupervised (learn what "normal" looks like) | Supervised if examples of known anomalies are labelled |
| Dimensionality reduction | Usually unsupervised | Can be a preparation step for a supervised model |
| Recommendation / ranking | Often learned from past user or engineer choices (supervised-style) | Can also use feedback and rewards, which is closer to reinforcement learning |

The "commonly" and "often" matter: these are tendencies, not rules.

### Worked example: same data, two task types

Using the Mission 2 timing data:
- If the output is **PASS or FAIL**, the task is **classification**.
- If the output is **the actual delay in ns**, the task is **regression**.

Both are supervised here, but the *task type* changed because the *output* changed.

### Worked example: same task, different training signals

For anomaly detection on test measurements:
- With **no labels**, a model can learn what normal units look like and flag units that differ strongly (unsupervised).
- If engineers have **labelled** some units as known-bad, a model can learn from those labels (supervised).

The task (flagging unusual units) is the same, but the training signal is different.

## 6. Multiple Algorithms Can Address the Same Task

A task type is not tied to one algorithm. For example (names only, no detail needed this week):

| Task | Some algorithms that can be used |
|---|---|
| Classification | Logistic regression, decision trees, random forests, neural networks |
| Regression | Linear regression, decision trees, random forests, neural networks |
| Clustering | k-means, hierarchical clustering |
| Anomaly detection | Statistical thresholds, isolation-based methods, neural-network-based methods |
| Dimensionality reduction | Principal component analysis (PCA) and others |

Which one is best depends on the data, the problem and how the results will be evaluated. So choosing the *task type* comes first, and the algorithm is chosen afterwards.

## 7. Common Confusions I Want to Avoid

1. **"Classification is supervised learning" as a definition.** Classification is a task type. It is usually *done with* supervised learning, but the two names mean different things.
2. **Clustering vs classification.** Classification assigns samples to *known* categories using labelled examples. Clustering *discovers* groups without being told what they are.
3. **Anomaly detection vs classification.** Anomalies can be rare and may not be well defined in advance, so they are often handled differently from ordinary classes.
4. **Ranking vs classification.** Ranking cares about the *order* of items, not just which class each belongs to.

## 8. What Is Still Unclear

- How different algorithms for the same task actually differ in how they learn (later weeks and Mission 5).
- How to decide in practice which task framing is best when a problem could be set up in more than one way (e.g. regression vs classification with a threshold).
- How performance is measured for each task type (Mission 6).

## 9. Conclusion

Classification predicts categories, regression predicts numbers, clustering finds groups, anomaly detection flags unusual cases, dimensionality reduction describes data with fewer features, and recommendation/ranking orders candidates. These are classified by the *output* wanted, not by how the model was trained. The same task can be learned in different ways, and the same data can support different tasks, so a problem should be framed by its desired output first, and the method chosen after.

## 10. Sources

Sources for this mission will be added to [`sources.md`](sources.md).
