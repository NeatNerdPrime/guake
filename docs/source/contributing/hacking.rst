=============
Hacking Guake
=============

Contributing
============

First, be sure to use a verion of Python 3 where GTK and GObjects works in your system.
For instance, under Ubuntu 17.04, PyGtk and ``python3-gi`` does not work well if the default
python 3 interpreter is forced to Python 3.6.

+-------------------+----------------------------+-----------------------------+
| Operating System  | Recommended Python version | Notes                       |
+===================+============================+=============================+
| Ubuntu 14.04 LTS  | Python 3.4 (UNTESTED)      |                             |
+-------------------+----------------------------+-----------------------------+
| Ubuntu 16.04 LTS  | Python 3.5 (TESTED)        |                             |
+-------------------+----------------------------+-----------------------------+
| Ubuntu 17.04      | Python 3.5 (TESTED)        |                             |
+-------------------+----------------------------+-----------------------------+
| Ubuntu 17.10      | Python 3.6 (TESTED)        | Quick Open disabled (#1230) |
+-------------------+----------------------------+-----------------------------+

Validate your code
------------------

We are strict on code styling, with pep8 and pylint running automatically in GitHub Actions
in order to reject badly shaped patches. Please use the following command to validate all
python files:

.. code-block:: bash

    $ make style  # fix the style of python files
    $ make check  # static code analysis
    $ make test   # unit test campaign
    $ make dists  # make distribution packages

Update translation
==================

Update all translation files:

.. code-block:: bash

    $ make update-po

Install the translations files:

.. code-block:: bash

    $ sudo make install-locale

Then use your favorite po editor, such as ``poedit``.

Start Guake with a different locale (locales should be installed):

.. code-block:: bash

    $ LC_ALL=fr_FR.UTF8 make run


Update NEWS
-----------

Update the `NEWS` file using the followng command:

.. code-block:: bash

    make release-note-news


The ``ChangeLog`` files is not maintained but instead automatically generated by PBR when
building the distribution packages.

Same goes for the `ChangeLog` file.

Versioning
-----------

Versioning is automatically done using git tags. When a semver tag is pushed, a new version
is automatically created by PBR.

PBR also has some magic to generate the version automatically from ``sem-ver`` tag found in the
commit message. See the ``Makefile``'s ``tag-pbr`` target.

GitHub Actions build
--------------------

GitHub Actions automatically check pull requests are compiling and check for code style.

Status of the latest build: https://github.com/Guake/guake/actions
