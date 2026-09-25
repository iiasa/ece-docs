.. _scenario_explorer:

Scenario Explorer 
=================

The Scenario Explorer is a web-based user interface for scenario results
and historical reference data.
It provides intuitive visualizations & display of timeseries data
and download of the data in multiple formats.

Workspaces for dissemination & collaboration
--------------------------------------------

The Scenario Explorer has a feature for saving and sharing “workspaces”;
see below the landing page for the *IAMC 1.5°C Scenario Explorer*
supporting the IPCC SR15,
which replicates three iconic figures from the report based
on the quantitative scenario ensemble.

Workspaces can be generated for the public such that every user
sees them on login.
Alternatively, they can be created by any user and shared bilaterally
with colleagues or on social-media.

.. figure:: _static/iamc15.png

   The `IAMC 1.5°C Scenario Explorer`_ was the first application |br|
   of the IIASA modeling platform infrastructure

.. _`IAMC 1.5°C Scenario Explorer`: https://data.ece.iiasa.ac.at/iamc-1.5c-explorer

Scenario management
-------------------

The Scenario Explorer also has an interface for uploading and
managing scenario data as a central data repository
in multi-institution model comparison exercises.
The infrastructure includes data version control and allows to run scenario
post-processing on any uploaded data (e.g., validation, consistency,
meta-analysis).

Scenario version management
```````````````````````````

When submitting a scenario (a.k.a. "run") to an IIASA database instance with an already
existing model-scenario combination, the database will save the new submission as a new
version of that run. The **version number** is incremented automatically and the new
version will be automatically set as **default version** for that model-scenario name.

To select other (non-default) versions, you can use the "Switch to Advanced View" button
in the scenario-selection tab of an IIASA Scenario Explorer or you can use the
:code:`default_only=False` option of the function :func:`pyam.read_iiasa()`
or the **ixmp4** package (`read the docs <https://docs.ece.iiasa.ac.at/ixmp4>`_),
see also the User Guide :ref:`query-iiasa-databases`.
