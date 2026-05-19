---
tags:
  - statistics
  - io
  - numpy
created: 2026-04-28
---

# Standard Deviation

Standard deviation measures how spread out data is from the mean.

- Low std: data points clustered near mean
- High std: data points spread wide
- Formula: `sqrt(sum((x - mean)^2) / n)`
- Related to [[Variance]]: `std = sqrt(variance)`

In numpy:
```python
np.std(arr)
```