# Sigmoid Function

The sigmoid function is the **activation** function used in [[Supervised Learning#Logistic Regression|logistic regression]] to transform a **linear combination of inputs** into a **probability between 0 and 1**. First, the model computes a **weighted sum** of the features plus a bias term, often written as $z = w^T x + b$. This value $z$ can be **any real number**, positive or negative. The sigmoid function then **maps** that number into the range $(0,1),$ making it interpretable as the **probability** that the input belongs to class 1.

The **shape** of the sigmoid curve is S-shaped. When $z$ is a **large positive number**, the output gets very close to 1; when $z$ is a **large negative number**, the output gets very close to $0$; and when $z=0$, the output is exactly 0.5. This **smooth behavior** allows logistic regression to model probabilities in a **differentiable** way, which is essential for optimization using gradient descent and for computing the cross-entropy loss during training.

$$
\hat{y} = \sigma(z) = \frac{1}{1 + e^{-z}}
$$

$$
z = w_1x_1 + w_2x_2 + \dots + w_Mx_M + b
$$