.. _regions:

Native and common regions
=========================

Native model regions
--------------------

Each model has a **native region** resolution.

Models with a coarse spatial resolution should add a model-specific identifier to the
native model regions (e.g., `MESSAGEix-GLOBIOM 1.1|North America`) to avoid confusion
when comparing results to other models with similar-but-different regions.

If a model has a country-level resolution (where disambiguation is not a concern),
we recommend to *not add* a model identifier. Instead, use the naming convention
following the common list of countries (see :ref:`countries`).

Common regions
--------------

In model-comparison projects, it is useful to define **common regions** that can be
computed consistently from original model results to compare scenarios.

A widely used example are the `R5, R9 and R10 regions`_.

.. _`R5, R9 and R10 regions`: https://github.com/IAMconsortium/common-definitions/blob/main/definitions/region/common.yaml

Computing aggregated data
`````````````````````````

The `**nomenclature** <https://nomenclature-iamc.readthedocs.io>`_ package includes
a user guide on how to setup instructions for region aggregation.
This enables reporting data at a model's native regional resolution, and then
aggregating the data to the selected common regions.
This instruction-based aggregation can be run locally on IAMC data files, and is also
integrated in project workflows for uploading data to Scenario Explorer instances.

To learn more about how nomenclature enables region aggregation, please see our
guide on `Region processing using model mappings`_ and the `RegionProcessor`_.

.. _`Region processing using model mappings`: <https://nomenclature-iamc.readthedocs.io/en/stable/user_guide/model-mapping.html>

.. _`RegionProcessor`: <https://nomenclature-iamc.readthedocs.io/en/stable/api/regionprocessor.html>_`
