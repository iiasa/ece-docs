.. _regions:

Native and common regions
=========================

.. note::

   For examples for defining regions in :class:`nomenclature`, see the
   :ref:`region codelist guide <region-codelist>`.

Native model regions
--------------------

The **native region** resolution is the list of regions that are explicitly represented
in a model.

Models with a coarse spatial resolution should add a model-specific identifier to the
native model regions (e.g., ``MESSAGEix-GLOBIOM 1.1|North America``) to avoid confusion
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

The |nomenclature| can aggregate results reported at a model's native regional
resolution into common regions. This can be run locally on IAMC data files and is
also integrated into project workflows for submissions to a Scenario Explorer.

For instructions, see the guide to :ref:`model-mappings` and the `RegionProcessor
<https://nomenclature-iamc.readthedocs.io/en/stable/api/regionprocessor.html>`_
API documentation.

Connections between regions
---------------------------

For reporting of connections (e.g., trade flows), "directional regions" can be
defined using a ``>`` separator. The region before the separator is the *origin*,
the region after the separator is the *destination*.

For example, ``China>Europe`` describes a connection from China to Europe.
