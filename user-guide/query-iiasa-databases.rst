.. _query-iiasa-databases:

Querying IIASA databases
========================

You can query scenario data from an IIASA database instance directly via Python, R or a
Rest API. The **pyam** package allows to directly query both the new *Scenario Apps*
and the (legacy) *Scenario Explorer* databases (2018-2024).

.. code:: python

    import pyam
    df = pyam.read_iiasa("<slug>", region="World", ...)

Here, the `slug` is the name of the database. To avoid large queries, you can also
filter by model, scenario or variable.

.. tip::

    Learn more about the Python package **pyam** on `Read The Docs`_.

    There is a tutorial_ to use **pyam** with **R** via the **reticulate** package.

.. _`Read The Docs`: https://pyam-iamc.readthedocs.io

.. _tutorial: https://pyam-iamc.readthedocs.io/en/stable/R_tutorials/pyam_R_tutorial.html

The approach for more complex queries depends on the database backend:

- :ref:`ixmp4`
- :ref:`legacy`

.. note::

    **Access and permission management for project-internal databases**

    By default, your can connect to all public scenario database instances via the API.
    If you have permission to connect to a private, project-internal database instance,
    you can set your credentials by running the following command in a console:

    .. code::

         ixmp4 login <username>

    You will be prompted to enter your password.

    *Your username and password will be saved locally in plain-text for future use.*

.. _ixmp4:

*Scenario Apps* and **ixmp4** instances
---------------------------------------

New *Scenario Explorer* instances (set up since 2025) use the *ScSe Apps infrastructure*
and the **ixmp4** package as a database backend. You can list all **ixmp4** platforms
hosted by IIASA (and to which you have access) using :func:`pyam.iiasa.platforms()`.

You can use :func:`pyam.read_iiasa()` for simple queries or the **ixmp4** package for
connecting to a platform and executing other requests.

.. code:: python

    import ixmp4

    # connect to a database platform
    platform = ixmp4.Platform("<slug>")

    # get a table of all "scenario runs" in the database
    platform.runs.tabulate()

    # get a table of all IAMC variables
    platform.iamc.variables.tabulate()

.. _legacy:

Legacy *Scenario Explorer* instances
------------------------------------

You can use the **pyam** package to connect to a legacy *Scenario Explorer* instance
developed by the Scenario Services and Scientific Software team from 2018 until 2024.

You can use :func:`pyam.read_iiasa()` for simple queries or the
:class:`pyam.iiasa.Connection` class to get a list of available instances or for more
elaborate queries.

.. code:: python

    import pyam

    # get a list of all available legacy database instances
    pyam.iiasa.Connection().valid_connections

    # connect to a specific legacy database instance
    database = pyam.iiasa.Connection("<slug>")

    # get a table of all scenarios in this database
    database.properties()
