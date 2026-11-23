.. _nomenclature-guide:

Scenario processing and validation
==================================

The |nomenclature| is a Python package developed by the |ScSe team|. It is a key part
of the scenario submission process for projects that use the IIASA scenario database
infrastructure.

In the scenario submission process, :class:`nomenclature` is used to perform three tasks:

1. Management of the variables and regions (a.k.a. "codelists") used in a project
2. Processing of configuration files
3. Data processing workflows

   - Validation of submitted scenario data against codelists
   - Region aggregation from model-native regions to common (aggregate) regions

The three parts of the processing workflow: codelists, model mappings and the actual
processing code are usually hosted in a GitHub repository.

As an example, in the openENTRANCE project (`github.com/openENTRANCE/openentrance
<https://github.com/openENTRANCE/openentrance>`_) these three parts are the
``definitions/`` and ``mappings/`` folders which contain codelists and model mappings,
and ``workflow.py`` which contains the processing code using nomenclature.

The validation and region-processing for a specific can be run locally by any user. In
order to do so, the corresponding GitHub repository needs to be cloned, nomenclature
installed and the ``main`` function in ``workflow.py`` be given a
:class:`pyam.IamDataFrame` of the model data as input.

When working with nomenclature, there are two main classes that the user interacts with,
``DataStructureDefinition`` and ``RegionProcessor``.

The ``DataStructureDefinition`` class parses :ref:`codelist <codelist>` files which
define allowed values for validation. The most commonly used dimensions for validation
in a model comparison or scenario exercise are *variable* and *region*.

The ``RegionProcessor`` parses :ref:`model mapping <model-mappings>` files which
define the renaming of native regions and aggregation to common regions.

The top-level function ``process`` takes both of the above classes as input along
with data in form of a ``pyam.IamDataFrame``. The input data is aggregated using
the RegionProcessor and validated using DataStructureDefinition.

To learn more about each step in-depth, please see the guides below:

.. toctree::
   :maxdepth: 1

   nomenclature/directory-structure
   nomenclature/config
   nomenclature/codelist
   nomenclature/model-mappings
   nomenclature/scenario-workflow

.. tip::

  Learn more about the :class:`nomenclature` package at
  https://nomenclature-iamc.readthedocs.io.
