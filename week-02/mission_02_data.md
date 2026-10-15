# Mission 2: Understand Data - What Does an ML System Learn From?

**Research question:** What does it mean to learn a pattern from data?

## 1. Introduction

An ML model has no built-in knowledge of the problem. Everything it learns comes from the examples it is given, so the type, quality and representativeness of the data limit how good the model can become. In VLSI, one idea is to use historical measurements from earlier design runs to predict whether a new run will pass or fail timing.

All data in this file is **synthetic**, made up to illustrate the concepts. It is not from a real chip-design project. The same table is available as [`mission_02_dataset.csv`](mission_02_dataset.csv).

## 2. Key Terms

| Term | Meaning | In the timing example |
|---|---|---|
| **Dataset** | The whole collection of examples used for analysis or training | The full table of design runs |
| **Sample** | One example in the dataset | One design run |
| **Observation** | The recorded information about one sample (one row in a table) | R1: 0.80 ns, 12.5 mW, Low complexity, PASS |
| **Feature** | An input value the model uses to make a prediction | Delay, power, design type |
| **Label** | The known correct answer attached to a sample in the data | PASS or FAIL for that run |
| **Target** | The quantity the model is trained to predict | The timing result |

**Label vs target.** They usually refer to the same column in supervised learning, but from different angles. The *label* is the known answer stored with each sample. The *target* is what the model is being asked to predict. In unlabelled data there is no label column, so there is no supervised target.

## 3. Types of Data

**Structured vs unstructured**
- *Structured data* fits a fixed table of rows and columns. Example: timing reports with delay, power and status columns.
- *Unstructured data* has no fixed table shape. Examples: images (such as wafer or layout images), free-text bug reports, raw simulation logs. It usually needs extra processing before a model can use it.

**Numerical vs categorical features**
- *Numerical features* are measurable numbers. Examples: delay (ns), power (mW), cell area.
- *Categorical features* are groups or names. Examples: process corner, operating mode, design type.
- Some categorical features have a natural order (called *ordinal*). "Low, Medium, High complexity" is ordinal, whereas process corner names are not.

## 4. Labelled vs Unlabelled Data

- **Labelled data** has inputs plus the known outcome. Example: measurements with the final PASS/FAIL. It can train a *supervised* model.
- **Unlabelled data** has inputs only. Example: measurements from many runs where nobody recorded the outcome. It may be used to find groups or unusual cases with *unsupervised* methods.

Getting labels often takes extra effort (running full analysis, or an engineer reviewing results), which is one reason labelled data can be scarce.

## 5. Illustrative Dataset (8 rows, synthetic)

| Run | Delay (ns) | Power (mW) | Design type | Timing result |
|---|---:|---:|---|---|
| R1 | 0.80 | 12.5 | Low complexity | PASS |
| R2 | 1.20 | 14.0 | Medium complexity | FAIL |
| R3 | 0.95 | 13.2 | Low complexity | PASS |
| R4 | 1.35 | 15.1 | High complexity | FAIL |
| R5 | 0.75 | 11.8 | Medium complexity | PASS |
| R6 | 1.10 | 14.5 | High complexity | FAIL |
| R7 | 0.90 | 12.9 | Medium complexity | PASS |
| R8 | 1.25 | 14.8 | High complexity | FAIL |

**Identifying the parts**

| Component | Answer |
|---|---|
| Dataset | The table of 8 design runs |
| Sample / observation | Each row (R1 to R8) |
| Features | Delay, power, design type |
| Numerical features | Delay (ns), power (mW) |
| Categorical feature | Design type (ordinal: Low < Medium < High) |
| Label / target | Timing result (PASS or FAIL) |
| Labelled? | Yes, all 8 rows have a known result |

**Task this could support:** given delay, power and design type for a *new* run, predict PASS or FAIL. That would be supervised learning, specifically classification.

**Honest limitation:** this is a toy table. Here FAIL happens to line up with higher delay, which makes the pattern look easy. Eight rows are nowhere near enough to trust a model, and real data is rarely this clean.

## 6. Data Collection and Cleaning

**Collection.** Data should come from sources relevant to the problem, such as simulation reports, timing-analysis output or a public dataset. It should also cover the range of situations where the model will be used.

**Cleaning.** Raw data usually needs checking before training. Here is a small made-up example of what problems look like:

| Run | Delay (ns) | Power (mW) | Design type | Timing result | Problem |
|---|---:|---:|---|---|---|
| R9 | 1.05 | *(missing)* | High complexity | Pass | Missing value; label written "Pass" |
| R10 | 0.88 | 12.7 | Low complexity | PASS | (fine) |
| R11 | 1.18 | 14.2 | Medium complexity | FAIL | Appears twice (duplicate) |
| R11 | 1.18 | 14.2 | Medium complexity | FAIL | Appears twice (duplicate) |
| R12 | 9.5 | 13.0 | Low complexity | SUCCESS | Delay looks like a typo (0.95?); label is "SUCCESS" instead of "PASS" |

Common problems:
- **Missing values:** some measurements are absent.
- **Noisy data:** measurements contain random variation or measurement error.
- **Inconsistent labels:** the same outcome is written in different ways (PASS, Pass, SUCCESS).
- **Incorrect values:** a number is wrong because of a collection or processing error.
- **Duplicates:** the same sample appears more than once and gets extra weight.

Each should be investigated against the original reports before training, not just silently dropped or guessed.

## 7. Why More Data Does Not Guarantee Better Data

Quantity says how *much* data there is. Quality says whether it is *correct, relevant, consistent and representative*.

- 100,000 timing reports with wrong PASS/FAIL labels teach the model wrong answers, just at scale.
- A huge dataset collected only from small, simple designs may say nothing useful about large, complex ones.
- Duplicates inflate the size without adding new information.

A smaller, carefully checked dataset can be more useful than a larger messy one.

## 8. Two Ways Data Quality Can Affect a Model

**1. Wrong or inconsistent labels.** If a run that really failed timing is labelled PASS, the model is taught a false example. Repeated label errors blur the real pattern, so the model makes less reliable predictions. The evaluation can also look wrong, because the "correct answers" it is compared against are themselves wrong. *Check:* compare labels against the original timing reports and apply one consistent labelling rule.

**2. Unrepresentative data.** If the training runs are mostly Low complexity designs, the model may learn patterns that only hold for those, and then perform poorly on High complexity runs it has rarely seen. *Check:* look at how the data is spread across design types and measure performance separately for each group.

(Missing or incorrect measurements, such as the typo in R12, are a third example: they distort the learned relationship between features and target.)

## 9. Connection to Design Verification

Simulation results, coverage reports and failure logs are data that could in principle reveal patterns, such as which kinds of tests tend to find failures. For that to be dependable, the data must be accurate, consistently labelled and representative of the designs the model will be used on. This is a possible idea to investigate, not a claim about an existing tool.

## 10. Conclusion

An ML model learns patterns from the examples it is given. Features are the inputs, and the label or target is the answer it learns to predict in supervised learning. Data can be structured or unstructured, labelled or unlabelled, and its features can be numerical or categorical. Missing values, noise, duplicates, wrong labels and unrepresentative samples all reduce model quality, and more data helps only if it is good data.

## 11. Sources

Full list with the claims each one supports is in [`sources.md`](sources.md) (Mission 2 section).
