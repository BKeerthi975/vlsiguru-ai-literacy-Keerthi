
# Mission 1: Build the AI and ML Landscape

## 1. Objective

The objective of this mission is to understand Artificial Intelligence (AI), Machine Learning (ML), conventional rule-based programming, and the relationship between deep learning, generative AI, and Large Language Models (LLMs).

## 2. AI and ML Concept Map

```text
Artificial Intelligence (AI)
|
|-- Rule-based systems
|   |-- Use predefined rules and logic
|
|-- Machine Learning (ML)
    |-- Learns patterns from data
    |
    |-- Deep Learning
    |   |-- Uses multi-layer neural networks
    |
    |-- Generative AI
        |-- Generates text, images, code, etc.
        |-- LLMs process and generate language
```

Note: This is a simplified map. Generative AI is a category of AI systems, not simply a direct child of deep learning. Many generative AI systems use deep learning, and many modern LLMs use transformer architectures.

## 3. AI, Rule-Based Programming, and ML

### Artificial Intelligence (AI)

AI is a broad field of computer science that aims to build systems capable of tasks associated with intelligent behaviour, such as reasoning, problem-solving, and decision-making.

### Conventional Rule-Based Programming

In rule-based programming, a developer explicitly writes the instructions and conditions that a computer follows to produce an output.

Example: A Verilog testbench checks whether a circuit output matches the expected value.

### Machine Learning (ML)

ML is an approach in which a computer learns patterns from training data and uses them to make predictions or generate outputs for new inputs.

Example: An ML model learns from historical timing reports to predict whether a new design run may pass or fail timing.

## 4. Five Important Distinctions

### 1. AI vs ML

AI is the broader field of building systems that perform intelligent tasks. ML is one approach within AI that learns patterns from data.

### 2. Rule-Based Programming vs ML

Rule-based programming follows explicitly written instructions. ML learns patterns from examples rather than requiring every decision rule to be manually specified.

### 3. ML vs Deep Learning

ML includes different methods for learning from data. Deep learning is a subset of ML that uses neural networks with multiple layers.

### 4. Deep Learning vs Generative AI

Deep learning describes a family of learning techniques. Generative AI describes systems that create new content, such as text, images, or code. Many generative AI systems use deep learning.

### 5. Generative AI vs LLMs

Generative AI is a broad category of systems that generate content. LLMs are designed to process and generate language. Many modern LLMs are generative AI systems.

## 5. Why Automation Is Not Necessarily AI

Automation means performing a task automatically with minimal human intervention. It can work using fixed instructions without learning from data.

For example, a script that runs a simulation every night is automation, but it does not necessarily use AI.

AI does not always mean ML because some AI systems use predefined rules, logic, or search techniques instead of learning from data.

## 6. Explicitly Programmed vs Learned from Data

- Explicitly programmed: Instructions, conditions, and rules written by the developer.
- Learned from data: Patterns and relationships identified by an ML model during training.

In Design Verification, an engineer can explicitly program assertions to check expected behaviour. An ML model could learn from historical simulation results to identify patterns associated with failures.

ML systems still require programming. The difference is that some of their predictive behaviour is learned from examples.

## 7. Three Examples Classified with Reasons

### Example 1: Automated Simulation Execution

Classification: Conventional automation.

Reason: A script executes predefined commands to run simulations and save logs. It does not need to learn patterns from data.

### Example 2: Timing Pass/Fail Prediction

Classification: Supervised ML - classification.

Reason: A model learns from historical design measurements with known pass/fail outcomes and predicts the category for a new design run.

### Example 3: A Text Assistant Generating Verilog Explanations

Classification: Generative AI using an LLM.

Reason: It processes a text prompt and generates a natural-language response. Many modern LLMs use deep learning and transformer architectures.

## 8. Application to VLSI Design Verification

Conventional automation is useful for running testbenches, checking assertions, and collecting simulation logs. ML could complement these techniques by analysing historical failures or helping prioritise tests for investigation.

However, an ML prediction should not automatically replace functional checks, assertions, or engineering review. Its usefulness must be evaluated using suitable data and reliable performance measurements.

## 9. Conclusion

AI is the broad field, while ML is an approach that learns patterns from data. Deep learning uses multi-layer neural networks, generative AI creates content, and LLMs specialise in language-related tasks. Automation can work without AI, and AI can work without ML. Engineers should choose the approach that best fits the problem, available data, and required outcome.

## 10. Sources

1. Google for Developers - Introduction to Machine Learning:
   https://developers.google.com/machine-learning/intro-to-ml/what-is-ml

2. Google Cloud - AI vs Machine Learning:
   https://cloud.google.com/learn/artificial-intelligence-vs-machine-learning

3. Google for Developers - Machine Learning:
   https://developers.google.com/machine-learning/

4. Google for Developers - Machine Learning Problem Framing:
   https://developers.google.com/machine-learning/problem-framing

## 11. Source Verification Notes

- Source 1 supports the explanation of ML, learning from data, classification, and generative AI.
- Source 2 supports the distinction between AI and ML.
- Source 3 provides additional introductory ML learning resources.
- Source 4 helps explain how to decide whether ML is appropriate for a problem.

The VLSI/DV examples in this file are illustrative applications. They should not be interpreted as claims that a particular commercial tool already implements these capabilities.
