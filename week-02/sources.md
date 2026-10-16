# Week 02 - Sources and Claim Mapping

Each entry says which specific claims the source supports. Anything not listed here is my own illustrative example or reasoning, and is marked as such.

## Mission 1: AI and ML Landscape

### Source 1
- **Title:** Machine Learning & Artificial Intelligence Basics
- **Publisher:** Google for Developers
- **URL:** https://developers.google.com/machine-learning/resources/ml-ai-basics
- **Supports:**
  - ML is the field of programs/systems that train models to make predictions from input data.
  - ML is formally considered a subfield of AI.
  - AI is described as a program or model that can perform sophisticated tasks (examples given: image generation, speech recognition).

### Source 2
- **Title:** Introduction to Machine Learning
- **Publisher:** Google for Developers
- **URL:** https://developers.google.com/machine-learning/intro-to-ml
- **Supports:**
  - Introductory ML concepts, used for the rule-based vs ML contrast and the learning-paradigm names (supervised, unsupervised, reinforcement) used in the concept map.
  - The course itself states that it covers concepts and does not cover implementing ML or working with data.

### Source 3
- **Title:** Introduction to Machine Learning Problem Framing
- **Publisher:** Google for Developers
- **URL:** https://developers.google.com/machine-learning/problem-framing
- **Supports:**
  - The idea that you should decide whether ML is the right tool for a problem before using it (Sections 3 and 11 of Mission 1).

### Own examples (not from a source)
- Chess engine / expert system as AI without ML, the nightly-simulation script as automation, the Verilog explanation assistant, and all VLSI/DV applications are **my own illustrations**. They are not claims that any specific commercial tool implements them.

## Mission 2: Data

### Source 4
- **Title:** Machine Learning Crash Course
- **Publisher:** Google for Developers
- **URL:** https://developers.google.com/machine-learning/crash-course
- **Supports:**
  - The "Datasets, Generalization, and Overfitting" module covers the characteristics of ML datasets and how to prepare data to get high-quality results when training and evaluating a model. Used for the points that data quality matters and that data should be prepared before training (Mission 2, Sections 6 to 8).

### Source 2 (reused)
- **Introduction to Machine Learning** (URL above). Used for the basic ideas of learning from examples, features and labels.

### Own examples (not from a source)
- The 8-row timing dataset, the "messy data" table (missing value, duplicate, typo, inconsistent labels), and the unrepresentative-data scenario are **synthetic and invented by me** to illustrate the concepts. They do not represent real chip-design measurements.

## Verification note

The synthetic datasets and every semiconductor/DV example are illustrative only. No claim is made that any of them is deployed in a real tool or flow.

## Mission 3: Learning Approaches

### Source 2 (reused)
- Introduction to Machine Learning (Google for Developers), URL above.
- **Supports:** the names and basic ideas of supervised, unsupervised and reinforcement learning.

### Source 5
- **Title:** What is machine learning?
- **Publisher:** IBM
- **URL:** https://www.ibm.com/think/topics/machine-learning
- **Supports:** the overview of the major learning approaches, and the point that self-supervised learning is related to unsupervised learning but not identical in every context.

### Own examples (not from a source)
- All semiconductor examples for each approach are my own illustrations.

## Mission 4: ML Task Types

### Source 2 and Source 5 (reused)
- **Supports:** the general ideas of classification and regression as prediction tasks, and the examples of clustering and anomaly detection.

### Own examples (not from a source)
- The 10 classified problems, their inputs and outputs, and the table of algorithms per task are my own summary. Names of algorithms are general knowledge, not tied to one checked source.

## Mission 5: Anatomy of an ML Model

### Source 4 (reused)
- Machine Learning Crash Course (Google), URL above.
- **Supports:** the Linear Regression module's idea of learning a relationship from examples, and loss as a measure of prediction error.

### Own examples (not from a source)
- The 6-row block size / power data and the fitted line are **synthetic**. The line was fitted with a least-squares fit in Python.

## Mission 6: Evaluation and Generalisation

### Source 4 (reused)
- **Supports:** the roles of training, validation and test sets; overfitting and generalisation; and the Classification module's accuracy, precision and recall.

### Source 6
- **Title:** Overfitting (Machine Learning Crash Course)
- **Publisher:** Google for Developers
- **URL:** https://developers.google.com/machine-learning/crash-course/overfitting
- **Supports:** the explanation of overfitting and why performance on unseen examples matters.

### Own examples (not from a source)
- The 1000-run imbalanced example, Models A and B, and the baseline calculations are **synthetic**.

## Mission 7: Why ML Systems Fail

### Source 7
- **Title:** Production ML systems (Machine Learning Crash Course)
- **Publisher:** Google for Developers
- **URL:** https://developers.google.com/machine-learning/crash-course/production-ml-systems
- **Supports:** monitoring, data leakage, changing data (drift) and the gap between test performance and real-world behaviour.

### Source 4 (reused)
- **Supports:** the fairness module's point that model performance can differ across subsets of data.

### Own examples (not from a source)
- The three failure scenarios and the subset-accuracy table are **hypothetical and invented** for learning.

## Mission 8: When to Use ML

### Source 3 (reused)
- Introduction to Machine Learning Problem Framing (Google), URL above.
- **Supports:** deciding whether ML is appropriate, defining the desired output and choosing success metrics before building a model.

### Own examples (not from a source)
- The failure-log classification problem, the rule table and the log lines are **synthetic**. My conclusion ("start with rules") is my own judgement.

## Mission 9: Semiconductor Case Study

### Source 8 (primary)
- **Title:** Supervised Learning for Coverage-Directed Test Selection in Simulation-Based Verification
- **Authors:** N. Masamba, K. Eder, T. Blackmore (University of Bristol, Infineon Technologies)
- **URL:** https://arxiv.org/pdf/2205.08524
- **Supports:** the problem description, the RSPU design and data (300 fields, about 200 coverage groups, about 6,000 coverage points, 86,000 tests), the compared classifiers, the results table and the stated limitations.

### Source 9 (primary, earlier method)
- **Title:** Coverage directed test generation for functional verification using Bayesian networks
- **Authors:** S. Fine, A. Ziv, DAC '03
- **URL:** https://dl.acm.org/doi/10.1145/775832.775907
- **Supports:** an earlier ML-based approach to coverage-directed test generation.

### Own reasoning (not from a source)
- Limitation 8 (re-checking the model when the design changes) is my own reasoning.
