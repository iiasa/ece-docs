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

Option 1) Registration using an Excel template
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you do not feel comfortable using GitHub, please use the `Excel template`_ and send
it to the project managers by email.

.. _`Excel template`: https://raw.githubusercontent.com/IAMconsortium/nomenclature/main/templates/model-registration-template.xlsx

.. tip::

    **Do you need to submit a model registration spreadsheet?**

    If your model uses "standard" regions like countries (see :ref:`countries`),
    NUTS regions (see :ref:`nuts`), or US states, you typically do **not** need to
    submit a model registration spreadsheet.

    A model registration is primarily needed for models with custom regional definitions
    or aggregations that require explicit mapping.

Option 2) Registration using a GitHub pull request
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The preferred approach for model registration is starting a GitHub pull request.
Please contact the administrators if permissions for the project repository
are required.

Please follow the `Model registration user guide
<https://nomenclature-iamc.readthedocs.io/en/stable/user_guide/model-registration.html>`_.

Scenario version management
---------------------------

When submitting a scenario (a.k.a. "run") to an IIASA database instance with an already
existing model-scenario combination, the database will save the new submission as a new
version of that run. The **version number** is incremented automatically and the new
version will be automatically set as **default version** for that model-scenario name.

To select other (non-default) versions, you can use the "Switch to Advanced View" button
in the scenario-selection tab of an IIASA Scenario Explorer or you can use the
:code:`default_only=False` option of the function :func:`pyam.read_iiasa()`
or the **ixmp4** package (`read the docs <https://docs.ece.iiasa.ac.at/ixmp4>`_),
see also the Section :ref:`database-api`.

