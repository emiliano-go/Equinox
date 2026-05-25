---
tags:
  - math
  - linear-algebra
  - concept
created: 2026-04-28
---

# Introduction

The equation $A\mathbf{x} = \mathbf{b}$ uses the language of linear combinations. 

The vector $A\mathbf{x} = \mathbf{b}$ is a *combination of the  columns of A*. The equation is asking for a *combination that produces b*. The solution vector $\mathbf{x}$ comes at three levels and all are important:
- **Direct solution** to find $\mathbf{x}$ by forward elimination and back substitution.
- **Matrix solution** using the inverse matrix: $x = A^{-1}\mathbf{b}$ (If $A$ has an inverse).
- **Particular solution** (to $A\mathbf{y} = \mathbf{b}$) plus **nullspace solution** (to $A\mathbf{x} = 0$).

Direct elimination is the most frequently used algorithm in scientific computing. the matrix $A$ becomes triangular, then solutions come quickly.

## Introduction to Vectors

Linear algebra is based around vectors. For two vectors $v$ and $w$, if we add them, 
we get $v + w$. If we multiply them by numbers $c$ and $d$, we get $cv$ and $dw$ . 

Combining this two operations (adding $cv$ to $dw$) gives the **linear combination** $cv + dw$. 

**Example of a Linear Combination**: $c\begin{bmatrix} 1\\1\end{bmatrix} + d \begin{bmatrix}2 \\  3 \end{bmatrix} = \begin{bmatrix}c + 2d \\  c+ 3d \end{bmatrix}$

Then:

$v + w = \begin{bmatrix}1 \\  1 \end{bmatrix} + \begin{bmatrix}2 \\  3 \end{bmatrix} = \begin{bmatrix} 3 \\  4\end{bmatrix}$ is the combination with $c = d = 1$.

### Vectors and Linear Combinations

1. $3v + 5v$ is a typical **linear combination** $cv + dw$ of the vectors $v$ and $w$.
2. For $v = \begin{bmatrix} 1 \\  1\end{bmatrix}$ and $w = \begin{bmatrix} 2 \\ 3\end{bmatrix}$ that combination is $3 \begin{bmatrix} 1 \\  1 \\  \end{bmatrix} + 5 \begin{bmatrix} 2 \\  3\end{bmatrix} = \begin{bmatrix}3 + 10 \\  3 + 15 \end{bmatrix} = \begin{bmatrix} 13  \\  18\end{bmatrix}$
3. The vector $\begin{bmatrix} 2 \\  3  \end{bmatrix} = \begin{bmatrix} 2 \\   0\end{bmatrix} + \begin{bmatrix}0 \\  3\end{bmatrix}$ goes across to $x=2$ and up to $y =  3$ in the $xy$ plane.
4. The combinations $c \begin{bmatrix}1 \\  1\end{bmatrix} + d \begin{bmatrix}2 \\  3\end{bmatrix}$ fill the whole $xy$ plane. they produce every $\begin{bmatrix}x \\  y\end{bmatrix}$.
5. The combinations $c \begin{bmatrix}1 \\  1 \\  1\end{bmatrix} + d \begin{bmatrix}2 \\  3 \\  4\end{bmatrix}$ fill a **plane** in $xyz$ space. Same plane for $\begin{bmatrix}1 \\  1 \\  1\end{bmatrix} · \begin{bmatrix}3 \\  4 \\  5\end{bmatrix}$
6. But $\begin{matrix}c + 2d = 1 \\  c+3d = 0 \\  c+4d=0\end{matrix}$ has no solution because its right side $\begin{bmatrix}1 \\  0 \\  0\end{bmatrix}$ is not on that plane.

**Two separate numbers** $v_{1}$ and $v_{2}$ produce a **two-dimensional vector** $v$:

**Column vector** $v = \begin{bmatrix}v_{1} \\  v_{2}\end{bmatrix}$ 
$v_{1}$ = first component of $v$
$v_{2}$ = second component of $v$

