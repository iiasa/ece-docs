.. _regions:

Regions in model-comparison projects
====================================

Common regions
--------------

In model-comparison projects, it is useful to define **common regions** that can be
computed consistently from original model results.

A widely used example are the `R5, R9 and R10 regions`_.

.. _`R5, R9 and R10 regions`: https://github.com/IAMconsortium/common-definitions/blob/main/definitions/region/common.yaml

Naming conventions for model regions
------------------------------------

In contrast to common regions used for comparison of scenarios across models,
each model has a **native region** resolution.

Models with a coarse spatial resolution should add a model-specific identifier to the
native model regions (e.g., `MESSAGEix-GLOBIOM 1.1|North America`) to avoid confusion
when comparing results to other models with similar-but-different regions.

If a model has a country-level resolution (where disambiguation is not a concern),
we recommend to *not add* a model identifier. Instead, use the naming convention
following the common list of countries (see :ref:`countries`).
