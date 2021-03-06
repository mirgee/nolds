NOnLinear measures for Dynamical Systems (nolds)
================================================

Nolds is a small numpy-based library that provides an implementation and a learning resource for nonlinear measures for dynamical systems based on one-dimensional time series.
Currently the following measures are implemented:

**sample entropy** (``sampen``)
  Measures the complexity of a time-series, based on approximate entropy
**correlation dimension** (``corr_dim``)
  A measure of the *fractal dimension* of a time series which is also related to complexity.
**Lyapunov exponent** (``lyap_r``, ``lyap_e``)
  Positive Lyapunov exponents indicate chaos and unpredictability.
  Nolds provides the algorithm of Rosenstein et al. (``lyap_r``) to estimate the largest Lyapunov exponent and the algorithm of Eckmann et al. (``lyap_e``) to estimate the whole spectrum of Lyapunov exponents.
**Hurst exponent** (``hurst_rs``)
	The hurst exponent is a measure of the "long-term memory" of a time series.
	It can be used to determine whether the time series is more, less, or equally likely to increase if it has increased in previous steps.
	This property makes the Hurst exponent especially interesting for the analysis of stock data.
**detrended fluctuation analysis (DFA)** (``dfa``)
	DFA measures the Hurst parameter *H*, which is very similar to the Hurst exponent.
	The main difference is that DFA can be used for non-stationary processes (whose mean and/or variance change over time).

Example
-------

::

	import nolds
	import numpy as np

	rwalk = np.cumsum(np.random.random(1000))
	h = nolds.dfa(rwalk)

Requirements
------------
Nolds supports Python 2 (>= 2.7) and 3 (>= 3.4) from one code source. It requires the package numpy_.

These are the only hard requirements, but some functions will need other packages:

* If you want to use the RANSAC algorithm for line fitting, you will also need the package sklearn_.
* For the true random numbers generated by ``nolds.qrandom`` you need the package quantumrandom_.
* The plotting functions in ``nolds.examples`` require the package matplotlib_.

.. _numpy: http://numpy.scipy.org/
.. _sklearn: http://scikit-learn.org/stable/
.. _quantumrandom: https://pypi.python.org/pypi/quantumrandom/1.9.0
.. _matplotlib: https://matplotlib.org/

Installation
------------
Nolds is available through PyPI and can be installed using pip:

``pip install nolds``

You can test your installation by running some sample code with:

``python -m nolds.examples lyapunov-logistic``

Alternatively, if you do not have matplotlib_ installed, you can run the unittests with:

``python -m unittest nolds.test_measures``

Documentation
-------------

Nolds is designed as a learning resource for the measures mentioned above.
Therefore the corresponding functions feature extensive documentation that not only explains the interface but also the algorithm used and points the user to additional reference code and papers.
The documentation can be found in the code, but it is also available as `HTML-Version <https://cschoel.github.io/nolds/>`_ and on `Read the Docs <http://nolds.readthedocs.io/>`_.

The relevant measures can be found in the file ``nolds/measures.py``.


Contact information
-------------------

If you have any questions, suggestions or corrections, you can find my contact
information on my blog_.

.. _blog: http://arbitrary-but-fixed.net/
