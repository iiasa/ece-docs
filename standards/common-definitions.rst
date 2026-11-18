.. _common-definitions:

Common definitions
==================

The *common-definitions* repository (`GitHub`_) is a central location for definitions
and mappings used across model-comparison projects based on the IAMC data format.
This facilitates reuse of standardized naming conventions and allows easier comparison
of results between different projects and studies.

This project uses the |nomenclature| for management of codelists and validation
of scenario data in the IAMC data format.

Integration in project workflows
--------------------------------

Within the Scenario Services infrastructure, *common-definitions* is used by
"importing" some or all of its content into a "project workflow repository".

A workflow repository contains the definitions and mappings used for a given
project, a configuration file, and a workflow script file.
For projects using codelists stored in *common-definitions*, the configuration
file in the repository can specify which ones to include or exclude.

To learn how to import from *common-definitions*, see the `user guide`_ in the
nomenclature documentation.

.. _GitHub: https://github.com/IAMconsortium/common-definitions

.. _user guide: https://nomenclature-iamc.readthedocs.io/en/stable/user_guide/config.html#importing-from-an-external-repository
