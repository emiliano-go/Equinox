---
tags:
  - numpy
  - python
  - linear-algebra
created: 2026-04-28
---

# Matrix Broadcasting

When performing operations on arrays with different shapes, numpy automatically expands one array to match the other. This is broadcasting.

Rules:
1. Compare dimensions from right to left
2. Dimensions must be equal, or one must be 1
3. If either is 1, expand to match the other

Example:
```python
arr = np.array([1, 2, 3, 4])
arr * 2  # [2, 4, 6, 8]
# Expands [2] to [2, 2, 2, 2]
```

Error case:
```python
a = np.array([1, 2, 3])
b = np.array([1, 2])
a + b  # ValueError: shapes (3,) and (2,) not aligned
```