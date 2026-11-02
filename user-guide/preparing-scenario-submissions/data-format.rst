.. _data-format:

.. tip::

  This is the last step of the **Preparing Scenario Submissions** user guide.

  To learn how to submit scenarios in the Scenario App, go to :ref:`scenario-submission`.

Formatting data in IAMC format
==============================

You can confirm the full list of definitions (allowed values) for your IAMC data
dimensions by checking the project GitHub repository or by downloading the data
template at: ``http://files.ece.iiasa.ac.at/<project>/<project>-template.xlsx``

If you are familiar with Python and git, you have the option to run validation
locally using nomenclature. For more information, see :ref:`local-validation`.

IAMC format checklist
---------------------

.. |check| raw:: html

    <input checked=""  type="checkbox">

.. |uncheck| raw:: html

    <input type="checkbox">

The following checklist helps ensure that the scenarios to be submitted are
properly formatted according to the IAMC data format and ready for upload to
the Scenario App:

|uncheck| The file format is .XLSX

|uncheck| The file contains at least one **data** sheet

   |uncheck| The sheet contains **model**, **scenario**, **region**, **variable**,
   and **unit** columns

   |uncheck| The sheet contains timeslice columns (e.g.: 2005, 2010, 2015, 2020, etc.)

|uncheck| The file does not contain duplicate rows or duplicate indexes
(combination of model, scenario, region, variable, unit)
