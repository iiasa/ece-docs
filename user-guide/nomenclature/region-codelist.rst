.. _region-codelist:

The region codelist
===================

Region format specification
---------------------------

Each region **must** be part of a hierarchy, which means that the following nested
list structure is required in YAML files in the ``definitions/region`` directory:

.. code:: yaml

   - Hierarchy 1:
     - Region 1:
         description: Some short explanation
         countries: [Country 1, Country 2, ...]
     - Region 2:
         description: Some short explanation
   - Hierarchy 2:
     - ...

Regions can have attributes, for example a description or a list of countries comprised
in that region. If the ``countries`` attribute is provided, the entries are validated
against the supported country names. More details on the list of countries can be found
in :ref:`countries`.

Naming conventions for native model regions
-------------------------------------------

Models with a coarse spatial resolution should add a model-specific *prefix* to
the native model regions to avoid confusion when comparing results to other models
with similar-but-different regions:

.. code:: yaml

   - Model A v1.0:
     - Model A v1.0|Region 1:
         description: Some short explanation
     - Model A v1.0|Region 2

The renaming from (short) region names as reported by a modelling framework to
more verbose region names for use in model-comparison projects can be implemented
by the :ref:`model-mappings`. See :ref:`regions` for the naming conventions.

Connections between regions
---------------------------

For reporting of connections (e.g., trade flows), "directional regions" can be
defined using a ``>`` separator. The region before the separator is the *origin*,
the region after the separator is the *destination*.

.. code:: yaml

   - Trade Connections:
     - China>Europe

.. code:: yaml

   - Model A v1.0 [Connection]:
     - Model A v1.0|Region 1>Region 2

For model-specific directional connections, the *prefix* must be added as well.
For example, ``Model A v1.0|Region 1>Region 2`` describes a connection between
``Model A v1.0|Region 1`` and ``Model A v1.0|Region 2``. Both origin and destination
must be defined in the region codelist.

.. warning::

    Region prefixes other than model names are *not* recommended! Instead, sub-divisions
    of regions (e.g., states within a country) should be defined as distinct
    region-hierarchies. This is because using country-names as region-prefixes can cause
    confusion when defining connections between regions.
