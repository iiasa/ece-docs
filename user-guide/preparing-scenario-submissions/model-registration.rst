.. _model_registration:

Model registration
==================

To participate in a model comparison project using the IIASA scenario database
infrastructure, you have to "register" your model.
A model registration requires three specifications:

* A model name including a *version number*, preferably using
  `semantic versioning <https://semver.org>`_
* A list or mapping of region names as they will be submitted (uploaded) to an IIASA
  database instance by the modeling team, and how the region names should appear
  in the processed scenario data
* A model mapping to perform region aggregation from *native_regions* to
  *common_regions* and renaming of model native regions (optional)

.. note::

    **When to change the model version number**

    The version number should (only) be changed if:
    
    a) the regional resolution of the model changes (e.g., adding more countries/regions), or
    b) new sectors or modules are added to the model

    Minor updates or changes do not require a new version number.

Registration using an Excel template
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you do not feel comfortable using GitHub, please use the `Excel template`_ and
send it to the project managers by e-mail.

.. _`Excel template`: https://raw.githubusercontent.com/IAMconsortium/nomenclature/main/templates/model-registration-template.xlsx

.. tip::

    **Do you need to submit a model registration spreadsheet?**

    If your model uses "standard" regions like countries (see :ref:`countries`),
    NUTS regions (see :ref:`nuts`), or US states, you typically do **not** need to
    submit a model registration spreadsheet.

    A model registration is primarily needed for models with custom regional definitions
    or aggregations that require explicit mapping.

If you have filled out the Excel model registration template and need to convert
it to YAML format, you can use the :ref:`cli` command ``parse-model-registration``:

.. code:: bash

    nomenclature parse-model-registration registration.xlsx

This command reads the Excel file and generates two sets of YAML files:

- **Region definitions**: created in ``definitions/region/`` (default location)
- **Model mappings**: created in ``mappings/`` (default location)

You can specify custom output folders using the ``--definition-path`` and
``--mappings-path`` options:

.. code:: bash

    nomenclature parse-model-registration registration.xlsx \
        --definition-path ./custom/definitions/region \
        --mappings-path ./custom/mappings

The command automatically:

- Parses the **"Common-Region-Mapping"** sheet to generate model mapping YAML files
- Parses the **"Region-Country-Mapping"** sheet (if present) to generate region
  definitions with country lists
- Adds an aggregation to "World" from R5 regions (if present)

Registration using a GitHub Pull Request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The preferred approach for model registration is starting a GitHub Pull Request.
The project workflow repository is usually found in:
`https://github.com/iiasa/<project>-workflow <https://github.com/iiasa>`_
Please contact an administrator from the IIASA Scenario Services team if permissions
for the project repository are required.

1. **Native-region definitions**

If the model reports results at a model-specific regional resolution (e.g., other
than national countries), add a file ``<your-model_vX.X>.yaml`` in the folder
``definitions/region/model_native_regions/``.

This file should follow the region-naming conventions of :ref:`region`.
The *hierarchy* property should be the model name including the version number.

2. **Model mapping for region processing**

If the scenario-processing workflow should execute a region-processing step,
add a file ``<your-model_vX.X>.yaml`` in the folder ``mappings/``.

This file should follow the region-naming conventions of :ref:`model_mapping`.

3. **Continuous integration**

When registering a model via a pull request to a GitHub project repository, a
GitHub Actions workflow is executed for ensuring that the model mapping is valid.
This serves to ensure that there are no typos or inconsistencies in the mapping or
region names. For example, only regions defined in the *region* codelist can be
used as targets for renaming or aggregation in the region-aggregation.

You can run the validation locally using the **nomenclature** function
:func:`assert_valid_structure` of the `cli`_.

.. _`cli`: https://nomenclature-iamc.readthedocs.io/en/stable/cli.html
