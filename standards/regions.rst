.. _regions:

Common and native regions
=========================

Common regions
--------------

In model-comparison projects, it is useful to define **common regions** that can be
computed consistently from original model results.

A widely used example are the `R5, R9 and R10 regions`_.

.. _`R5, R9 and R10 regions`: https://github.com/IAMconsortium/common-definitions/blob/main/definitions/region/common.yaml

Native model regions
--------------------

In contrast to common regions used for comparison of scenarios across models,
each model has a **native region** resolution.

Models with a coarse spatial resolution should add a model-specific identifier to the
native model regions (e.g., `MESSAGEix-GLOBIOM 1.1|North America`) to avoid confusion
when comparing results to other models with similar-but-different regions.

If a model has a country-level resolution (where disambiguation is not a concern),
we recommend to *not add* a model identifier. Instead, use the naming convention
following the common list of countries (see :ref:`countries`).

.. _region_codelist:

Region format specification
---------------------------

Each region **must** be part of a hierarchy, which means that the following nested
list structure is required:

.. code:: yaml

   - Hierarchy 1:
     - Region 1:
         description: Some short explanation
         countries: [Country 1, Country 2, ...]
     - Region 2:
         description: Some short explanation
         iso3_codes: ABC
   - Hierarchy 2:
     - ...

Regions can have attributes, for example a description, a list of countries, or ISO3 codes.
If the attributes `countries` and/or `iso3_codes` are provided, the item(s) are 
validated against a list of valid ISO3 country names/codes adapted from the
`pycountry <https://github.com/flyingcircusio/pycountry>`_ package.
More details on the list of countries can be found :ref:`here <countries>`.
