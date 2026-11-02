.. _local-usage:

Local usage of a project
========================

.. attention:: This page is intended for users who are familiar with Python,
   `git <https://git-scm.com>`_  and a service like `GitHub <https://github.com>`_.

You can use the **nomenclature** package locally (on your machine) for validation
and region-aggregration.
This can be helpful as part of processing your model results, or to ensure that
a submission to an IIASA Scenario Explorer instance will succeed.

The following **requirements** must be satisfied to use a :class:`nomenclature`-based
project locally:

1. Install Python and run ``pip install nomenclature-iamc`` to install the package
   (see `instructions <https://nomenclature-iamc.readthedocs.io/en/stable/installation.html>`_)
2. Have a project folder that has the required :ref:`directory-structure`:

   * Set up the folder with the required structure and files yourself, or
   * Clone the git repository for a specific project
     (e.g., `https://github.com/iiasa/<project>-workflow`_)

   .. attention:: When using a project repository from GitHub or a similar service,
      make sure that you keep your local clone in sync with the upstream repository.

.. _`https://github.com/iiasa/<project>-workflow`: https://github.com/iiasa

.. _local-validation:

Validation against codelists
----------------------------

The easiest use case is to validate that a data file or an `IamDataFrame
<https://pyam-iamc.readthedocs.io/en/stable/data.html#the-pyam-data-model>`_ is
compatible with the codelists (lists of variables and regions) of a project.

If there are inconsistencies with the codelists, the method
``DataStructureDefinition.validate`` will raise an error.
If the scenario data is consistent, the method returns *True*.

.. code-block:: python

  import pyam
  from nomenclature import DataStructureDefinition, process

  # Initialize the DataStructureDefinition from a suitable directory
  dsd = DataStructureDefinition("definitions")

  # Read the data using pyam
  df = pyam.IamDataFrame("/path/to/file")

  # Perform the validation
  dsd.validate(df)

Per default, a `DataStructureDefinition`_ uses the *region* and *variable*
dimensions, reading the codelists from their respective folders inside the
*definition* folder.

Alternative dimensions can be specified using the *dimensions* parameter.

.. _`DataStructureDefinition`: https://nomenclature-iamc.readthedocs.io/en/stable/api/datastructuredefinition.html

.. _region-processing:

Validation and region-processing
--------------------------------

A more elaborate use case is to perform validation against the codelists and use the
`RegionProcessor`_ to aggregate timeseries from "native regions" of a model to
"common regions" (see :ref:`regions` for more information on this standard).

.. code-block:: python

  # Import the necessary libraries
  import pyam
  from nomenclature import DataStructureDefinition, RegionProcessor, process

  # Initialize a DataStructureDefinition from a suitable directory
  dsd = DataStructureDefinition("definitions")

  # Initialize a RegionProcessor from a suitable directory that has the mappings
  rp = RegionProcessor.from_directory("mappings")

  # Read the data using pyam
  df = pyam.IamDataFrame("/path/to/file")

  # Perform the validation and apply the region aggregation
  df = process(df, dsd, processor=rp)

Refer to the section :ref:`model-mapping` for more information about this feature.

.. _`RegionProcessor`: https://nomenclature-iamc.readthedocs.io/en/stable/api/regionprocessor.html

.. _local-workflow:

Using a project-specific workflow
---------------------------------

A project workflow can be run on a scenario locally, before submission to an IIASA
database instance.
This can be useful to test the specific processing steps configured for the project.
These can include, as seen above, region-aggregation, and codelist validation.
These workflows are usually implemented as a ``main()`` function in ``workflow.py``
of a project repository.
To see a breakdown of a typical workflow, see :ref:`project-workflow`.

To run the project workflow locally, use the following command on a scenario data
file using the terminal:

.. code:: console

  nomenclature run-workflow path/to/scenario/file.xlsx

.. attention:: 
  
  The working-directory of the Python console has to be set to the clone of the
  project repository.

The output should be saved using the ``--output-file`` option with a path to an
.xlsx file.

.. code-block:: bash

  nomenclature run-workflow path/to/scenario/file.xlsx --output-file output.xlsx

If the current working directory is not the workflow directory and/or the processing
function is not main, this is also covered:

.. code-block:: bash

  nomenclature run-workflow path/to/scenario/file.xlsx \
    --workflow-file path/to/workflow.py --workflow-function not_main \
    --output-file output.xlsx

The output log in the terminal will show any validation errors.
If the output log is empty, the validation was successful.

If you want to run the workflow as part of another Python script, you can instead
import the ``main()`` function.

.. code-block:: python

  # Import the pyam library and the project-specific workflow
  import pyam
  from workflow import main as project_workflow

  # Read the scenario data and call the project-specific workflow
  df = pyam.IamDataFrame("/path/to/file")
  df = project_workflow(df)

.. important::

  Make sure to pull the latest project repository and update the **nomenclature**
  package when you repeat this step later to make sure that the IIASA infrastructure
  and your local check are in sync.
