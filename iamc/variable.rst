The *variable* column
=====================

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
   space between words (e.g., *Primary Energy|Non-Biomass Renewables*).
*  Do not use abbreviations (e.g, *PHEV*) unless strictly necessary.
*  Do not use abbreviations of statistical operations (*min*, *max*,
   *avg*) but always spell out the term.
*  All words must be capitalised (except for *and*, *w/*, *w/o*, etc.).
*  Add hierarchy levels where it might be useful in the future, e.g.,
   use *Electric Vehicle|Plugin-Hybrid* instead of *Plugin-Hybrid
   Electric Vehicle*.
*  Do not include words like *Level* or *Quantity* in the variable,
   because this should be clear from the context or unit.

Units
-----

The **unit** attribute is **required** and its value should be compatible with the
`iam-units <https://github.com/iamconsortium/units>`_ package. Alternatively,
a variable can be *dimensionless*, i.e., not have a unit.
