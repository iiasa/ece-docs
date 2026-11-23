.. _variable-codelist:

The variable codelist
=====================

An entry in a variable codelist **must** be a mapping (or a ``dict`` in Python).
It maps the name of an allowed variable to, at least, one key-value pair defining
the allowed unit(s) for the variable.

This is an example for a valid entry in a variable codelist:

.. code:: yaml

  - Allowed variable name:
      description: A short explanation or definition
      unit: A unit
      <other attribute>: Some text, value, boolean or list

.. note::

  See :ref:`variables` for variable naming conventions and units.

Required and recommended attributes
-----------------------------------

The ``unit`` attribute is **required**. It can be a string for one allowed unit,
a list of strings for multiple allowed units, or empty for a dimensionless variable:

.. code:: yaml

  - Primary Energy:
      description: Total primary energy supply
      unit: EJ/yr
  - Population:
      description: Total population
      unit: [million, billion]
  - Population|Urban [Share]:
      description: Share of the population living in urban areas
      unit:

A ``description`` with an explanation or definition is recommended.

The yaml format allows *any* number of additional arbitrary named attributes.

.. _region-aggregation:

Attributes for region aggregation
---------------------------------

There are several attributes that affect region processing by the |nomenclature|.
See :ref:`model-mappings` for more information.

- By default, variables are processed using :meth:`pyam.IamDataFrame.aggregate_region`,
  which performs a simple summation of all subregions.

- Region aggregation for a particular variable can be skipped by using the attribute
  ``skip-region-aggregation: true``; see this example:
  
  .. code:: yaml

    - Some Variable:
        skip-region-aggregation: true

  Setting ``skip-region-aggregation: true`` skips aggregation for that variable but
  does not remove it from the provided scenario data.
  
- Any attributes which are arguments of :meth:`pyam.IamDataFrame.aggregate_region`
  will be passed to that method. Examples inclide ``method`` and ``weight``.

- The ``weight`` attribute is optional. If provided, this variable will be used
  as a weight for computing the region.aggregation as a weighted average.
  The variable given in the ``weight`` attribute **must** be defined in the codelist.

- It is possible to rename the variable returned by the region processing using
  a ``region-aggregation`` attribute, which must have a mapping of the target variable
  to arguments of :meth:`pyam.IamDataFrame.aggregate_region`.

  This option can be used to compute several variables as part of the region-processing.
  In the example below, the variable ``Price|Carbon`` is computed as a weighted average
  using the CO2 emissions as weights, and in addition, the mean carbon price
  within each aggregate-region is added as a new variable ``Price|Carbon [Mean]``.

.. code:: yaml

  - Price|Carbon:
      unit: USD/t CO2
      region-aggregation:
      - Price|Carbon:
          weight: Emissions|CO2
      - Price|Carbon [Mean]:
          method: mean

Consistency across the variable hierarchy
-----------------------------------------

The nomenclature package supports automated validation across the variable hierarchy,
checking that the components of a variable sum to the category value. This feature
uses :meth:`pyam.IamDataFrame.check_aggregate`.

- To activate the aggregation-check, add ``check-aggregate: true`` as a variable attribute.

- By default, the method uses all sub-categories of the variable name, i.e.
  all variables ``Final Energy|*`` for computing the aggregate of ``Final Energy``.

- You can specify the ``components`` explicitly either as a list of variables or
  as a list of dictionaries to validate along multiple dimensions.

  .. code:: yaml

    - Final Energy:
        definition: Total final energy consumption
        unit: EJ/yr
        check-aggregate: true
        components:
          - By fuel:
            - Final Energy|Gas
            - Final Energy|Electricity
            - ...
          - By sector:
            - Final Energy|Residential
            - Final Energy|Industry
            - ...
    - Final Energy|Industry:
        definition: Final consumption of the industrial sector
        unit: EJ/yr
        check-aggregate: true
        components:
          - Final Energy|Industry|Gas
          - Final Energy|Industry|Electricity

- The method :meth:`DataStructureDefinition.check_aggregate` returns a ``pandas.DataFrame``
  with a comparison of the original value and the computed aggregate for all variables
  that fail the validation.