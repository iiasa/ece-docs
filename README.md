# Documentation of data formats and software packages 

Copyright (c) 2023-2024 IIASA; released under the
<a href="http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">
  Creative Commons CC0 1.0 License
  <img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/zero.svg?ref=chooser-v1">
</a>

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

This is a [Sphinx](http://sphinx-doc.org/) project for documentation of the IAMC timeseries format
and for software projects developed by the Energy, Climate, and Environment Program (ECE).
The website is deployed at https://docs.ece.iiasa.ac.at/ hosted by ReadTheDocs.

## Building the docs

Install the requirements for building the docs.

    pip install -r requirements.txt

Run Sphinx to build the docs!

    make html

The rendered html pages will be located in `_build/index.html`.

## Style guide

The documentation pages use reStructuredText:

- Use literal markup for IAMC names, YAML keys and values, file paths, and codes,
  e.g., ``` ``Primary Energy`` ```, ``` ``description`` ```, and
  ``` ``definitions/variable`` ```.
- Use Sphinx roles for documented Python objects and `:ref:` for links to other
  sections; use descriptive labels for cross-references. For example,
  `` :meth:`pyam.IamDataFrame.aggregate_region` ``, `` :ref:`model-mappings` ``
  and ``` :class:`nomenclature` ```.
- Use `.. code:: yaml` or another language-specific directive for code examples:

  ```rst
  .. code:: yaml

    unit: EJ/yr
  ```

- Use `.. note::` and `.. tip::` for additional guidance, and `.. warning::`
  for important caveats:

  ```rst
  .. note::

    A variable can have more than one allowed unit.

  .. warning::

    Check that the units in the data match the codelist.
  ```

- Use `=` underlines for page titles, `-` for sections, and backticks for subsections.
  Leave blank lines around directives, lists, and headings:

  ~~~rst
  Page title
  ==========

  Section
  -------

  Subsection
  ``````````
  ~~~
