.. _countries:

A common list of countries
==========================

Having a standardized list of country names is an important prerequisite for region
definitions, scenario analysis and model comparison.

The :py:mod:`nomenclature` package (`read the docs`_) builds on the :py:mod:`pycountry`
package to provide a standardized list of country names based on the
`ISO 3166-1 standard`_.

For consistency with established conventions in the modelling community, several country
names are shortened compared to ISO 3166-1, e.g. from "Bolivia, Plurinational State of"
to "Bolivia".
Also, "Kosovo" is added (with *alpha_3* code "KOS", following the
`IOC <https://olympics.com/ioc/kosovo>`_), even though it is not a universally
recognized state and not oficially included in ISO 3166-1.
See the full list of changes on GitHub_.

You can access the list of countries via the model-registration `Excel template`_.

The :py:mod:`nomenclature` package also provides utility functions to work with the
country-names and easily translate between country names and alpha-3/alpha-2 codes
(also known as ISO3 and ISO2 codes). Here is an example:

.. code:: python

  from nomenclature import countries

  # list of country names
  countries.names

  # mappings between alpha_3 (ISO3), alpha_2 and country names
  name = countries.get(alpha_3="...").name
  alpha_3 = countries.get(name="...").alpha_3
  alpha_2 = countries.get(name="...").alpha_2

.. _`read the docs`: https://nomenclature-iamc.readthedocs.io/en/stable/

.. _`ISO 3166-1 standard`: https://en.wikipedia.org/wiki/ISO_3166-1

.. _GitHub: https://github.com/IAMconsortium/nomenclature/blob/main/nomenclature/countries.py

.. _`Excel template`: https://raw.githubusercontent.com/IAMconsortium/nomenclature/main/templates/model-registration-template.xlsx
