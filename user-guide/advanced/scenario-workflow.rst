.. _project-workflow:

Scenario workflow processing
============================

.. code:: python

    from pathlib import Path

    import pyam
    from nomenclature import DataStructureDefinition, RegionProcessor, process

    here = Path(__file__).absolute().parent


    def main(df: pyam.IamDataFrame) -> pyam.IamDataFrame:
        """Project/instance-specific workflow for scenario processing"""

        # Run the validation and region-processing
        dsd = DataStructureDefinition(here / "definitions")
        processor = RegionProcessor.from_directory(path=here / "mappings", dsd=dsd)
        return process(df, dsd, processor=processor)


This simple workflow script consists of four main steps:

1. Importing the Python dependencies, **pyam** and **nomenclature**

	- `pyam` is responsible for manipulating IAM DataFrames
	- `nomenclature` provides scenario validation and region aggregation
    functionalities

		- For more information on scenario validation, see:

2. Parsing the project definitions

	- The project workflow directory contains and/or imports "codelists", which
    specify the allowed values for the data dimensions (regions, variables, etc.)

		- For more information on codelists, see:

3. Instantiating region-aggregation processor(s)

	- The ``RegionProcessor`` is built on the project's mappings, in the `mappings`
    directory and/or imported from external repositories

		- For more information on mappings and importing from external repositories,
        see:

	- Other specialised processors are available, such as the ``CountryProcessor``
    (for aggregating multi-country regions) and the ``NUTSProcessor``
    (for NUTS administrative regions)

4. Running the processor(s)

	- Region processing has two parts:

		- Region renaming, from internal names outputted by the models to
        user-friendly, human-readable names for model-comparison studies
		- Region aggregation, ... 
