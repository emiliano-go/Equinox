---
tags:
  - math
  - information-gain
  - decision-trees
created: 2026-05-26
---

**Information Gain** (IG) is a measure used in [[Supervised Learning#Decision Trees|Decision Trees]] to quantify how much a **feature** reduces **uncertainty** ([[Entropy]]). about the target variable after splitting the data.

**Mathematically**, is the **difference** between the entropy **before** the split and the **weighted entropy after** the split. A high IG means the feature creates a split that separates the classes well, making the data more "organized" and easier to classify. 

$$
IG(S, A) = H(S) - \sum_{v \in Values(A)} \frac{|S_v|}{|S|} H(S_v)
$$

Where:

- $IG(S,A)$ = Information Gain of attribute **A**
- $H(S)$ = Entropy of the original dataset **S**
-  $S_{v}$ = Subset of data where attribute **A** has value **v**
- $\frac{|S_{v}| }{|S|}$ = Weight (proportion of subset size)
- $H(S_{V})$ = Entropy of each subset after splitting

### Entropy of the dataset
$$
H(S) = -\sum_{i=1}^{c} p_i \log_2(p_i)
$$
Where:
- $c$ = number of classes
- $p_{i}$ = proportion of class $i$ in dataset $S$

Measures the **uncertainty / disorder** in the whole dataset before splitting.

#### Probability of a class in the dataset
$$
p_i = \frac{\text{number of samples in class } i}{\text{total samples in } S}
$$
### Subset Weight
$$
\frac{|S_v|}{|S|}
$$
Where:
- $|S_{v}|$ = number of samples in subset where attribute $A=v$
- $|S|$ =  total samples in original dataset

So:
$$|S_{v}|=\text{count of rows where }A=v$$
$$|S| = \text{total number of rows}$$
### Entropy of each subset

Entropy formula applied to the subset, where $p_{i, v} = \text{samples of class in the subset }S_{v}$.
$$
H(S_v) = -\sum_{i=1}^{c} p_{i,v} \log_2(p_{i,v})
$$
$$
p_{i,v} = \frac{\text{samples of class } i \text{ in subset } S_v}{|S_v|}
$$
