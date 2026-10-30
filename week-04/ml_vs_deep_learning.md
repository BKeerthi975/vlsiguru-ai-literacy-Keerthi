# Mission 2 – What Makes Deep Learning Different?

**Question:** Why do we need neural networks when we already have traditional machine learning?

## How the terms relate
Artificial intelligence is the broad goal of machines doing tasks that need intelligence. Machine learning
is a part of AI where systems learn patterns from data instead of following only hand-written rules.
Neural networks are one family of ML models. Deep learning means using neural networks with several
hidden layers.

## Comparison table
| Approach | How it works | Problems it may handle | Example | Limitation |
|---|---|---|---|---|
| Rule-based | Engineers write explicit if/then rules | Clear, stable conditions that can be written down | **Semiconductor:** flag a wafer if more than X% of dies fail. **Outside:** spam filter blocking a fixed word list | Cannot handle patterns nobody can describe; rules multiply and break on new cases |
| Traditional ML | Engineers design features; the model (e.g. SVM, decision tree) learns from them | Structured/tabular data, small or medium datasets | **Semiconductor:** classify wafer patterns from hand-made features (fail ratio, position) with an SVM. **Outside:** predicting house prices from size, location, age | Quality depends on the hand-made features; struggles with raw images, audio or text |
| Deep learning | A multi-layer neural network learns its own features from raw data | Complex inputs: images, audio, language | **Semiconductor:** CNN reads wafer-map or inspection images directly. **Outside:** voice assistant converting speech to text | Needs lots of labelled data and compute; harder to explain; can overfit |

## Research topics
**What is a neural network?** It is a model made of many small computing units (neurons) connected in layers.
Each unit does a simple calculation, and the network can represent complex patterns because many simple
units are combined. Google's course describes neural networks as models designed to find nonlinear
patterns, learning useful feature combinations automatically instead of the engineer designing them by hand.

**What does "learning useful patterns" mean?** The model adjusts its internal numbers (weights) so that its
predictions on training examples get closer to the correct answers, and so that the same patterns also work on
new data.

**Why is deep learning useful for images, audio and language?** These inputs have huge numbers of raw values
with patterns at several scales (edges, then shapes, then objects). Layers can learn those steps automatically.

**Does adding more layers automatically help?** No. A bigger network can overfit (memorise training data),
needs more data and compute, and can be harder to train. Google's course notes problems such as vanishing
gradients in deep networks. More layers help only if the problem and data justify them.

**When is a simple rule or traditional ML better?** When the data is small or tabular, the rule is clear,
the decision must be easy to explain, or a simple threshold already works. Using deep learning where a
threshold works adds cost and risk without benefit.
