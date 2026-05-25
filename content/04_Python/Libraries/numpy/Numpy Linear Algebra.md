---
tags:
  - numpy
  - python
  - concept
  - linear-algebra
created: 2026-04-28
---

# Numpy Linear Algebra

This note covers the `numpy.linalg` module.

> For the mathematics behind these functions, check [[07_Math/Linear_Algebra/Linear Algebra|Linear Algebra]].

#### `det()` function

Calculates the determinant of a given matrix. The matrix must be a **square matrix** (n\*n).

```python
from numpy import linalg as LA

A = np.arrange(1,5).reshape(2,2)
> [[1  2]
   [3 4]]

LA.det(A)
> -2
```

#### `inv()` function

Calculates the inverse of a given matrix. The determinant **must not be 0** and matrix **must be square**.

```python
LA.inv(A)
> [[-2     1]
   [1.5 -0.5]]
```

#### `norm()` function

Calculates the norm of a **vector**. This operation does not work with matrices. 

By default, it calculates the **L2 norm**.

```python
x = np.array([1,2,3,4])

LA.norm(x)
> 5.48
```

By specifying the `ord` argument, it corresponds to the Lp norm.

```python
LA.norm(x, ord=1)
> 10
```

When `ord` is set to `np.inf`, it calculates the L∞ norm.

```python
LA.norm(x, ord=np.inf)
> 4
```

**L1, L2 and L∞ norms** are the most used ones, and they correspond, respectively, to:
- The sum of the absolute values, called Manhattan Norm
- Distance in a straight line in space, called Euclidean Norm
- Biggest absolute value, called L∞ or L<sub>inf</sub>
