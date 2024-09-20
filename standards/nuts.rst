.. _nuts:

NUTS classification
===================

The :py:mod:`nomenclature` (`read the docs`_) package makes use of the :py:mod:`pysquirrel` package
(:ref:`more information here <pysquirrel>`) to provide a utility for region
names based on the `NUTS classification <https://ec.europa.eu/eurostat/web/nuts>`_. 

This feature allows users to easily import the NUTS regions which are territorial units with 
multiple levels of resolution, adding functionality to facilitate scenario 
analysis and model comparison.

The full list of NUTS regions is accessible in Eurostat's `Excel file`_.

.. code:: python

  from nomenclature import nuts

  # list of NUTS region codes
  nuts.codes
  
  # list of NUTS region names
  nuts.names

.. _`read the docs`: https://nomenclature-iamc.readthedocs.io/en/stable/

.. _GitHub: https://github.com/IAMconsortium/nomenclature/blob/main/nomenclature/countries.py

.. _`Excel file`: https://ec.europa.eu/eurostat/documents/345175/629341/NUTS2021-NUTS2024.xlsx