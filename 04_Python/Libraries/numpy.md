---
tags:
  - numpy
  - python
  - library
created: 2026-04-20
---

# Introduction

Almost all data can (and will eventually) be represented as vectors and matrices.

[[04_Python/Concepts/Vectors|Vectors]] are represented in numpy using 1D arrays. 
[[04_Python/Concepts/Matrices|Matrices]] are represented in numpy using 2D arrays.

In Libraries, the [[04_Python/Concepts/Import Conventions|convention]] is to import `numpy` as `np`.

```python
import numpy as np
```

**Numpy** is a specialized python library made for efficient numerical computation.

## Vectors: 1D Arrays

**Numpy Arrays** allow to represent different mathematical structures, like **Vectors**.

```python
# Numpy Array
arr = np.array([1,2,3,4,5,6]) 

# You can also pass variables
arr = [1,2,3,4]
nparr = np.array(arr)
```

To get the length of an array, we can use the `shape` attribute.

```python
array_size = nparr.shape
> (4,)
```

You can make use of basic arithmetic symbols to operate in numpy arrays.

```python
sumarr = arr1 + arr2
diffarr = arr1 - arr2
prodarr = arr1 * arr2
divarr = arr1 / arr2
```

You also have more advanced functions.

```python
np.max(arr) # max value of an array
np.min(arr) # min value of an array
np.sum(arr) # sum of array values
np.mean(arr) # average value of the array
np.std(arr) # Array's [[06_Statistical_Analysis/Standard Deviation | standard deviation]] 
```

In **numpy**, you can represent **infinity** using `np.inf` as a value.

Read[[04_Python/Libraries/numpy/Numpy 1D Arrays | more about numpy 1D arrays]].

### Conditional Operations

In numpy, conditional operations between arrays are evaluated element by element, not as the full array:

```python
a = np.array([1, 2, 3, 4, 5])
b = np.array([2, 2, 3, 6, 1])

print("a==a:", a==a)
> a==a: [ True  True  True  True  True]
print("a==b:", a==b)
> a==b: [False  True  True False False]
print("a>b:", a>b)
> a>b:  [False False False False  True]
```

Read [[04_Python/Libraries/numpy/Numpy Conditional Operations | more about numpy conditional operations]].

### Broadcasting

In Numpy, when performing a universal binary operation on two arrays with different lengths or dimensions, one of the arrays is automatically broadcast to match the other in terms of dimensions and length. This is called **broadcasting**.

```python
arr = np.array([1,2,3,4])
res = arr * 2
```

Due to broadcasting, that translates to:

```python
res = [1,2,3,4] * [2,2,2,2]
```

Details on how this works can be seen in [[04_Python/Libraries/numpy/Matrix Broadcasting|Matrix Broadcasting]].

**Broadcasting doesn't work for all matrices**. 

Broadcasting works when dimensions are compatible. Starting from the trailing dimensions, two dimensions are compatible when they are equal or when one of them is 1. If dimensions are not compatible, a `ValueError` is raised.

### Concatenation

Unlike in Python, using the `+` operator in numpy doesn't concatenate two arrays. To concatenate arrays in numpy we use the `concatenate` method.

```python
np.concatenate((arr1, arr2))
```

### Indexing

Indexes are the easiest way to retrieve data from an array.

```python
arr = np.array([1,2,3,4,5])

print(arr[0])
> 1
```

**Indexes always start at 0 unless specified otherwise.**

#### Negative Indexes

You can use **negative indexes** to retrieve data from the end of the array.

```python
print(arr[-1])
> 5
```


#### Multiple Retrieval

In **numpy**, you can specify multiple indexes to retrieve multiple values at the same time.

```python
print(arr[np.array([3, 1, -1])])
> [4, 2, 5]
```

They return as an array.

#### Boolean Indexing

**Boolean Indexing** allows to filter elements of an array based on a conditional statement.

```python
arr = np.array([1,2,3,4,5,6,7,8,9,10])
condition = arr % 2 == 0
> [False, True, False, True, False, True, False, True, False, True]
```

You can use this to filter outlier values.

```python
arr = np.array([-524,-240,12,35,45,56,234,347])
filtered_arr = arr[(arr > 0) & (arr < 100)]
> [12,35,45,56]
```

Read more about [[04_Python/Concepts/Conditional Filtering|conditional filtering.]]
### Slicing

**Numpy 1D slicing** works the same as [[04_Python/Concepts/Slicing |Python slicing]]. 

## Matrices: 2D Arrays

2D arrays (or nD arrays for that purpose) represent **matrices**. They work almost the same as 1D arrays.

```python
matrix = np.array([
	[1,2,3],
	[4,5,6],
	[7,8,9]
])
```

We can use the `shape` attribute to get the matrix shape. `shape` returns a tuple.

```python
matrix.shape
> (3, 3)
```

We can use the `reshape()` method to reshape an array.

```python
arr = np.array([1,2,3,4,5,6])
matrix = arr.reshape(3,2)
```

**Reshape Rule**: An matrix can only be reshaped if: n\*m = a\*b. This means that a matrix with *n* height and *m* length can be reshaped into any matrix with *a* height and *b* length if 
`n*m = a*b`.

