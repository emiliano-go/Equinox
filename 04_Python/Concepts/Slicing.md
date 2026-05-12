---
tags:
  - python
  - concept
created: 2026-04-28
---

Slicing is [[10_Atomic/Subscript Notation]] to get a subrange from a sequence.

For any array, you can slice its contents.

```python
arr = [1,2,3,4,5,6,7,8,9]
```

You use the `start:stop:step` format.

```python
sliced = arr[2:5:1]
> [3,4,5]
```

The `start:stop:step` format:
- `start` is included
- `stop` is excluded

You can skip values.

If you **skip the start**, it starts at index `0`.

```python
sliced = arr[:5:1]
> [1,2,3,4,5]
```

If you **skip the end**, it goes until the end of the list.

```python
sliced = arr[2::1]
> [3,4,5,6,7,8,9]
```

If you **skip the step**, it defaults to `1`.

```python
sliced = arr[2:5:]
> [3,4,5]
```

You can even skip the `:` entirely.

```python
sliced = arr[2:5]
> [3,4,5]
```

**You can set negative values for all variables**.

**Start** and **end** with negative values just use the index starting from **the end of the array**.

**Step** with negative values **traverses the array backwards**.

```python
sliced = arr[4:1:-1]
> [5,4,3]
```

**Important:** If you use a **negative step**, `start` must be **bigger** than `stop`.

When both **start** and **stop** are omitted but **step** is negative, the array gets reversed.

```python
sliced = arr[::-1]
> [9,8,7,6,5,4,3,2,1]
```

You can also skip indexes with `step =/= |1|`

```python
sliced = arr[::2]
sliced_reversed = arr[::-2]
> [1,3,5,7,9] # Skipping one
> [9,7,5,3,1] # Skipping one from the back
```

