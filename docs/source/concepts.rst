Concepts in our library
==========================

In our library, we consider the differentiation for high-dimensional tensors.
Every tensor can be represented as a n-dimensional real-valued array.
Each tensor also possesses a gradient, which is as the identical shape as the tensor itself,
representing the negative descent direction in gradient-based optimization.

Jacobian Matrix and Gradients
-------------------------------
Jacobian Matrix is an important concept in vector calculus, and it also helps us to understand the calculations in the automatic differentiation. Given a mapping $h: \mathbb{R}^n \to \mathbb{R}^m$, the Jacobian matrix of h is as follows:

$$
J  =  {\begin{bmatrix}{\dfrac {\partial h_1}{\partial x_1}}&\cdots &{\dfrac {\partial h_{1}}{\partial x_{n}}}\\\vdots &\ddots &\vdots \\{\dfrac {\partial h_{m}}{\partial x_{1}}}&\cdots &{\dfrac {\partial h_{m}}{\partial x_{n}}}\end{bmatrix}}
$$
