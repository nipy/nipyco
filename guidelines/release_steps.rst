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
* Update version number of documentation in doc/conf.py
* Does the documentation build correctly?
* Do we have a documentation.zip built?
* Do the examples and tutorials work?

Create Tag
----------
Create the release tag.  In svn the command looks like this::

  svn copy https://nipy.svn.sourceforge.net/svnroot/nipy/nipype/trunk \
  https://nipy.svn.sourceforge.net/svnroot/nipy/nipype/tags/0.2 \
  -m "Tagging the 0.2 release of nipype."

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

  * ``make sdist``

* Build egg:

  * ``make egg``

After the release
-----------------
* Bump up the version number.  Set release flag (in version.py) to
  False.
* On the trac site, update the *default milestone* that new tickets
  are filed as.  Under trac > Admin > Ticket System > Milestones.

SourceForge
-----------
* Login to sourceforge and make a new documentation directory::

    ssh -t USER,PROJECT@shell.sourceforge.net create

  Once logged in, type ``sf-help`` to get information on directory locations.

* Upload documentation to new directory::

    cd doc
    #make sf_cburns

  The make target is broken... update it to tarball the built
  directory and upload that.  Created tarball manually and uploaded with::

    scp nipype-0.2-doc.tar.gz cburns,nipy@web.sourceforge.net:htdocs/nipype/0.2

* Rename documentation.zip to match distributions::

  mv documentation.zip nipype-0.2-docs.zip

* Write and upload release_notes

* Upload distribution files (tarball and eggs), documentation zip, and
  release notes.  Use SourceForge File Manager for this as I've found
  no other way.  And update the File Details for the uploaded files.

* Close the Milestone on Trac

