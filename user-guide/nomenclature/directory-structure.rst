.. _directory-structure:

Directory structure for definitions and mappings
================================================

This is the directory structure for validation and region processing:

.. code-block:: bash

   .
   │
   ├── definitions
   │   ├── region
   │   │   ├── regions.yaml
   │   │   └── ...
   │   └── variable
   │       ├── variable.yaml
   │       └── ...
   ├── mappings [optional]
   │   ├── model_a.yaml
   │   └── ...
   └── nomenclature.yaml [optional]

The ``DataStructureDefinition`` reads the codelists from the *definitions* folder.
More information of this class is available in its API documentation `page`_.

.. _page: https://nomenclature-iamc.readthedocs.io/en/stable/api/datastructuredefinition.html

- Each "dimension" to be used for validation must have its own sub-directory in
  the *definitions* folder. The dimension names usually follow the column names
  of the IAMC data format.

- The codelists for a dimension can be distributed across multiple yaml files within a
  dimension folder, including any subfolders. When the ``DataStructureDefinition``
  object is initialized, all files in a dimension folder are combined into a single
  ``CodeList`` object for that dimension.

The ``RegionProcessor`` reads model-specific region-mappings from the *mappings*
folder. If the project has no model specific mappings, this folder can also be omitted.

Optionally, a file called *nomenclature.yaml* can be added which is used to enable
certain features.

.. tip::

  To learn about the configuration file *nomenclature.yaml*, see :ref:`nomenclature-config`
