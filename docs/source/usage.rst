Usage
=====

.. _installation:

Installation
------------

To use spladtool, first install it using pip:

.. code-block:: console

   (.venv) $ pip install spladtool

Live example
----------------

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
>>> w.grad
array([[-4.20404488e+01,  4.27363350e-01],
       [ 4.17169950e-02,  8.86701846e-03]])

