# Sources and Claim Mapping

## Learning resources I used
| Source | Used for |
|---|---|
| Google ML Crash Course – Neural networks: https://developers.google.com/machine-learning/crash-course/neural-networks | What neural networks are for, nodes, hidden layers, activation functions |
| Google ML Crash Course – Training using backpropagation: https://developers.google.com/machine-learning/crash-course/neural-networks/backpropagation | Backpropagation as the main training algorithm, vanishing gradients, dropout |
| Google ML Crash Course – Dividing the original dataset: https://developers.google.com/machine-learning/crash-course/overfitting/dividing-datasets | Three-way split, validation/test sets "wearing out", removing duplicates |
| Google ML Crash Course – Working with numerical data: https://developers.google.com/machine-learning/crash-course/numerical-data | Normalisation and data preparation |
| Google ML Crash Course – Datasets, generalization, and overfitting: https://developers.google.com/machine-learning/crash-course/overfitting | Labels, imbalance, overfitting, generalisation |
| TensorFlow Neural Network Playground: https://playground.tensorflow.org/ | Mission 5 experiment |

## Case-study sources
| # | Source | Type | Supports |
|---|---|---|---|
| 1 | Wafer Map Defect Classification Using Autoencoder-Based Data Augmentation and CNN, arXiv: https://arxiv.org/pdf/2411.11029 | Research paper | WM-811K size (811,457 maps; 172,950 labelled) and class counts |
| 2 | Wafer map defect pattern classification using deep selective learning (CNN with reject option), NSF PAR: https://par.nsf.gov/servlets/purl/10192082 | Research paper | CNN approach, reject option, earlier feature + SVM approach |
| 3 | MathWorks, Classify Defects on Wafer Maps Using Deep Learning: https://www.mathworks.com/help/vision/ug/classify-defects-on-wafer-maps-using-deep-learning.html | Tutorial / documentation example | WM-811K description, wafer maps as pass/fail images, CNN workflow |
| 4 | Ji and Lee, "Using GAN to improve CNN performance of wafer map defect type classification", ASMC 2020: https://pure.skku.edu/en/publications/using-gan-to-improve-cnn-performance-of-wafer-map-defect-type-cla/ | Conference paper | CNNs on WM-811K, accuracy 97.0% to 98.3% with augmentation |
| 5 | Wafer Map Defect Patterns Semi-Supervised Classification Using Latent Vector Representation, arXiv: https://arxiv.org/pdf/2311.12840 | Research paper | Normal wafers are about 85% of the labelled WM-811K data; metrics for imbalanced data |

## Claim I checked
Two papers describe the share of normal wafers in the labelled WM-811K data differently: arXiv 2311.12840 says about 85%,
while arXiv 2411.11029 says 18.2%. I added up the class counts listed in arXiv 2411.11029:
4,294 + 555 + 5,189 + 9,680 + 3,593 + 866 + 1,193 + 149 = 25,519 defect examples. Subtracting this from 172,950 labelled maps
leaves 147,431 normal ones, which is about 85.2%. So the 85% figure fits the counts, and the 18.2% figure appears to be
inconsistent with that paper's own numbers. Lesson: even published sources can contain inconsistencies, so numbers
should be cross-checked.

## Established, research or proposal?
- Established concepts: neural network basics, backpropagation, train/validation/test splitting (Google course).
- Research demonstrations: CNN wafer-map classification on WM-811K (sources 1, 2, 4, 5).
- My own proposals: lot-wise splitting, reject-option workflow, baseline comparison, per-class evaluation plan.
