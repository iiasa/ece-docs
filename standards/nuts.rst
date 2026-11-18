.. _nuts:

NUTS classification
===================

The |nomenclature| uses the :py:mod:`pysquirrel` package
(:ref:`more information here <pysquirrel>`) to provide a utility suite for region names
based on the `NUTS classification`_. These are territorial units for Europe including
multiple levels of resolution depending on the required level of detail.

The package allows users to easily import the NUTS regions into a project workflow. It
also provides functionality to facilitate scenario analysis and model comparison.

The full list of NUTS regions is accessible via Eurostat's `Excel file`_ or via
the package API (see below).

The |SCSE team| also provides geojson files of the NUTS regions via a dedicated
`scse-geojson <https://github.com/iiasa/scse-geojson>`_ repository.

.. code:: python

  from nomenclature import nuts

  # Get list of NUTS region codes
  ### this does't work, please double-check!
  nuts.codes
  
  # Get list of NUTS region names
  ### this does't work, please double-check!
  nuts.names

.. _`NUTS classification`: https://ec.europa.eu/eurostat/web/nuts

.. _GitHub: https://github.com/IAMconsortium/nomenclature/blob/main/nomenclature/countries.py

.. _`Excel file`: https://ec.europa.eu/eurostat/documents/345175/629341/NUTS2021-NUTS2024.xlsx
