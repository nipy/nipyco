============================
 Steps for making a release
============================

* Make sure the package installs correctly, often our site-packages
  has a symlink to our development directory.
* Do all of the subpackages install?  Sometimes we forget to put the
  'config.add_subpackage('package_name')' in the setup.py.
* Does the documentation build correctly?
* Do we have a documentation.zip built?
* Are all files included in the source distribution?  If any are
  missing, update the MANIFEST.in.  The sdist should include
  everything to build the code and the docs, as though one did an 'svn
  co'.
* Do the examples and tutorials work?
* Is the version number correct?  Is release set to True?
* Are the installation instructions on the website correct?
* Build source distribution:

  * ``python setup.py sdist``
  * nipype has a make target: ``make sdist``

* Build egg:

  * ``python setup.py bdist_egg``
  * nipype has a make target: ``make egg``


