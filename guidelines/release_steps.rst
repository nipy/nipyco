============================
 Steps for making a release
============================

This document will serve as a check-list for each release.  The
release process should be automated where possible, but some steps
always require human involvement and inspection.  Please update this
document if you find missing information during a release.

Bugs and Tickets
----------------
* Are there any remaining tickets on the bug tracker targeted to this
  release?

Build and Install
-----------------

* Make sure the package installs correctly, often we (developers)
  symlink from our site-packages directory to our development
  directory.  Do an actual install and confirm the install works
  correctly.  Virtualenv is helpful for this.
* Do all of the subpackages install?  Sometimes we forget to put the
  'config.add_subpackage('package_name')' in the setup.py.
* Do all tests pass?

Tests
-----
* Do all tests pass?  Run tests from top-level directory and include
  doctests::

  nosetests -v --with-doctest

Documentation
-------------
* Does the documentation build correctly?
* Do we have a documentation.zip built?
* Do the examples and tutorials work?

Distributions
-------------
* Are all files included in the source distribution?  If any are
  missing, update the MANIFEST.in.  The sdist should include
  everything to build the code and the docs, as though one did an 'svn
  co'.
* Is the version number correct?  Is the release flag (in version.py)
  set to True?
* Are the installation instructions on the website correct?
* Build source distribution:

  * ``python setup.py sdist``
  * nipype has a make target: ``make sdist``

* Build egg:

  * ``python setup.py bdist_egg``
  * nipype has a make target: ``make egg``

After the release
-----------------
* Bump up the version number.  Set release flag (in version.py) to
  False.
* On the trac site, update the *default milestone* that new tickets
  are filed as.
