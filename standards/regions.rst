.. _regions:

Native and common regions
=========================

Native model regions
--------------------

The **native region** resolution is the list of regions that are explicitly represented in a model.

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

Computing regional aggregates
`````````````````````````````

The `**nomenclature** <https://nomenclature-iamc.readthedocs.io>`_ package includes
a user guide on how to setup instructions for region aggregation.
This enables reporting data at a model's native regional resolution, and then
aggregating the data to the selected common regions.
This instruction-based aggregation can be run locally on IAMC data files, and is also
integrated in project workflows for uploading data to Scenario Explorer instances.

To learn more about region aggregation using **nomenclature**, please see our user
guide on :ref:`model-mappings` and the package API documentation for the `RegionProcessor`_.

.. _`RegionProcessor`: <https://nomenclature-iamc.readthedocs.io/en/stable/api/regionprocessor.html>_`

Region attributes
-----------------

Regions can have attributes, for example a description, a list of countries, or ISO3 codes.
If the attributes `countries` and/or `iso3_codes` are provided, the item(s) are 
validated against a list of valid ISO3 country names/codes adapted from the
`pycountry <https://github.com/flyingcircusio/pycountry>`_ package.
More details on the list of countries can be found :ref:`here <countries>`.

Naming conventions for native model regions
-------------------------------------------

In contrast to common regions used for comparison or scenario analysis across models,
each model has a "native region" resolution.

Models with a coarse spatial resolution should add a model-specific *prefix* to
the native model regions (e.g., `MESSAGEix-GLOBIOM 1.1|North America`) to avoid
confusion when comparing results to other models with similar-but-different regions.

.. code:: yaml

   - Model A v1.0:
     - Model A v1.0|Region 1:
         description: Some short explanation

The renaming from (short) region names as reported by a modelling framework to
more verbose region names for use in model-comparison projects can be implemented
by the :ref:`model-mappings`.

If a model has a country-level resolution where disambiguation is not a concern,
we recommend to *not add* a model identifier.

Connections between regions
---------------------------

For reporting of connections (e.g., trade flows), "directional regions" can be
defined using a *>* separator. The region before the separator is the *origin*,
the region after the separator is the *destination*.

.. code:: yaml

   - Trade Connections:
     - China>Europe

Both the *origin* and *destination* regions must be defined in the region codelist.

For model-specific directional connections, the *prefix* must be added as well.

.. code:: yaml

   - Model A v1.0 [Connection]:
     - Model A v1.0|Region 1>Region 2

Both origin and destination `Model A v1.0|Region 1` and `Model A v1.0|Region 2` must be
defined in the region codelist.

Region prefixes other than model names are *not* advised. For example,
:code:`Country A|Region 1` should not be used in a connection with :code:`Country B`,
as :code:`Country A|Region 1>Country B` would resolve the destination as
:code:`Country A|Country B`.
