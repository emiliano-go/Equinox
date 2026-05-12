---
tags:
  - numpy
  - python
  - concept
created: 2026-04-28
---

For **Numpy arrays** with more than 1 dimension, we slice by passing one selector per axis.

General form:

- 2D array: `arr[row_selector, col_selector]`
- 3D array: `arr[axis0_selector, axis1_selector, axis2_selector]`
- nD array: `arr[selector0, selector1, ..., selectorN]`

Each selector can be:

- an integer (pick one index)
- a slice (`start:end:step`)
- a list/array of indices
- a boolean mask
- `...` (ellipsis, "fill the rest")
- `None` (add a new axis)

## 2D Basics

```python
matrix = np.array([
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
])

matrix.shape
# (3, 4)
```

```python
matrix[0, 0]      # 1 (single value)
matrix[1, :]      # [5, 6, 7, 8] (row)
matrix[:, 2]      # [3, 7, 11] (column)
matrix[0:2, 1:3]  # [[2, 3], [6, 7]]
```

## Negative Indexing and Reverse Slicing

```python
matrix[-1, -1]  # 12 (last row, last column)
matrix[::-1, :] # rows reversed
matrix[:, ::-1] # columns reversed
matrix[:, -2:]  # last 2 columns
```

## 3D Slicing

```python
cube = np.arange(2 * 3 * 4).reshape(2, 3, 4)
cube.shape
# (2, 3, 4)

cube[0, :, :]    # first 2D block
cube[:, 1, :]    # all blocks, second row
cube[:, :, 2]    # all blocks, third column
cube[:, 1, 1:4]  # slice on last axis
```

## Ellipsis and New Axis

```python
cube[..., 0]        # same as cube[:, :, 0]
cube[:, None, :, :] # adds one dimension
```

`None` (or `np.newaxis`) is useful to reshape arrays before broadcasting.

## Integer and Boolean Indexing

```python
matrix[[0, 2], :]   # take rows 0 and 2
matrix[:, [1, 3]]   # take columns 1 and 3

mask = matrix % 2 == 0
matrix[mask]        # flattened array with all even values
```

## Assignment with Slices

```python
matrix[:, 0] = 0     # set first column to zero
matrix[0:2, 1:3] = 9 # set a submatrix
```

## Shape Behavior (Important)

Using an integer index removes that axis. Using a slice preserves it.

```python
matrix[1, :].shape   # (4,)
matrix[1:2, :].shape # (1, 4)
```

## View vs Copy

- Basic slicing (like `arr[1:4, :]`) usually returns a **view**.
- Advanced indexing (lists/boolean masks) usually returns a **copy**.

This matters when you modify the result and expect the original array to change.
