Concepts in our library
==========================

In our library, we consider the differentiation for high-dimensional tensors.
Every tensor can be represented as a n-dimensional real-valued array.
Each tensor also possesses a gradient, which is as the identical shape as the tensor itself,
representing the negative descent direction in gradient-based optimization.

Jacobian Matrix and Gradients
-------------------------------
Jacobian Matrix is an important concept in vector calculus. 
Suppose there is a m-dimensional vector y, 
and an n-dimensional vector x, and there exists a 
multi-variable mapping x to y, the Jacobian the y regarding x 
would be a mxn matrix, where the element at i-th row and j-th column 
represents the scalar derivative of y[i] w.r.t x[j]

If we extend the concept of Jacobian to broader tensor calculus,
we should still compute the scalar derivative to lay the foundation
for tensor differentiation. But do we really need that much?

Consider the negative descent direction for $y$, or the gradient for $y$. 
The concept of gradient is used in multi-variable calculus, 
where the output is a scalar value. In the desired application, 
namely optimization, the final optimization target is usually a scalar. 
(Except in cases like Paleto Optimal).
Suppose both x and y are intermediate variables.
Then y would have a gradient w.r.t the final objective. 
What our library aims to do is to compute the gradient of x w.r.t that final objective.

