.. _variable:

Variables in the IAMC format
============================

The 'variable' column of the IAMC format describes the type of information represented
in the specific timeseries. The variable name implements a "semi-hierarchical" structure
using the :code:`|` character (*pipe*, not l or i) to indicate the structure or "depth".
Names (should) follow a structure like *Category|Subcategory|Specification*.

Semi-hierarchical means that a hierarchy can be imposed, e.g., one can enforce
that the sum of *Emissions|CO2|Energy* and *Emissions|CO2|Other*
must be equal to *Emissions|CO2* (if there are no other *Emissions|CO2|…* variables).

However, this is not mandatory, e.g., the sum of *Primary Energy|Coal*,
*Primary Energy|Gas* and *Primary Energy|Fossil* should not be equal
to *Primary Energy* because this would double-count fossil fuels.

Variable naming conventions
---------------------------

A variable name should adhere to the following conventions:

*  A *|* (pipe) character indicates levels of hierarchy.
*  Do not use spaces before and after the *|* character, but add a
   space between words

   .. code:: yaml

      Primary Energy|Non-Biomass Renewables

*  Do not use abbreviations (e.g, *PHEV*) unless strictly necessary.
*  Do not use abbreviations of statistical operations (*min*, *max*,
   *avg*) but always spell out the term.
*  All words must be capitalised (except for *and*, *w/*, *w/o*, etc.).
*  If necessary to add a method or operation-identifier (e.g., Share, per capita)
   to a variable name, add it in square brackets, e.g.,

   .. code:: yaml

      Population|Urban [Share]

Units
-----

The **unit** associated with a variable should be compatible with the
`iam-units <https://github.com/iamconsortium/units>`_ package.
Alternatively, a variable can be *dimensionless*, i.e., not have a unit.
