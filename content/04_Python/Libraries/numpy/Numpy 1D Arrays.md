---
tags:
  - numpy
  - python
  - concept
  - linear-algebra
created: 2026-04-28
---

# Numpy 1D Arrays

This note covers vectors in Numpy using 1D arrays.

- Creation with `np.array`
- Indexing and slicing
- Element-wise operations
- Boolean filtering

## Row and Column Vectors

When dealing with **vectors**, usually represented as 1D arrays, it's useful to distinguish between **column vectors** (vertical) and **row vectors** (horizontal). Therefore, they're usually treated as 2D arrays, because 2D arrays allow [[Matrix Math#Transposition|transposition]] and other operations to be performed on them.

```python
arr = np.array([1,2,3,4,5]) # 1D array
> [1,2,3,4,5]

arr = arr.reshape(1, -1) # Using -1 for the axis automatically calculates the number of elements
arr.T
> [[1]
   [0]
   [1]
   [0]
   [1]]
```

## 1D Array Methods

Common `ndarray` methods and operations for 1D arrays:

### Shape and Conversion

```python
arr = np.array([1, 2, 3, 4, 5])

arr.shape        # (5,)
arr.ndim         # 1
arr.size         # 5
arr.dtype        # data type
arr.astype(float)
arr.tolist()     # [1, 2, 3, 4, 5]
```

### Ordering and Rearranging

```python
arr.sort()               # in place
np.sort(arr)             # returns sorted copy
arr.argsort()            # indices that sort arr
arr[::-1]                # reverse via slicing
np.flip(arr)             # reversed copy
np.concatenate((a, b))   # join arrays
```

### Selection and Filtering

```python
arr[2]                   # single index
arr[1:4]                 # slice
arr[[0, 2, 4]]           # index array
arr[arr > 2]             # boolean mask
np.where(arr % 2 == 0)   # matching indices
```

### Statistics and Aggregation

```python
arr.min()
arr.max()
arr.sum()
arr.mean()
arr.std()
arr.var()
arr.argmin()   # index of min
arr.argmax()   # index of max
```

### Math and Linear Algebra Helpers

```python
arr + 10
arr * 2
arr1 + arr2
arr1 * arr2             # element-wise product
np.dot(arr1, arr2)      # dot product
np.linalg.norm(arr)     # vector norm
```

### Useful Transformations

```python
arr.reshape(1, -1)   # row vector (2D)
arr.reshape(-1, 1)   # column vector (2D)
arr.flatten()        # 1D copy
arr.ravel()          # 1D view when possible
```
