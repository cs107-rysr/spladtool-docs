Test Suite
======================

We have implemented thorough test suites for all methods in our package using unittest as our testing framework. 

 * test_analytical.py.
 * test_backwards_func.py
 * test_basic_ops.py
 * test_basic_ops_reverse.py
 * test_comp_ops.py
 * test_comp_ops_reverse.py
 * test_functional_reverse.py
 * test_optimize.py

The code coverage of our tests achieves 96%.

To run given tests, first install pytorch, to which we are comparing our results, and under UNIX environment, type:

.. code-block:: console

  sh test.sh

Under Windows environment, run:

.. code-block:: console

  coverage run test.py
  
  coverage report
