---
tags:
  - numpy
  - python
  - concept
  - linear-algebra
created: 2026-04-28
---

# Numpy 2D Arrays

This note covers matrices in Numpy using 2D arrays.

- Shape and dimensions
- Row/column slicing
- Axis-based operations
- Reshape basics

## Base Example

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
])

matrix.shape   # (3, 3)
matrix.ndim    # 2
matrix.size    # 9
```

## 2D Array Methods

### Shape and Structure

```python
matrix.T                  # transpose
matrix.reshape(1, 9)
matrix.reshape(9, 1)
matrix.flatten()          # 1D copy
matrix.ravel()            # 1D view when possible
matrix.astype(float)
```

### Row/Column Selection

```python
matrix[0, :]              # first row
matrix[:, 0]              # first column
matrix[0:2, 1:3]          # submatrix
matrix[[0, 2], :]         # select rows by index list
matrix[:, [0, 2]]         # select columns by index list
matrix[matrix > 4]        # boolean indexing
```

### Aggregation with axis

```python
matrix.sum()              # all elements
matrix.sum(axis=0)        # per column
matrix.sum(axis=1)        # per row
matrix.mean(axis=0)
matrix.min(axis=1)
matrix.argmax(axis=1)
```

### Matrix Operations

```python
matrix + 10
matrix * 2
matrix1 * matrix2         # element-wise
matrix1 @ matrix2         # matrix multiplication
np.dot(matrix1, matrix2)  # same idea for 2D arrays
```

### Joining and Splitting

```python
np.concatenate((a, b), axis=0)  # stack rows
np.concatenate((a, b), axis=1)  # stack columns
np.vstack((a, b))
np.hstack((a, b))
```

For multidimensional indexing and advanced slice patterns, see [[04_Python/Libraries/numpy/Multidimensional Slicing|Multidimensional Slicing]].
