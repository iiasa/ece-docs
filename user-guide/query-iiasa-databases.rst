.. _query-iiasa-databases:

Querying IIASA databases
========================

You can query scenario data from an IIASA database instance directly via Python, R or a
Rest API.

*Scenario Apps* and **ixmp4** instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

New *Scenario Explorer* instances (set up since 2025) use the *ScSe Apps infrastructure*
and the **ixmp4** package as a database backend. You can list all **ixmp4** platforms
hosted by IIASA (and to which you have access) using :func:`pyam.iiasa.platforms()`.

You can use :func:`pyam.read_iiasa()` for simple queries or the **ixmp4** package for
connecting to a platform and executing other requests.

.. code:: python

    import ixmp4

    platform = ixmp4.Platform("<instance>")

    # get a table of all "scenario runs" in the database
    platform.runs.tabulate()

    # get a table of all IAMC variables
    platform.iamc.variables.tabulate()

Legacy *Scenario Explorer* instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can use the **pyam** package to connect to a legacy *Scenario Explorer* instance
developed by the Scenario Services and Scientific Software team from 2018 until 2024.
For example, you can get a list of all scenarios in a database instance. You can also
use :func:`pyam.read_iiasa()` to query scenario data from a legacy instance.

.. code:: python

    import pyam

    conn = pyam.iiasa.Connection("<instance>")

    # get a table of all scenarios in the database
    conn.properties()

    # query scenario data and meta indicators from the database
    df = pyam.read_iiasa(conn, .. <filter_arguments>)

Refer to :class:`pyam.iiasa.Connection` for more information.

.. note::

    Read the `pyam documentation`_ for more information about working with the IIASA
    scenario databases and Python.

.. _`pyam documentation`:  https://pyam-iamc.readthedocs.io/en/stable/tutorials/iiasa.html
