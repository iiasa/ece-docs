.. _local-processing:

Executing scenario processing locally
=====================================

A project workflow can be run on a scenario locally, before submission to an IIASA
database instance.
This can be useful to test region aggregation and validation.

To run the project workflow locally, do the following:

1. Install Python and run ``pip install nomenclature-iamc`` to install the package
2. Git-clone the project repository
   (usually `https://github.com/iiasa/<project>-workflow`_)
3. Run the workflow on a scenario data file using the terminal (from the folder
   where the project repository was cloned to).

.. code::

    nomenclature run-workflow <path-to-scenario-file>.xlsx

The output log in the terminal will show any validation errors.
If the output is empty, the validation was successful.

.. _`https://github.com/iiasa/<project>-workflow`: https://github.com/iiasa

.. warning::

   Make sure to pull the latest project repository and update the **nomenclature** package
   when you repeat this step later to make sure that the IIASA infrastructure and your
   local check are in sync.

Read the `Local usage of a project`_ guide in the **nomenclature** package
documentation for more information!

.. _`Local usage of a project`: https://nomenclature-iamc.readthedocs.io/en/stable/user_guide/local-usage.html