> Rule for Matrices= n\*m = E, E being the total of individual elements in a matrix.

### Math Operations

Math operations on 2D arrays are the same as in 1D arrays, so they will be computed per element. Rules of broadcasting also apply here. As a result, multiplication and division are element-wise calculations to be different from the actual matrix multiplication.

See more in [[04_Python/Libraries/numpy/Matrix Math|Matrix Math]].
### The Axis Parameter

Because nD arrays can get pretty big, we need a way to determine which **axis** we need to use. 

We can pass the `axis` parameter to any `ndarray` method.

```python
np.min(matrix, axis=0)
np.max(matrix, axis=1)
```


### Slicing
**Numpy 2D** (or higher dimensions) **slicing** doesn't work the same as python slicing.

We can use the standard **array of arrays** notation.

```python
first = matrix[0][0]
last = matrix[-1][-1]
```

But numpy provides a better alternative: [[04_Python/Libraries/numpy/Multidimensional Slicing|multidimensional slicing]].

**In short**:

Instead of using `arr[x][y]` we use `arr[x,y]`. We add a parameter for each axis the matrix has

```python
arr[0] # Take the first value
matrix[0,0]
cube[0,0,0]
teseract[0,0,0,0]
```

This also works with normal slicing as values for the axis parameters.

```python
matrix[:, 3] # Everything from axis 0, of column 3 of axis 1 
```

And, with list as parameters!

```python
cube[:, 2, [0, 2, 4]] # Full axis 0, Colunm 2 of axis 1, Columns 0, 2 and 4 of axis 2
```

And also conditional statements!

```python
cube[:, 4, (cube[0, 4, :] % 2 == 0)]
```

Read[[04_Python/Libraries/numpy/Numpy 2D Arrays | more about numpy 2D arrays]].
## Constants

**Numpy** has a number of constants.

```python
np.pi  # 3.141592653589793
np.e   # 2.718281828459045
np.inf # inf
-np.inf # -inf
```

`np.inf` has a number of set properties.

```python
1 + np.inf
> inf

1 -np.inf
> -inf

2 * np.inf
> inf

2 / np.inf
> 0.0

1000000000000 < np.inf
> True

100000000000 > -np.inf
> True
```

## Random Values

**Numpy** allows to generate random values using the `numpy.random` module.

The `random` module allows us to create arrays of random values.

### Uniform Distribution

We use `rand` to generate a uniform distribution of values between \[0, 1).

We want uniform distributions when we are running simulations where all outcomes are **equally likely**.

```python
uni = np.random.rand()
uniarr = np.random.rand(5) # Random uniform distribution array of size 5
unimtrx = np.random.rand(5, 3) # Matrix of shape (5, 3)
```

### Normal Distribution

We use `randn` to generate a normal distribution of values whose mean is ~0 (See [[06_Statistical_Analysis/Law of Large Numbers|the Law of Large Numbers]]) and variance is 1.

We want normal distributions when we are **modeling natural variation**.

```python
norm = np.random.randn()
normarr = np.random.randn(5) # Random uniform distribution array of size 5
normmtrx = np.random.randn(5, 3) # Matrix of shape (5, 3)
```

### Integer Generation

We use `randint` to generate integers.

`randint` takes 3 parameters.

```python
np.random.randint(low, high=None, size=None, dtype=int)
```

**low**: lowest integer (inclusive)
**high**: optional parameter. Upper bound (exclusive). If omitted, range is  (0, **low**)
**size**: optional parameter. Shape of the output

```python
np.random.randint(-5, 10, (5,5))
# Generates values from -5 (included) to 10 (excluded) in a 5*5 matrix
```

### Seed

The random number generation above produces different results each time it is executed. However, there are cases where you may want to fix the generated random numbers for reproducibility.

By setting a **seed** (the random number seed), you can ensure that the same random numbers are generated if the seed is the same.

```python
np.random.seed(32)
```

**A better practice** is to **not** set a global state and use a local variable.

```python
rng = np.random.default_rng(32)
rng.random(5)
```

This uses the **new numpy API** which gives better results.

```python
rng.random(534) # Replaces rand
rng.integers(-5, 10, (12,4)) # Replaces randint
rng.standard_normal((3, 2)) # Replaces randn
```

See more in [[04_Python/Libraries/numpy/Random|the random module page]].

## Linear Algebra Computation

**Numpy** includes a module called `linalg` that allows various linear algebra calculations.

Import convention is `from numpy import linalg as LA`.

Some basic methods are `det()` and `inv()`.

```python
LA.det(A) # Calculates the determinant of a matrix
LA.inv(A) # Calculates the inverse of a matrix
```

`inv()` method doesn't work in **singular matrices**.

```python
LA.norm(A) # Calculates the norm
LA.norm(A, ord=1) # Calculates the L1 norm = sum of absolute values
LA.norm(A, ord=np.inf) # Calculates L∞, the largest absolute value
```

See more in [[04_Python/Libraries/numpy/Numpy Linear Algebra|linear algebra with numpy]].
