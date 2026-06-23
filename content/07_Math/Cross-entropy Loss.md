---
tags:
  - math
  - cross-entropy
  - machine-learning
created: 2026-05-26
---

# Cross-entropy Loss

Cross-entropy loss is the function used in [[Supervised Learning#Logistic Regression|Logistic Regression]] to measure how well the model’s predicted **probabilities** match the **true** labels. Instead of simply checking whether a prediction is correct or incorrect, it evaluates **how confident** the model was. If the true label is 1 and the model predicts a probability close to 1, the loss is very small. If the model predicts a probability close to 0 for that same case, the loss becomes very large. This makes cross-entropy especially useful because it strongly **penalizes** confident wrong predictions.

The loss works by **considering both possible classes**: when the true label is 1, it focuses on $\log(\hat{y})$, and when the true label is $0$, it focuses on $\log(1-\hat{y})$. Because [[Logarithm|logarithms]] become very negative near zero, incorrect predictions with high confidence produce a large penalty. During **training**, logistic regression **minimizes** this loss by adjusting the weights and bias so that predicted probabilities get closer to the actual labels across all training examples.

$$
L = -\frac{1}{N}\sum_{i=1}^{N}\left[y_i \log(\hat{y}_i) + (1-y_i)\log(1-\hat{y}_i)\right]
$$