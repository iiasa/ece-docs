The IAMC timeseries data format
===============================

.. figure:: _static/iamc-logo.png
   :width: 150px
   :align: right

Background
----------

The *Integrated Assessment Modeling Consortium* (`IAMC`_) developed a standardised
tabular timeseries format to exchange scenario data related to energy systems modelling,
land-use change, demand sectors, and economic indicators in the context of
climate change mitigation pathways and the the Sustainable Development Goals (SDGs).
Previous high-level use cases include reports by the *Intergovernmental Panel
on Climate Change* (`IPCC`_) and model comparison exercises
within the *Energy Modeling Forum* (`EMF`_) hosted by Stanford University.

Refer to https://data.ece.iiasa.ac.at/ for a selected list of projects
using the IAMC data format.

.. _`IAMC`: http://iamconsortium.org/

.. _`IPCC`: https://www.ipcc.ch

.. _`EMF`: https://emf.stanford.edu

An illustrative example
-----------------------

The table below shows a typical example of integrated-assessment scenario data
following the IAMC format from the Horizon 2020 `CD-LINKS`_ project.

The scenario data is usually saved as *xlsx* or *csv* files in wide format
(years as columns), but other types are also possible (e.g., via
the `pyam package <https://pyam-iamc.readthedocs.io/en/stable/api/io.html>`_).

.. figure:: _static/iamc-example.png

   Illustrative example of IAMC-format timeseries data
   from the `IAMC 1.5°C Scenario Explorer`_

.. _`CD-LINKS`: https://www.cd-links.org

.. _`IAMC 1.5°C Scenario Explorer`: https://data.ece.iiasa.ac.at/iamc-1.5c-explorer

Project "templates"
-------------------

Each project using the IAMC timeseries data format defines a list of "variables" and
regions for comparison and scenario analysis, commonly known as a "variable template".

The IAM community is developing a shared resource of variable and region definitions.
The aim is to provide a central location to facilitate reuse of definitions and
mappings across projects.

Visit https://github.com/IAMconsortium/common-definitions for more information.

Variable & region naming guidance
---------------------------------

.. toctree::
   :maxdepth: 2

   iamc/variable
   iamc/region

Related software packages
-------------------------

Read more about related :ref:`software`.
