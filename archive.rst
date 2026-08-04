The IIASA Modeling Platform Server
==================================

The IIASA *Energy, Climate, and Environment Program* (ECE) hosts
a suite of **Scenario Explorer** instances and
related infrastructure to support analysis of integrated-assessment pathways
in IPCC reports and model comparison projects.
High-profile use cases include the `IAMC 1.5°C Scenario Explorer hosted by IIASA`_
supporting the IPCC *Special Report on Global Warming of 1.5°C* (SR15) and
the Horizon 2020 project `CD-LINKS <https://data.ece.iiasa.ac.at/cd-links/>`_.

This page provides the technical documentation for the database infrastructure.
For more information on the hosted instances and related projects,
please visit https://data.ece.iiasa.ac.at.

The server infrastructure is built
on the open-source *integrated and cross-cutting modelling platform* package
(`ixmp <https://docs.messageix.org/projects/ixmp/en/latest/>`_).
The platform provides a data warehouse for high-powered numerical scenario
analysis. It allows an efficient workflow between original input data
sources and implementations of mathematical models, via application programming
interfaces (API) with the scientific programming languages Python and R
as well as a `REST API <rest_api.html>`_ for access via web-based applications.

.. _`IAMC 1.5°C Scenario Explorer hosted by IIASA`: https://data.ece.iiasa.ac.at/iamc-1.5c-explorer

Table of Contents
-----------------

.. toctree::
   :maxdepth: 1

   scenario_explorer
   tutorials
   rest_api
   scenario_processing
