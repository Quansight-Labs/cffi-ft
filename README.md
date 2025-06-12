[![GitHub Actions Status](https://github.com/python-cffi/cffi/actions/workflows/ci.yaml/badge.svg?branch=main)](https://github.com/python-cffi/cffi/actions/workflows/ci.yaml?query=branch%3Amain++)
[![PyPI version](https://img.shields.io/pypi/v/cffi.svg)](https://pypi.org/project/cffi)
[![Read the Docs](https://img.shields.io/badge/docs-latest-blue.svg)][Documentation]


CFFI-ft
=======

Foreign Function Interface for Python calling C code.

## Why a fork?

This is a fork of the CFFI project that adds support for free-threaded Python.
Our intention is to upstream the changes in our fork but we are publishing this
version to enable widespread real-world testing.

### How to depend on CFFI-ft

If your project depends on CFFI and you would like to publish free-threaded
wheels or experiment with the free-threaded build, you can add a dependency on
the `cffi-ft` on Python 3.13 and newer. For example, in a `pyproject.toml` file:

```toml
dependencies = [
    ...,
    "cffi; python_version<'3.13'",
    "cfft-ft; python_version>='3.13'",
]
```

Or in a `requirements.txt` file:

```
...
cffi python_version < '3.13'"
cfft-ft; python_version > ='3.13'
...
```

### Different module name

CFFI-ft uses a different module name (`cffi_ft`) than upstream CFFI on purpose:
so that both can be installed in the same environment.

To most easily use either library depending on which is available, you can
import `cffi` like this:

```
try:
    import cffi_ft as cffi
except ImportError:
    import cffi
```

This will import `cffi_ft` if it's available and use upstream CFFI otherwise.

Please see the [Documentation] or uncompiled in the `doc/` subdirectory. Note
that we have not modified the imports in the documentation.

Download
--------

[Download page](https://github.com/python-cffi/cffi/releases)

Source Code
-----------

Source code is publicly available on
[GitHub](https://github.com/python-cffi/cffi).

Contact
-------

[Mailing list](https://groups.google.com/forum/#!forum/python-cffi)

Testing/development tips
------------------------

After `git clone` or `wget && tar`, we will get a directory called `cffi` or `cffi-x.x.x`. we call it `repo-directory`. To run tests under CPython, run the following in the `repo-directory`:

    pip install pytest
    pip install -e .  # editable install of CFFI for local development
    pytest src/c/ testing/

[Documentation]: http://cffi.readthedocs.org/
