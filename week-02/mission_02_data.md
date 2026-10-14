
# Mission 2: Understand Data — What Does an ML System Learn From?

## 1. Introduction

Machine Learning models learn patterns from data. The quality and type of data we provide can affect how well a model makes predictions.

For example, in VLSI, we can use previous timing reports to train a model that predicts whether a new design run will pass or fail timing.

## 2. Important Data Concepts

- **Dataset:** A collection of related data used for analysis or training.
- **Sample:** One example in a dataset.
- **Observation:** The recorded information about one sample. In a tabular dataset, it is usually one row.
- **Feature:** An input value used by the model to make a prediction.
- **Label:** The known answer associated with a sample in a labelled dataset.
- **Target:** The outcome the model is expected to predict.

For example, if we want to predict timing pass or fail, delay and power can be features, while the timing result is the target.

## 3. Types of Data

### Structured Data

Structured data is organised in a fixed format, such as rows and columns in a table.

Example: Timing reports containing delay, power and timing status.

### Unstructured Data

Unstructured data does not follow a fixed tabular structure.

Examples: Images, audio recordings, free-text reports and many log files.

### Numerical Features

Numerical features contain measurable numbers.

Examples: Delay in nanoseconds, power in milliwatts and cell area.

### Categorical Features

Categorical features represent groups or labels.

Examples: Design type, operating mode and process corner.

## 4. Labelled and Unlabelled Data

### Labelled Data

Labelled data contains input examples along with their known outcomes.

Example: A dataset containing timing measurements and the corresponding PASS or FAIL result.

It can be used to train a supervised learning model.

### Unlabelled Data

Unlabelled data contains input examples without known target answers.

Example: Timing measurements from different design runs without their final timing status.

Such data may be useful for finding groups or patterns using unsupervised learning.

## 5. Illustrative Dataset

The following is a synthetic dataset created for this assignment. The values are illustrative and are not taken from an actual chip-design project.

| Run | Delay (ns) | Power (mW) | Design Type | Timing Result |
|---|---:|---:|---|---|
| R1 | 0.80 | 12.5 | Low complexity | PASS |
| R2 | 1.20 | 14.0 | Medium complexity | FAIL |
| R3 | 0.95 | 13.2 | Low complexity | PASS |
| R4 | 1.35 | 15.1 | High complexity | FAIL |
| R5 | 0.75 | 11.8 | Medium complexity | PASS |
| R6 | 1.10 | 14.5 | High complexity | FAIL |

### Identifying the Dataset Components

- **Dataset:** The complete table containing six design runs.
- **Sample/observation:** Each row represents one recorded design run.
- **Features:** Delay, power and design type.
- **Target/label:** Timing Result (PASS or FAIL).
- **Numerical features:** Delay and power.
- **Categorical feature:** Design Type.
- **Labelled data:** All six rows contain a known timing result.

If we wanted to predict the timing result for a new run, we could use delay, power and design type as inputs and timing result as the target.

This small dataset is only for illustration. Six examples are not enough to establish that a model would perform reliably in a real project.

## 6. Data Collection and Preparation

Before using data to train a model, we need to collect and prepare it properly.

### Data Collection

Data can be collected from suitable sources, such as simulation reports, timing analysis tools or publicly available datasets.

The collected data should be relevant to the problem we want to solve.

### Data Cleaning

Data cleaning involves checking and correcting problems in the dataset before using it.

Common issues include:

- **Missing values:** Some measurements or results are absent.
- **Noisy data:** Measurements contain unwanted variations or errors.
- **Inconsistent labels:** The same outcome is recorded using different labels, such as PASS, Pass and SUCCESS.
- **Incorrect values:** A measurement is recorded incorrectly because of a collection or processing error.

These problems should be investigated before training a model.

## 7. Why More Data Does Not Always Mean Better Data

A large dataset is not necessarily a good dataset.

If a dataset contains incorrect measurements, repeated records, missing values or biased examples, the model may learn misleading patterns.

For example, collecting thousands of timing reports with incorrect timing labels may cause a model to make unreliable predictions.

It is important to have data that is accurate, relevant, sufficiently representative and consistently labelled, rather than focusing only on its size.

## 8. Two Ways Data Quality Can Affect a Model

### 1. Missing or Incorrect Measurements

If delay or power values are missing or recorded incorrectly, the model may learn inaccurate relationships between the input features and the target.

This can reduce prediction quality when the model is used on new design runs.

**Possible solution:** Check the source reports, investigate missing values and correct confirmed errors before training.

### 2. Inconsistent or Incorrect Labels

If a design run that failed timing is incorrectly labelled PASS, the model receives a wrong training example. Repeated label errors can confuse the learning process and reduce the reliability of predictions.

**Possible solution:** Verify labels against the original timing reports and apply consistent labelling rules.

## 9. Connection to VLSI Design Verification

Data is important in Design Verification because simulation results, coverage reports and failure logs can contain useful information about a design.

A dataset containing previous test results could potentially help identify patterns associated with failures or prioritise tests for further investigation.

However, the data must be reliable and representative. An ML model cannot be expected to make dependable predictions if its training data contains serious errors or does not represent the conditions in which it will be used.

## 10. Conclusion

From this mission, I understood that an ML model learns patterns from the examples provided to it. Features are the inputs used for prediction, while labels or targets represent the outcomes the model learns to predict in supervised learning.

I also learned that structured and unstructured data are different, and that missing values, noisy measurements and incorrect labels can affect model performance. Having more data is useful only when the data is also suitable for the problem.

## 11. Sources

1. Google for Developers — Introduction to Machine Learning:
   https://developers.google.com/machine-learning/intro-to-ml

2. Google for Developers — Machine Learning Crash Course:
   https://developers.google.com/machine-learning/crash-course

3. Google for Developers — Datasets:
   https://developers.google.com/machine-learning/crash-course/overfitting/dividing-datasets

These resources provide introductory information about machine learning, training data and datasets. The table in this assignment is synthetic and was created only to demonstrate the concepts.
