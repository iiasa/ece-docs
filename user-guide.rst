User Guide & FAQ
================

Frequently Asked Questions
--------------------------

.. rubric:: Why are there different *Scenario Explorer* instances for specific projects?

Each project usually brings together different consortium partners and uses a
project-specific list of variable and regions (see :ref:`project-templates`).

It is therefore easier to keep projects separate, with its own database **platform**,
*Scenario Explorer* instance and related GitHub repository (see :ref:`scenario-processing`).

.. rubric:: What is the level of spatial granularity of scenarios?

The spatial granularity of the scenario data depends on the scope of the project and the
contributing modeling teams. The IAMC data format supports both aggregated data as well
as more detailed regional data like country-level resolution (see :ref:`countries`)
or the :ref:`nuts` used by the European Union.

.. rubric:: Which sectors are covered by the variable template?

The sectoral coverage of the data format is flexible and can be adapted to the needs of
the project. Read more about the :ref:`variables`.

You can also look at the `common-definitions`_ repository for a list of variables
and regions used in several projects to get an idea of typical use cases.

Detailed User Guides
--------------------

.. toctree::
   :maxdepth: 2

   user-guide/local-processing

.. _common-definitions: https://github.com/iamconsortium/common-definitions
