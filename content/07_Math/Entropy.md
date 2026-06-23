---
tags:
  - math
  - entropy
  - information-theory
created: 2026-05-26
---

**Entropy** is a measure of the **expected uncertainty** (or information content) of a random variable.
$$
H(X) = -\sum_{i=1}^{n} P(x_i)\log_2 P(x_i)
$$
Where:
- $X$ is a random variable
- $x_{i}$ is the **possible outcome**
- $P(x_{i})$ is the **probability** of the outcome $x_{i}$
### Interpretation
- **Entropy = 0** → no uncertainty (all outcomes are known)
- **High entropy** → high uncertainty (outcomes are mixed/unpredictable)