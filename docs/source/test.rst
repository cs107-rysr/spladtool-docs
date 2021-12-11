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

To run given tests, under UNIX environment, use
```bash
sh test.sh
```
Under Windows environment, run
```bash
coverage run test.py
coverage report
```
