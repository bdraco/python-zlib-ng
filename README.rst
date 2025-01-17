.. image:: https://img.shields.io/pypi/v/zlib-ng.svg
  :target: https://pypi.org/project/zlib-ng/
  :alt:

.. image:: https://img.shields.io/conda/v/conda-forge/python-zlib-ng.svg
  :target: https://github.com/conda-forge/python-zlib-ng-feedstock
  :alt:

.. image:: https://img.shields.io/pypi/pyversions/zlib-ng.svg
  :target: https://pypi.org/project/zlib-ng/
  :alt:

.. image:: https://img.shields.io/pypi/l/zlib-ng.svg
  :target: https://github.com/pycompression/python-zlib-ng/blob/main/LICENSE
  :alt:

.. image:: https://img.shields.io/conda/pn/conda-forge/python-zlib-ng.svg
  :target: https://github.com/conda-forge/python-zlib-ng-feedstock
  :alt:

.. image:: https://github.com/pycompression/python-zlib-ng//actions/workflows/ci.yml/badge.svg
  :target: https://github.com/pycompression/python-zlib-ng/actions
  :alt:

.. image:: https://codecov.io/gh/pycompression/python-zlib-ng/branch/develop/graph/badge.svg
  :target: https://codecov.io/gh/pycompression/python-zlib-ng
  :alt:

.. image:: https://readthedocs.org/projects/python-zlib-ng/badge
   :target: https://python-zlib-ng.readthedocs.io
   :alt:


python-zlib-ng
==============

.. introduction start

Faster zlib and gzip compatible compression and decompression
by providing Python bindings for the zlib-ng library.

This package provides Python bindings for the `zlib-ng
<https://github.com/zlib-ng/zlib-ng>`_ library.

``python-zlib-ng`` provides the bindings by offering two modules:

+ ``zlib_ng``: A drop-in replacement for the zlib module that uses zlib-ng to
  accelerate its performance.

+ ``gzip_ng``: A drop-in replacement for the gzip module that uses ``zlib_ng``
  instead of ``zlib`` to perform its compression and checksum tasks, which
  improves performance.

``zlib_ng`` and ``gzip_ng`` are almost fully compatible with ``zlib`` and
``gzip`` from the Python standard library. There are some minor differences
see: differences-with-zlib-and-gzip-modules_.

.. introduction end

Quickstart
----------

.. quickstart start

The python-zlib-ng modules can be imported as follows

.. code-block:: python

    from zlib_ng import zlib_ng
    from zlib_ng import gzip_ng

``zlib_ng`` and ``gzip_ng`` are meant to be used as drop in replacements so
their api and functions are the same as the stdlib's modules.

A full API documentation can be found on `our readthedocs page
<https://python-zlib-ng.readthedocs.io>`_.

``python -m zlib_ng.gzip_ng`` implements a fully featured gzip-like command line
application (just like ``python -m gzip``, but better). Full usage documentation can be
found on `our readthedocs page <https://python-zlib-ng.readthedocs.io>`_.


.. quickstart end

Installation
------------
- with pip: ``pip install zlib-ng``
- with conda: ``conda install python-zlib-ng``

Installation is supported on Linux, Windows and MacOS. For more advanced
installation options check the `documentation
<https://python-zlib-ng.readthedocs.io/en/stable/index.html#installation>`_.

python-zlib-ng as a dependency in your project
----------------------------------------------

.. dependency start

zlib-ng supports numerous platforms but not all of these have pre-built wheels
available. To prevent your users from running into issues when installing
your project please list a python-zlib-ng dependency as follows.

``setup.cfg``::

    install_requires =
        zlib-ng; platform.machine == "x86_64" or platform.machine == "AMD64"

``setup.py``::

    extras_require={
        ":platform.machine == 'x86_64' or platform.machine == 'AMD64'": ['zlib-ng']
    },

.. dependency end

.. _differences-with-zlib-and-gzip-modules:

Differences with zlib and gzip modules
--------------------------------------

.. differences start

+ Compression level 1 zlib_ng has a worse compression rate than that in
  zlib. For other compression levels zlib_ng compresses better.
+ ``gzip_ng.open`` returns a class ``GzipNGFile`` instead of ``GzipFile``. Since
  there are differences between the compressed ratios between levels, a
  difference in naming was chosen to reflect this.
  ``gzip_ng.GzipFile`` does exist as an alias of
  ``gzip_ng.GzipNGFile`` for compatibility reasons.

.. differences end

Contributing
------------
.. contributing start

Please make a PR or issue if you feel anything can be improved. Bug reports
are also very welcome. Please report them on the `github issue tracker
<https://github.com/rhpvorderman/python-zlib-ng/issues>`_.

.. contributing end

Acknowledgements
----------------

.. acknowledgements start

This project builds upon the software and experience of many.  Many thanks to:

+ The `zlib-ng contributors
  <https://github.com/zlib-ng/zlib-ng/graphs/contributors>`_ for making the
  zlib-ng library.
+ The `CPython contributors
  <https://github.com/python/cpython/graphs/contributors>`_.
  Python-zlib-ng mimicks ``zlibmodule.c`` and ``gzip.py`` from the standard
  library to make it easier for python users to adopt it.
+ The `github actions team <https://github.com/orgs/actions/people>`_ for
  creating the actions CI service that enables building and testing on all
  three major operating systems.

.. acknowledgements end