#### Vector Addition
$v = \begin{bmatrix}v_{1} \\  v_{2}\end{bmatrix}$ and $w=\begin{bmatrix}w_{1} \\  w_{2}\end{bmatrix}$ add to $v + w = \begin{bmatrix}v_{1} + w_{1} \\  v_{2}+w_{2}\end{bmatrix}$

The $x_{i}$ components stays separated of the $w_{j}$ components.

**Subtraction follows the same principle**.

### Scalar Multiplication

$2v = \begin{bmatrix}2v_{1} \\  2v_{2}\end{bmatrix} = v+v$
$-v = \begin{bmatrix}-v_{1} \\  -v_{2}\end{bmatrix}$

The components of $cv$ are $cv_{1}$ and $cv_{2}$. The number $c$ is called a **scalar**. 

$v - v = 0$, but 0 is not the number zero, its the **Vector 0**. The vector 0 has components 0 and 0.

There are four linear combinations: sum, difference, zero and scalar multiple:
- $1v + 1w =$ sum of vectors
- $1v - 1w=$ difference of vectors
- $0v + 0w=$ *zero vector*
- $cv + 0w =$ vector $cv$ in the [[#Vector Direction|direction]] of $v$

**Visual representation of vectors**
![[Linear Algebra-1777926345664.png| @darkmode]]
Vector addition $v+w = (3,4)$ produces the diagonal of a parallelogram.


We travel **along** $v$ and then **along** $w$. This means $v + w = w + v$.

---
### Three Dimensional Vectors

A vector with two components corresponds to a point in the $xy$ plane. 
$$v_{1} = x \text{ and } v_{2}=y$$
The arrow ends at $(v_{1}, v_{2})$ and starts from $(0,0)$.

In **3D spaces**, the $xy$ **plane** is replaced by the three dimensional $xyz$ space.

$$v = \begin{bmatrix}
1 \\
1 \\
-1
\end{bmatrix} \text{ and } w = \begin{bmatrix}
2 \\
3 \\
4
\end{bmatrix} \text{ and }v+w=\begin{bmatrix}
3 \\
4 \\
3
\end{bmatrix}$$
The vector $v$ corresponds to an arrow in 3-space.

![[Linear Algebra-1777929856834.png|@darkmode]]

Vectors $\begin{bmatrix}x \\  y\end{bmatrix} \text{ and } \begin{bmatrix}x \\  y \\  z\end{bmatrix}$ correspond to points $(x, y)$ and $(x,y,z)$.

>Notation: $v=\begin{bmatrix}1 \\  1 \\  -1\end{bmatrix} \text{ is also written as } v=(1,1,-1)$

**Notice:** $v$ is not a **row vector**. It's a **column** vector written in a easier way.

In three dimensions, $v+w$ is still a component:
$$v_{1} + w_{1} \text{ and }v_{2}+w_{2} \text{ and }v_{3}+w_{3}$$
**This works for n dimensions:**
$$v_{1} + w_{1} \text{ and }v_{2}+w_{2} \text{ ... and }v_{n} + w_{n}$$

## Lines, Planes and Spaces

### Lines

A line [[#Subspaces|subspace]] is a one-dimensional subspace spanned by vectors that are scalar multiples of a single vector.
$$L = \{cv \mid c \text{ in }\mathbb{R}\}, v \neq 0$$
### Planes

A plane subspace is a two-dimensional subspace spanned by two linearly independent vectors. Equivalently, it consists of all linear combinations of those vectors.
$$P = \{cv+dw \mid c,d \text{ in } \mathbb{R}\},\ v, d \text{ linearly independent}$$

### Spaces

A space subspace is a $k$-dimensional subspace spanned by $k$ linearly independent vectors. Equivalently, it consists of all linear combinations of those vectors.$$S = \{ c_1 v_1 + c_2 v_2 + \cdots + c_k v_k \mid c_1, \dots, c_k \in \mathbb{R} \}, \quad v_1, \dots, v_k \text{ linearly independent}$$
See [[Problem Set 1.1]].

### Component sum

When you take any linear combination $cv +dw$:
$$\text{(first component) + (second component) + (third component)}$$
If every vector in a set has certain linear combination of its coordinates equal to zero, then **every linear combination** of them will also have that property.

### Spaces and Linear Combinations

When a vector $w$ can be written as a [[Linear Combination]] $w = c u + d v$, it means $w$ belongs to the **span** of $u$ and $v$: the set of all possible combinations $c u + d v$. 

If $u$ and $v$ are not parallel (i.e., they are [[Linear Independence]]), their span is a **plane through the origin** in 3D space. Since $u$ and $v$ themselves obviously lie in that plane (by choosing $(c,d) = (1,0)$ or $(0,1)$), adding $w$, which is just another combination, means all three vectors are confined to that same plane. 

Graphically, you can think of $u$ and $v$ as two arrows defining a flat sheet through the origin; any weighted sum of them stays on that sheet. Thus, the condition "$w$ is a linear combination of $u$ and $v$" is exactly the algebraic test for [[Coplanarity]] (through the origin), assuming $u$ and $v$ are not [[Collinearity|collinear]]. 

If $u$ and $v$ were parallel, the span would be just a line, not a plane, but then $u$, $v$, and $w$ would all lie on that line instead.

## Lengths and Dot Products

1. The "dot product" of $v = \begin{bmatrix} 1 \\ 2 \end{bmatrix}$ and $w = \begin{bmatrix} 4 \\ 5 \end{bmatrix}$ is $v \cdot w = (1)(4) + (2)(5) = 4 + 10 = 14$.

2. $v = \begin{bmatrix} 1 \\ 3 \\ 2 \end{bmatrix}$ and $w = \begin{bmatrix} 4 \\ -4 \\ 4 \end{bmatrix}$ are perpendicular because $v \cdot w$ is zero:  
   $(1)(4) + (3)(-4) + (2)(4) = 4 + -12 + 8 = 0$.  

3. The length squared of $v = \begin{bmatrix} 1 \\ 3 \\ 2 \end{bmatrix}$ is $v \cdot v = 1^2 + 3^2 + 2^2 = 1 + 9 + 4 = 14$. The length is $\|v\| = \sqrt{14}$.

4. Then $u = \frac{v}{\|v\|} = \frac{1}{\sqrt{14}} \begin{bmatrix} 1 \\ 3 \\ 2 \end{bmatrix}$ has length $\|u\| = 1$. Check:  
   $\frac{1}{14} + \frac{9}{14} + \frac{4}{14} = \frac{14}{14} = 1$.

5. The angle $\theta$ between $v$ and $w$ has $\cos\theta = \frac{v \cdot w}{\|v\| \|w\|}$.

6. The angle between $\begin{bmatrix} 1 \\ 0 \end{bmatrix}$ and $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$ has $\cos\theta = \frac{1}{\sqrt{2} \cdot 1} = \frac{1}{\sqrt{2}}$. That angle is $\theta = 45^\circ$.

7. All angles have $|\cos\theta| \le 1$. So all vectors have $|v \cdot w| \le \|v\| \|w\|$ ([[Cauchy–Schwarz inequality]]).
### Inner Product

[[Inner product]], also called **dot product**, of $v = (v_{1}, v_{2})$ and $w = (w_{1}, w_{2})$ is the number $v \cdot w$:
$$v \cdot w = v_{1}w_{1} + v_{2}w_{2}$$

If the **dot product** of two vectors equals **0**, it means that those two vectors are **perpendicular.** The angle between them is 90º. 
$$v \cdot w = w \cdot v$$
##### Example
We have three goods to buy and sell. Their prices are $(p1,p2,p3)$ for each unit-this is the "price **vector**" $p$. The quantities we buy or sell are $(q1,q2,q3)$, positive when we sell, negative when we buy.
Selling $q1$ units at the price $p1$ brings in $q1p1$. The total income (quantities $q$ times prices
$p$) is the dot product $q ·p$ in three dimensions:
$$Income = (qi,q2,q3) · (p1,P2,p3) = q1p1 + q2p2 + q3p3 = \text{dot product}$$
A **zero dot product** means that "the books balance". Total sales equal total purchases if
$q · p = 0$. Then $p$ is perpendicular to $q$ (in three-dimensional space). A supermarket with
thousands of goods goes quickly into high dimensions.

**Important**
For $v · w$, multiply each $v_{i}$ times $w_{i}$. Then $v · w = v_{1} w_{1} + · · · + v_{n}w_{n}$.

### Length

The dot product of a **vector with itself** gives the length squared: $$||v||² = \begin{bmatrix}
1 \\
2 \\
3 \\

\end{bmatrix} \cdot \begin{bmatrix}
1 \\
2 \\
3
\end{bmatrix} = 1 + + 9 = 14$$
Because $v$ is not perpendicular to itself, the answer is not 0.

The **length** $||v||$ of a vector $v$ is the square root of $v \cdot v$:
$$\text{length} = ||v|| = \sqrt{ v \cdot v } = (v_{1}² + v_{2}² + \dots + v_{n}²)^{1/2}$$

### Unit vector

The word "unit" is always indicating that some measurement equals "one". The unit
price is the price for one item. A unit cube has sides of length one. A unit circle is a circle
with radius one. Now we see the meaning of a "unit vector".

$$\text{A unit vector }u \text{ is a vector whose length equals one. Then }u \cdot u = 1$$

**Definition**: $u = v / ||v||$ is a **unit vector in the same direction as $v$**.

### The Angle between two Vectors

Perpendicular vectors have $v \cdot w = 0$. The dot product is 0 **when the angle is 90º**. So:
$$\text{The dot product is } v \cdot w = 0 \text{ when }v \text{ is perpendicular to }w$$
#### Proof
When $v$ and $w$ are perpendicular, they form two sides of a **right triangle**. The **third side** is $v - w$ (the **hypotenuse** of the triangle) The [[Pythagoras Law]] for the sides of a right triangle is $a^2 + b² = c²$:

**Perpendicular vectors**: $||v||² + ||w||² = ||v - w||²$

Writing out the formulas for those lengths in two dimensions, this equation is:
$$(v_{1}² + c_{2}²)+(w_{1}²+w_{2}²)=(v_{1}-w_{1})²+(v_{2}-w_{2})²$$
The right side begins with $v_{1}² - 2v_{1}w_{1} + w_{1}²$. Then, $v_{1}²$ and $w_{1}^2$ are on both sides of the equation and they cancel, leaving $-2v_{1}w_{1}$. Also $v_{2}²$ and $w_{2}^2$ cancel, leaving $-2v_{2}w_{2}$.
Now, divide by $-2$ to see $v - w = 0$:
$$ 0 = -2 v _{1}w_{1} \text{ which leads to } v _{1}w_{1}+v _{2}w_{2} = 0$$

**Conclusion**: Right angles produce $v \cdot w = 0$. The **dot product** is zero when the angle $\theta = 90º$. Then $\cos \theta = 0$. The zero vector $v=0$ is perpendicular to every vector $w$ because $0 \cdot w$ is always zero.

#### Properties

If the **dot product** $v \cdot w = 0$ then the angle is $90º$.

If the dot product is **positive**, then the angle $\theta$ is $\theta < 90$.

If the dot product is **negative**, then the angle $\theta$ is $\theta > 90$.

![[Linear Algebra-1779056249818.png | @darkmode]]
