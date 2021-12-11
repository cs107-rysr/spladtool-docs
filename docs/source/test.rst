Test Suite
======================

tests
├── test_analytical.py
├── test_backwards_func.py
├── test_basic_ops.py
├──test_basic_ops_reverse.py
├──test_comp_ops.py
├──test_comp_ops_reverse.py
├──test_functional_reverse.py
└──test_optimize.py

We have implemented thorough test suites for our package. The code coverage of our tests achieve 96%.

To run given tests, under UNIX environment, use:

.. code-block:: console

  sh test.sh

Under Windows environment, run:

.. code-block:: console

  coverage run test.py
  
  coverage report






Test Suite
==========


To use spladtool, first install it using pip:To use spladtool, first install it using pip:

.. code-block:: console

   (.venv) $ pip install spladtool

Live example
----------------
For forward mode, try out our 
.. _demo: https://github.com/cs107-rysr/cs107-FinalProject/blob/main/examples/newton.py
about Newton root finder
You can try out our well-implemented demo for polynomial regression
and logistic regression with this .. _jupyter notebook: https://github.com/cs107-rysr/cs107-FinalProject/blob/main/examples/toymodels.ipynb

Forward Mode
-------------------
For forward mode, first import the forward mode module,
and then define your initial variable using numeric value,
``np.ndarray`` or a list. Next, you should execute several
functions using the numpy practice that you are familiar with.

>>> import spladtool.spladtool_forward as sf
>>> x = sf.tensor([[1., 2.], [3., 4.]])
>>> y = 2 * x + 1
>>> z = -y / (x ** 3)
>>> w = sf.cos((sf.exp(z) + sf.exp(-z)) / 2)
>>> w
spladtool.Tensor(
[[-0.80037009  0.36072269]
 [ 0.51156054  0.53194201]]
)
>>> w.grad # should be the derivatives of w w.r.t x
array([[-4.20404488e+01,  4.27363350e-01],
       [ 4.17169950e-02,  8.86701846e-03]])

you can also use ``seed`` parameter to specify the derivative direction.

>>> x = sf.tensor([1., 2.], seed=[1, 0])
>>> y = sf.sin(3 * x + 1)
>>> y.grad
array([-1.96093086,  0.        ])

Reverse Mode
------------------
For reverse mode, the construction of the tensors are the same.
The difference is: the gradient won't be computed until the 
``backward()`` method is called.

Different from the forward mode, 
the gradient here represents the gradient of each variable w.r.t the 
output, instead of the derivatives w.r.t the input.

>>> import spladtool.spladtool_reverse as sr
>>> x = sr.tensor([[1, 2], [3, 4]])
>>> y = sr.cos(3 * (x ** 2) + 4 * x + 1)
>>> z = y.mean()
>>> z
spladtool_reverse.Tensor(-0.48065530173082893)
>>> z.backward()
>>> z.grad
array(1.)
>>> y.grad
array([[0.25, 0.25],
       [0.25, 0.25]])
>>> x.grad
array([[-2.47339562, -3.34662255],
       [-4.09812238, -5.78780076]])
