.. tip::

  This is the third step of the **Preparing Scenario Submissions** user guide.

  To learn how to upload a file to a Scenario App, go to :ref:`scenario-submission`.

.. _preparing-data:

Preparing data in the IAMC format
=================================

About the data format
---------------------

The format was developed by the *Integrated Assessment Modeling Consortium* (`IAMC`_)
as a tabular timeseries structure to exchange scenario data related to energy systems
modelling, land-use change, demand sectors, and economic indicators in the context of
climate change mitigation pathways and the the Sustainable Development Goals (SDGs).

.. _`IAMC`: http://iamconsortium.org/

.. tip::

    Read more about the :ref:`iamc-format`.

Project-specific templates
--------------------------

Each project using the IIASA database infrastructure defines a list of variables and
regions for comparison and scenario analysis, commonly known as a “variable template”.

You can download the full list of definitions (allowed variables, regions and units) for
the data file by checking the project GitHub repository or by downloading the data
template at: ``http://files.ece.iiasa.ac.at/<project>/<project>-template.xlsx``

.. tip::

    Reach out to the IIASA Scenario Services team and/or the relevant project manager(s)
    if you are not sure where to find the project template or the GitHub repository
    associated with a particular project.

Local validation
----------------

If you are familiar with Python and git, you have the option to run the project workflow
on your computer using the :class:`nomenclature` package. This can be useful to check
that your file conforms to the data format and project specifications before uploading
the file to the Scenario App.

.. tip::

    Read the User Guide for :ref:`local-processing` for more information.

Data file checklist
-------------------

.. |check| raw:: html

    <input checked=""  type="checkbox">

.. |uncheck| raw:: html

    <input type="checkbox">

The following checklist helps you to ensure that the scenarios to be submitted are
properly structured according to the IAMC data format and ready for upload to
the Scenario App:

|uncheck| The file format is ``.xlsx``

|uncheck| If the file contains multiple sheets, at least one sheet must be named
``data`` or have a name that starts with ``data``

|uncheck| All data sheets contain all required columns **model**, **scenario**,
**region**, **variable**, and **unit** |br|
(it does not make a difference if you write **Model** or **model**)

|uncheck| All data sheets contain timeslice columns (e.g., 2010, 2015, 2020, etc.)

|uncheck| The file does not contain duplicate rows or duplicate indexes (i.e., rows that
have the same combination of model, scenario, region, variable and unit)

.. warning::

    Please make sure that data files do not exceed 30MB. You can split distinct
    scenarios into separate files to reduce the file size, but all data related to one
    model/scenario combination (a.k.a. a "run") must be kept with one file. Otherwise,
    these files will be treated as separate submissions and saved as distinct versions
    in the database.
