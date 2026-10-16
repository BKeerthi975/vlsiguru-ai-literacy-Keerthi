# Week 02 Reflection

## 1. Which ML concept became clearest, and what helped?
The concept that became clearest was how accuracy can mislead when classes are imbalanced. At first I thought a high accuracy number meant a good model. Working through my 1000-run example in Mission 6 changed that: a model that always predicts PASS scored 98% accuracy but caught 0 of the 20 failures. Building the confusion matrices by hand and comparing recall and precision made it stick much better than just reading the definitions.

## 2. Which two concepts are easy to confuse?
The two I mixed up most were learning paradigms and task types. Supervised, unsupervised and reinforcement learning describe how a model gets its training signal, while classification, regression and clustering describe what the model outputs. The test I use now is: "Am I describing how it learns, or what it produces?" The same task can use different paradigms (for example, anomaly detection with or without labels), which showed me they are different levels. I also had to be careful with self-supervised and unsupervised learning. Both avoid human-written labels, but self-supervised learning creates its own prediction target from the data, while classic unsupervised learning has no target.

## 3. One claim I checked against a reliable source
I checked the claim that machine learning is a subfield of AI, and that AI also includes methods that do not learn from data (like rule-based or search-based systems). Google's ML and AI basics page confirms that ML is formally a subfield of AI. It did not directly discuss examples like chess engines, so that part of Mission 1 is my own reasoning and I marked it that way in `sources.md`.

## 4. Which stage of the lifecycle is easiest to underestimate?
I think understanding the data is the easiest stage to underestimate. It feels like the boring step before the "real" modelling, but in Missions 2 and 7 almost every failure traced back to data: wrong labels, unrepresentative samples, leakage in the split, or drift over time. A clean-looking model can still fail if the data behind it is not right.

## 5. One question before deep learning
In Mission 5, I understood that training adjusts parameters to reduce the loss, but I don't yet understand how the optimiser decides how much to change each parameter. How does this work when a neural network has millions of parameters?
