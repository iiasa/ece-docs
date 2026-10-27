.. _project-workflow:

Scenario workflow processing
============================

Each project workflow repository includes a ``workflow.py`` script that runs
when data is uploaded to a Scenario App instance.

Below, you can see a simple example and the breakdown of its four main steps:

.. code:: python

    from pathlib import Path

    import pyam
    from nomenclature import DataStructureDefinition, RegionProcessor, process

    here = Path(__file__).absolute().parent


    def main(df: pyam.IamDataFrame) -> pyam.IamDataFrame:
        """Project/instance-specific workflow for scenario processing"""

        dsd = DataStructureDefinition(here / "definitions")
        processor = RegionProcessor.from_directory(path=here / "mappings", dsd=dsd)
        return process(df, dsd, processor=processor)


1. Importing the Python dependencies, **pyam** and **nomenclature**

  - `pyam` is responsible for manipulating IAMC format DataFrames
  - `nomenclature` provides scenario validation and region aggregation functionalities
    
    - For more information on scenario validation, see: 

2. Parsing the project definitions

  - The project workflow directory contains and/or imports "codelists", which 
    specify the allowed values for the data dimensions (regions, variables, etc.)

	.. tip::
    
    For more information on codelists, see: :ref:`codelist`

3. Instantiating region-aggregation processor(s)

  - The ``RegionProcessor`` is built with the project's mappings, in the `mappings`
    directory, and/or imported from external repositories

	.. tip::

	  For more information on mappings and importing from external repositories, see:
    :ref:`external-repos`

  - Other specialised processors are available, such as the ``CountryProcessor``
    (for aggregating multi-country regions) and the ``NUTSProcessor``
    (for NUTS administrative regions). For more information on these, please see
    the nomenclature API documentation.

4. Running the processor(s)

  - Region processing has two parts:

    - Region renaming, from internal names outputted by the models to user-friendly,
      human-readable names for model-comparison studies
    - Region aggregation, by computing the common regions and merging the
      constituent regions' data according to a specified method.

    .. tip::
      
  	  For more information on common regions, see: :ref:`regions`

	    For more information on region aggregation, see: :ref:`model-mappings`
