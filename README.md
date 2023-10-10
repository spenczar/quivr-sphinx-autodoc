# quivr-sphinx-autodoc

This is a Sphinx extension for autodoc of Quivr Tables. 

## Installation

Install with pip:

```console
pip install quivr-sphinx-autodoc
```

Then enable by adding to the sphinx extensions in your `conf.py` sphinx configuration file:

```py
extensions = [
    "sphinx.ext.autodoc",
	"quivr_sphinx_autodoc",
]
```

## Usage

Once installed, documentation for `quivr.Table` subclasses will
include tables which list the columnar schema and any scalar
attributes.

This will automatically be enabled for any class declarations found
with a `.. automod::` directive.

If you're manually specifying classes, use `.. autoqvtable:: <tablename>`:

```rst
.. currentmodule:: adam_core.coordinates

.. autoqvtable:: CartesianCoordinates
  :members:
```

To add documentation for table columns or attributes, use the
attribute docstring syntax, which is to lead with `#:`:

```py
class MyTable(qv.Table):
    x = qv.Float64Column()
    
    #: Example of a documented y field
    y = qv.Int64Column()
    
    #: this one is documented
    #: on multiple lines
    #: and has inline ReST text, which works
    #: 
    #: .. warning::
    #:    Do not use
    z = qv.ListColumn(pa.int32())
```
