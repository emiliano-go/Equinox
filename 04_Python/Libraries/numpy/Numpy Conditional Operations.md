---
tags:
  - numpy
  - python
  - io
created: 2026-04-28
---

# Numpy Conditional Operations

Conditional operations in numpy evaluate element by element.

```python
a = np.array([1, 2, 3, 4, 5])
b = np.array([2, 2, 3, 6, 1])

a == a  # [True, True, True, True, True]
a == b  # [False, True, True, False, False]
a > b   # [False, False, False, False, True]

# Use with np.where for conditional selection
np.where(a > 3, a, 0)  # [0, 0, 0, 4, 5]
```