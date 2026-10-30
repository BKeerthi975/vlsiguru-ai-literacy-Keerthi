# Final Challenge – Case Study: Wafer-Map Defect Pattern Classification

**Status labels used below:** [Research] = published research demonstration, [Proposal] = my own proposed design.

## 1. Problem
Failing dies on a wafer form spatial patterns (ring, scratch, centre cluster) that point to different process
problems. Engineers must classify thousands of wafer maps. Goal: automatically classify the pattern so engineers can
prioritise root-cause investigation. A wafer map is a pass/fail map from electrical testing, so it is not an optical image.

## 2. Input data
Wafer maps, i.e. 2-D grids with a value for background, passing die and failing die. [Research] The public WM-811K
dataset has 811,457 wafer maps, of which 172,950 are manually labelled [1][3].

## 3. Preparation and labels
Maps differ in size, so resize them to one shape. Keep values as the three map codes. Labels are the pattern
class (eight defect patterns plus "none") assigned by engineers. [Proposal] Remove duplicates, have a second
engineer review doubtful labels, and keep only one version of each wafer across all splits.

## 4. What the model predicts
One class per wafer map, plus a confidence score. [Proposal] Maps with low confidence go to an engineer
instead of getting a forced label (a "reject option", as used in one published approach [2]).

## 5. Why deep learning could suit it
Defect patterns are spatial shapes in an image-like grid, and CNNs are designed for that. [Research] Published studies
apply CNNs to WM-811K [1][2][4], and one reports accuracy rising from 97.0% to 98.3% with data augmentation [4],
although that number depends on their data split and metric.

## 6. Rule-based or traditional ML alternatives
Yes, worth testing first. Simple rules (for example "fail rate near the edge above X%") catch obvious patterns.
[Research] A feature-extraction plus SVM approach was the previous state of the art on this dataset [2].
[Proposal] Use such a baseline, and prefer deep learning only if it clearly beats it on rare classes.

## 7. Evaluation on unseen data
[Proposal] Split by production lot (not by individual wafer), because wafers from one lot are similar and random
splitting would leak information. Keep a final test set from a later time period. Report precision, recall and a
confusion matrix per class. Overall accuracy is not enough: the labelled data is about 85% "none" [1][5], so a model
that always says "none" would already score about 85%.

## 8. Wrong predictions and consequences
- *Real pattern missed:* a process problem continues and yield loss grows.
- *False alarm:* engineers waste time on a healthy wafer.
- *Confusing similar patterns (e.g. edge-location vs edge-ring):* the wrong root cause is investigated.
- *New pattern forced into a known class:* a new problem is hidden. A reject option reduces this risk.

## 9. Where humans stay essential
Engineers define labelling rules, review low-confidence and rare-class cases, confirm root causes with failure
analysis, decide process changes, and recheck the model when the process or product changes.

## Limitations
My sources are research studies on one public dataset, and I have not found independent evidence in them of a specific
production deployment, so I treat this as research-demonstrated and not as an established industrial workflow.
Results may differ on a real fab's data.

**Sources:** [1] arXiv 2411.11029; [2] NSF PAR 10192082 (deep selective learning); [3] MathWorks wafer-map example;
[4] Ji and Lee, ASMC 2020; [5] arXiv 2311.12840. Full links in `sources.md`.
