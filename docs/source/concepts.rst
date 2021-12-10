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

Instead of thinking about the Jacobian, consider **the negative descent direction** for y, 
or the **gradient** for y. 

The concept of gradient is used in multi-variable calculus, 
where the output is a scalar value. In the desired application, 
namely optimization, the final optimization target is usually a scalar. 
(Except in cases like Paleto Optimal).

Suppose both x and y are intermediate variables.
Then y would have a gradient w.r.t the final objective. 
What our library aims to do is to compute the gradient of x w.r.t that final objective.


Forward Mode
--------------

Forward mode is a very simple pipeline to perform auto-differentiation.
We defined several *layers* which are element-wise tensor functions.
When these layers are called upon tensors, 
the function evaluation and the gradient will be computed together.

In this case, the gradient concept would simply be the element-wise
derivatives. (Consider the Jacobian, it is now a diagonal matrix).

Reverse Mode
----------------

Reverse mode is more complicated, but also closer to what is 
provided in PyTorch.

There is a forward pass phase and a backward pass phase
in our implementation.
During the forward pass phase, the variable evaluations
are computed.
Now let's think about how the backward pass works.

Suppose the final output is a scalar. When the backward pass
initiates, we will compute each variable's gradient
w.r.t the output scalar.

The output itself has a gradient of 1, and all its 
dependent variables are assigned a gradient recursively
by the chain rule.

If the final output is a tensor, in our implementation, we assume
each single scalar item has a gradient of 1, 
yielding the output itself having a gradient of all-one tensor.
Then the chain rule still works!

