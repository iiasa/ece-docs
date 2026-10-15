Frequently Asked Questions
==========================

.. rubric:: Why are there different *Scenario Explorers* for specific projects?

Each project brings together different consortium partners, focuses on a different
research question, and uses aproject-specific list of variable and regions
(see :ref:`project-templates`).

It is therefore easier to keep projects separate, with its own database platform,
an independent *Scenario Explorer* and a related GitHub repository
(see :ref:`scenario-processing`).

.. rubric:: What is the level of spatial granularity of scenarios?

The spatial granularity of the scenario data depends on the scope of the project and the
contributing modeling teams. The IAMC data format supports both aggregated data as well
as more detailed regional data like country-level resolution (see :ref:`countries`)
or the :ref:`nuts` used by the European Union.

.. rubric:: Which sectors are covered in the variable template?

The sectoral coverage of the data format is flexible and can be adapted to the needs of
the project. Read more about the :ref:`variables`.

You can also look at the `common-definitions`_ repository for a list of variables
and regions used in several projects to get an idea of typical use cases.

.. _common-definitions: https://github.com/iamconsortium/common-definitions

Scenario Submissions
--------------------

.. rubric:: My scenario submission to a Scenario App failed. How do I proceed?

For a list of common data upload errors, please see :ref:`scenario-submission-errors`.

.. rubric:: I didn't upload all of my regions/variables in my original submission. 
  Can I upload only the missing data?

The safest option is to upload the full dataset with the new data added to it.
The Scenario Explorer interprets a new submission of an already existing
model-scenario combination as a new version, and overrides it
(e.g.: you have uploaded Model A-Scenario B-Variable C data, and you need to add
missing Variable D data. If you upload Model A-Scenario B-Variable D data, the
previous data will be overwritten.
You must upload Model A-Scenario B-Variable C+Variable D data).

.. rubric:: I uploaded a large dataset more than 24 hours ago, and the upload is still running.
  Is this expected?

If your upload has been running for more than 24 hours, please contact the
Scenario Services team.

Scenario Apps
-------------

.. rubric:: Why is a workspace that I know exists not listed in the search?

Double-check the view permissions on the workspace.
Workspaces are set as private by default, so regular users will not see them
listed anywhere.
Public workspaces will be listed for all users, but can only be set to public
by app managers and administrators.

.. rubric:: How can I turn off filtering for only available data?

On the top bar of the "Data Explorer", select the dotted line document icon
**"Show variables, regions and scenarios where no data exists given the applied filters"**.
