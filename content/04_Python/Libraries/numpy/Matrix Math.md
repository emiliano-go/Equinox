---
tags:
  - numpy
  - python
  - concept
  - linear-algebra
created: 2026-04-28
---

# Matrix Math

**Matrix Math** centers around **Dot Product** and **Matrix Multiplication**.

> Also see [[07_Math/Linear_Algebra/Matrices|Linear Algebra: Matrices]] for mathematical references

## Dot Product

The **dot product** of a matrix is the multiplication of 2 matrices. 

`np.dot()` is a legacy numpy method that allows for consistent matrix multiplication up to 2D matrices.

`np.matmul` is the new method used for matrix multiplication in numpy, allowing for batched matrix multiplication.

> Rules of matrix multiplication must be followed when using `np.matmul()`

```python
"""
Let's say we have the following matrices:

x: [1 2 3] 
y: [6 7 8] 
A: [[1 2 3] 
    [4 5 6] 
    [7 8 9]] 
B: [[1 4 3] 
    [6 4 3] 
    [9 4 3]]
"""

np.matmul(x, y)
> 44

np.matmul(A, B)
>[[ 40 24 18] 
  [ 88 60 45] 
  [136 96 72]]

np.matmul(B, A)
> [[38 46 54]
   [43 56 69]
   [46 62 78]]
```

### Broadcasting

[[Matrix Broadcasting]] also happens in matrix calculations. 

```python
np.matmul(A, x)
> [14 32 50]

np.matmul(x, A)
> [30 36 42]
```

Refer to [[07_Math/Linear_Algebra/Matrices|Linear Algebra: Matrices]] to understand how this works.

## Transposition

Transposition changes the axis of a given matrix.

```python
import numpy as np  
  
A = np.array([[1,2,3],  
              [4,5,6]]).T
> [[1  4]
   [2  5]
   [3  6]]
```

If A is of an `(n,m)` shape, then A<sup>T</sup> is of `(m,n)` shape.

