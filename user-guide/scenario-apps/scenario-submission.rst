.. _scenario_submission:

The Scenario Submission Page
============================

The **Submit Scenario File** menu on the left side displays a space to drag
and drop or click to select the file to upload, and an optional text
description for the upload job log.

The **Your Registered Models** on the right side lists the model names and
versions for which upload permissions are set for the current user.

Submitting Scenario Data
------------------------

.. _scenario-processing:

Scenario processing
-------------------

When submitting a scenario (a.k.a. "run") to an IIASA database instance, the server
executes a scenario-processing workflow including *region-aggregation* and *scenario
validation* prior to saving the scenario to the database. The processing uses the
**nomenclature** package (`read the docs <https://nomenclature-iamc.readthedocs.io>`_).

The region-aggregation and validation is configured via a project-specific GitHub_
repository, usually named `https://github.com/iiasa/<project>-workflow`_. Please contact
the respective project managers or the Scenario Services team if you need access.

You can also run the project workflow locally (on your computer) before submission to
an IIASA database instance, to make sure that the validation and processing works.
See :ref:`local-processing` for more information.
 
The workflow for processing files uploaded via the IIASA Scenario Explorer is
implemented in a modular fashion. It is possible to execute programs, code and tools
developed by (non-IIASA) research partners as part of the processing workflow
if the tool follows the :ref:`processing-requirements`.

.. _GitHub: https://www.github.com

.. _`https://github.com/iiasa/<project>-workflow`: https://github.com/iiasa
