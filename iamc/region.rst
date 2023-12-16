The *region* column
===================

Common regions
--------------

In model-comparison projects, it is useful to define *common regions* that can be
computed consistently from original model results. Widely used examples are the
`R5, R9 and R10 regions`_.

.. _`R5, R9 and R10 regions`: https://github.com/IAMconsortium/common-definitions/blob/main/definitions/region/common.yaml

Naming conventions for native model regions
-------------------------------------------

In contrast to common regions used for comparison or scenario analysis across models,
each model has a "native region" resolution.

Models with a coarse spatial resolution should add a model-specific identifier to the
native model regions (e.g., `MESSAGEix-GLOBIOM 1.1|North America`) to avoid confusion
when comparing results to other models with similar-but-different regions.

If a model has a country-level resolution (where disambiguation is not a concern),
we recommend to *not add* a model identifier.

For country-level regional resolution, the :class:`nomenclature` package provides
a standardized list of `country names`_ based on the :class:`pycountry` package
(`link <https://github.com/flyingcircusio/pycountry>`_) and the ISO 3166-1 standard.

.. _`country names` : https://nomenclature-iamc.readthedocs.io/en/stable/api/countries.html
