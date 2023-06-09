****************************************
Drill-Bits: Handy tools for ML in Python
****************************************

.. image:: https://img.shields.io/pypi/v/drill-bits.svg
   :target: https://pypi.python.org/pypi/drill-bits/
.. image:: https://img.shields.io/travis/com/jiujiuche/drill-bits
   :target: https://app.travis-ci.com/github/JiuJiuChe/drill-bits
.. image:: https://img.shields.io/github/languages/top/jiujiuche/drill-bits
   :target: https://github.com/JiuJiuChe/drill-bits
.. image:: https://img.shields.io/codecov/c/github/jiujiuche/drill-bits
    :target: https://app.codecov.io/gh/JiuJiuChe/drill-bits
.. image:: https://img.shields.io/github/license/jiujiuche/drill-bits
   :target: https://github.com/JiuJiuChe/drill-bits
.. image:: https://img.shields.io/github/last-commit/jiujiuche/drill-bits
   :target: https://github.com/JiuJiuChe/drill-bits

Install
#######
.. code-block:: bash

    pip install drill-bits
    
    
Examples
########
**All type read & write:**

.. code-block:: python

    from drill-bits.io import io_utils
    data = io_utils.omni_load(file_name)
    io_utils.omni_save(file_name, data)

Currently supported extensions including: `.npy`, `.txt`, `.pkl`, `.jpg`, `.png`.

**Extract digit information from str:**

.. code-block:: python
	
	from drill_bits.io import str_utils

    test_str = 'img1_h102_w103.img'
    resolution = str_utils.extract_info(test_str, ['h', 'w'], int)
    # resolution will be [102, 103]

**A decorator saves you from reprocessing:**

.. code-block:: python
	
    import time
	from drill_bits.operation import base_operation
    
    def foo(n):
    	time.sleep(1)
        if n == 1:
        	return 1
        else:
    		return n * foo(n-1)

    opt = BaseOperation(path).get_handle(force_run=False, verbose=True)
    foo_warp = opt(foo)
    print(foo_warp(5))      # it will take 5s to run
    print(foo_warp(5))      # it will finish immediately 
    opt = BaseOperation(path).get_handle(force_run=True, verbose=True)
    foo_warp = opt(foo)
    print(foo_warp(5))      # it will take 5s to run again
