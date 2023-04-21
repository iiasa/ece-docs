# An overview page for software documentation 

Copyright (c) 2023 IIASA; published under the [MIT License](LICENSE)

![License](https://img.shields.io/github/license/iiasa/python-stub)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

This is a [Sphinx](http://sphinx-doc.org/) project for a landing page of 
software project documentation developed by the Energy, Climate, and Environment Program (ECE).
The website is deployed at https://docs.ece.iiasa.ac.at/ hosted by ReadTheDocs.

## Installation

Install the package including the requirements for building the docs.

    pip install --editable .[doc]

## Building the docs

Run Sphinx to build the docs!

    make html

The rendered html pages will be located in `_build/index.html`.
