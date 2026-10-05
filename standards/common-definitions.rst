.. _common-definitions:

Common definitions
==================

The *common-definitions* repository (`GitHub`_) holds definitions and mappings for model-comparison
projects using the IAMC data format.
The aim is to provide a central location to facilitate reuse of definitions and
mappings across projects.

This project uses the Python package `nomenclature-iamc`_ for management of
codelists and validation of scenario data in the IAMC data format.

Integration in project workflows
--------------------------------

Within the Scenario Services infrastructure, *common-definitions* is used by
"importing" some or all of its content into a "project workflow repository".

A workflow repository contains the definitions and mappings used for a given
project, a configuration file, and a workflow script file.
For projects using codelists stored in *common-definitions*, the configuration
file in the repository can specify which ones to include/exclude.

To learn how to import from *common-definitions*, see the `user guide`_ in the
`nomenclature` documentation.

.. _`nomenclature-iamc`: https://nomenclature-iamc.readthedocs.io/en/stable/

.. _GitHub: https://github.com/IAMconsortium/common-definitions

.. _user guide: https://nomenclature-iamc.readthedocs.io/en/stable/user_guide/config.html#importing-from-an-external-repository
