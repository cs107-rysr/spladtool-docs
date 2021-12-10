Development Designs
====================

Data Structures
-----------------
- Tensor
        The core data structure here is the `Tensor`, which contains the value (that will be represented by a ``numpy.ndarray``) and gradient. 

        In the reverse mode, we need two more attributes or member variables to keep record of the graph dependency: `Tensor.dependency` tracks the dependent tensor and `Tensor.layer` will store the layer or the operation used to attain this tensor. We will explain further how they are used. In the reverse mode, we also add a member function called `Tensor.backward()`, which will automatically call the `backward` method of ``Tensor.layer`` with arguments being ``Tensor.dependency`` to achieve reverse propagation.

- Layer
    A layer is defined as a basic operations, i.e. sum, product, division, sine function, etc.

    All layer classes inherit from a base class called ``Layer``. For the forward mode, the member function `Layer.forward()` computes the evaluation and gradients altogether. In the reverse mode, `Layer.forward()` will only handle the evaluation, while ``Layer.reverse()`` will handle the gradients computation.

- Functional APIs
    We wrap up our implementations of operations in functional APIs. We also add dunders or magic functions to ``Tensor`` class so that basic operators can be used on them.

- Supported Operations
    - Basic Operations: Add, Substract, Power, Negation, Product, Division
    - Analytical functions: trignomical, exponential, logarithm, hyperbolic trignomical, inverse trignomical
    - Comparators
    - Mean, Sum
    - Logistic
    - Loss functions: mean squared error(MSE), binary cross entropy(BCE)

- Python Typing
    To make sure the type is  correct, we add python typing to each of the operation classes and functional APIs to make sure the library will raise proper exceptions when encountered with unsupported operations.
