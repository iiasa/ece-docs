Preparing scenario submissions
==============================

The following steps guide new users from registering new Scenario Explorer
accounts to successfully uploading data.

1. **Registering in the Scenario Explorer**

   To register a new user account, head to
   https://manager.ece.iiasa.ac.at/register. Once you click **Register**, a
   message will be sent to the registered e-mail address to validate the
   account.

2. **Accessing a Scenario Explorer App**

   Access permission for Scenario Explorer apps is configured in the IIASA ECE
   Manager.

   In order to have access to a private or gated app, the user must be
   registered in the respective accessor group. Public apps are accessible to
   any person by default.

   To gain access, please contact an administrator from the IIASA Scenario
   Services team, or the appropriate contact person in the project.

3. **Logging in to the Scenario Explorer**

   To log in, navigate to the top-right corner of the screen, click the **Log
   In** button, and enter your credentials (for legacy apps, the log in screen
   should be on the right-hand side of the main screen).

4. **Setting up Upload Permissions**

   In order to upload data to the Scenario Explorer, the user must be
   registered in the appropriate modeler group(s).

   To have submit permission, please contact an administrator from the IIASA
   Scenario Services team, or the appropriate contact person in the project,
   specifying the model name(s) and version(s) to be uploaded (e.g.:
   **Model-Name v1.0**).

5. **The Scenario Submission Page**

   The **Submit Scenario File** menu on the left side displays a space to drag
   and drop or click to select the file to upload, and an optional text
   description for the upload job log.

   The **Your Registered Models** on the right side lists the model names and
   versions for which upload permissions are set for the current user.

   .. note::

      For legacy apps, the scenario submission page can be accessed in the user
      dropdown menu, by clicking **Uploads**.

      The **+** button on the top right corner opens the upload menu. To
      upload, select the file type (IAMC data or image), add an optional
      description for the upload job log, and choose a file. The **Process
      file upon upload** option must remain selected for IAMC data to be
      displayed in the Scenario Explorer.

   Once an upload job starts, it will be displayed in the **Submissions List**.
   Here, the filename, upload date/time, file size, and user are listed for
   each job, as well as the processing time and upload status (success or
   failure).

   For each job, the user can download the file, restart the job, and open the
   **Job details** window with the full log output and error summary.

   For common upload errors with short messages, a red warning box with the
   error text will be displayed in the **Error Summary** (e.g.:
   ``Forbidden: You are missing submit permissions for: ['Model-Name v1.0'].``).

   If no error summary is displayed, the full error can be identified in the
   log.

6. **Common Scenario Submission Errors**

   The following is a list of common scenario submission errors:

   * ``Forbidden: You are missing submit permissions for: [...]``

     **Reason:** The user does not have permission to upload data for the
     model(s) listed in the error message.

     **Fix:** If the user is not meant to upload data for the model(s), remove
     the corresponding rows of data. If the user is meant to upload data for
     the model(s), compare the **Your Registered Models** list to the error
     message and 1) check the spelling, including upper/lowercase, extra
     whitespace, etc., 2) check the model version number. If the error persists
     or no such model is listed in the registered models, please contact a
     project manager or IIASA administrator to add the missing permissions.

   * ``nomenclature.exceptions.WrongUnitError: The following variables(s) are reported in the wrong unit: [...]``

     **Reason:** The data contains variables reported with the wrong unit of
     measurement.

     **Fix:** Replace the wrong (``found``) unit of measurement for the correct
     one (**expected**). If the expected unit is incorrect, please contact a
     project manager or IIASA administrator.

   * ``nomenclature.exceptions.UnknownVariableError: The following variable(s) are not defined in the variable codelist: [...]``

     **Reason:** The data contains variables not allowed for the project.

     **Fix:** If the variables are not meant to be uploaded, remove the
     corresponding rows of data. If the variables are meant to be uploaded,
     please refer to the template file in the full log output, compare the
     listed variables with the template's and check the spelling, including
     upper/lowercase, extra whitespace, etc. If the variables are listed in the
     template with a different naming convention, rename the variables in the
     upload data or please contact a project manager or IIASA administrator.

   * ``nomenclature.exceptions.UnknownRegionError: The following region(s) are not defined in the region codelist: [...]``

     **Reason:** The data contains regions not allowed for the project.

     **Fix:** If the regions are not meant to be uploaded, remove the
     corresponding rows of data. If the regions are meant to be uploaded,
     please refer to the template file in the full log output, compare the
     listed regions with the template's and check the spelling, including
     upper/lowercase, extra whitespace, etc. If the regions are listed in the
     template with a different naming convention, rename the regions in the
     upload data or please contact a project manager or IIASA administrator.

7. **IAMC Data Format Checklist**

.. |check| raw:: html

    <input checked=""  type="checkbox">

.. |uncheck| raw:: html

    <input type="checkbox">

   The following checklist helps ensure that the files to be uploaded are
   properly formatted according to the IAMC data format and ready for upload to
   the Scenario Explorer:

   |uncheck| The file format is in XLSX
   |uncheck| The file contains a **data** sheet

        |uncheck| The sheet contains **model**, **scenario**, **region**,
          **variable**, and **unit** columns
        |uncheck| The sheet contains timeslice columns (e.g.: 2005, 2010, 2015, 2020,
       etc.)

   |uncheck| The file does not contain duplicate rows or duplicate indexes
     (combination of model, scenario, region, variable, unit)