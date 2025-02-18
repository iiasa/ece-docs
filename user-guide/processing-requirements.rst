.. _processing-requirements:

Requirements for processing modules
===================================

Any module (a.k.a. program, code or tool) must adhere to the following standards of
best-practice software development. The aim of these guidelines is to ensure reliability
of our services, minimize maintenance requirements, and guarantee reproducibility of
results across platforms.

General requirements
--------------------

- The program, code or tool must be implemented in Python (≥3.10) or R; compiled
  executables are not acceptable for security reasons
- Distribution of the source code
  - via an online version-controlled repository
  (preferably GitHub) to which the IIASA admin team has access; or
  - installation via a package manager (pip, conda, CRAN).
- The program must run on Debian (preferably Ubuntu)
- The dependencies must be clearly stated,
  e.g. as Dockerfile (describing execution environment, library dependencies etc.)
  Python package dependencies according to packaging user guide (e.g. as environment.yml, requirements.txt etc.)
  R dependencies
- The license must be clearly stated.
- The documentation of the program, code or tool must include:
  - Purpose of the program and individual top-level functions
  - Instructions how to run the program
  - Expected input (variables, region mappings) and standard output
  - Explanation of any settings and optional parameters

Application programming interface
---------------------------------

**Option 1**:

The module is called via a command-line interface (CLI)
and take the following arguments:

- :code:`input`: path to an IAMC-formatted file (:code:`xlsx` or :code:`csv`)
- :code:`output`: path where to write an output file
  (usually derived timeseries data) in the same format
- Any relevant settings and optional parameters must also be specified
  via the CLI

e.g. :code:`"python process.py --input path-to-input-file.xlsx --output path-to-output-file.xlsx"`

**Option 2** (applicable for packages/functions written in Python):

Importable Python functions that take and return :class:`pandas.DataFrame` (with columns
folllowing the IAMC format) or :class:`pyam.IamDataFrame` objects can be called as part
of the processing workflow. Any settings or optional parameters must be given as keyword
arguments to the top-level function, preferably with the option to set them via a
settings or configuration file.
