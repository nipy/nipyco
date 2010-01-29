Possible titles
---------------

* Reproduciable Brain Imaging Results with Nipype
* Why should I use Nipype to run my spm or fsl analysis?
* Nipye to run spm or FSL analysis

Authors
-------

* Satrajit Ghosh
* Chris Burns
* Dav Clark
* Cindee Madison
* Rosalia Tungaraza
* K. Jarrod Millman


Introduction
------------

Nipype is a project under the umbrella of Nipy, an effort to develop
open-source, community-developed neuroimaging tools in Python.  The
goals of Nipype are two-fold.  First, to provide a uniform interface
to existing neuroimaging software packages.  Second, is to provide a
pipeline structure which allows for parallel processing, simple
parameter sweeping, interoperability between packages, reproducible
analyses, and easy pipeline visualization.

Nipype aims to encourages the scientific exploration of different
algorithms and associated parameters, ease the development of
pipelines within and between packages.  And to reduce the learning
curve associated with understanding the algorithms, APIs and user
interfaces of disparate packages.


limitations of existing pipelines, and
LONI pipeline and fiswidgets
(CDB: I don't think we should specifically name LONI and FISWidgets.
These tools have a lot of functionality we don't have.)

Problem of application specific pipelines


Methods
-------

Nipype is an open-source project hosted SourceForge and written in the
Python programming language, a freely available, high-level language
that is accessible to both programmers and non-programmers.  Our
documentation is written in a light-weight markup language,
Restructured Text, which is then used to generate print-quality HTML
and PDF documentation using the Sphinx application.  The source code
is tested using the Nose Python testing framework to ensure
robustness.  The software is released frequently to provide users with
prompt bug fixes and feature updates and have a release cycle of every
two months.

The interface component provides access to the individual algorithms
from the external packages SPM, FSL, and Freesurfer.  Internally, each
algorithm in the external package is wrapped in a Python class with
each algorthim parameter mapped to a class attribute.  Researchers can
get or set the parameter attributes and call a run method to execute
the algorthim with the supplied parameters.

The pipeline component provides the framework for connecting interface
nodes to form a complete analysis graph.  A Direct Acyclic Graph (DAG)
is used to manage the pipeline and ensure operational order.  At each
stage of pipeline, execution of the output of each node is
validated before inputs are passed to the next stage.  Provenance
information is stored during each stage of the pipeline, including
information about the working environment, the parameter values passed
to the algorithms and the input data files including an md5 hash of
the image data.  This provenance information is checked on re-execution
of the pipeline to determine which stages of the pipeline need to be
executed or can safely be skipped.

The pipeline allows one to easily compare algorithms [expand on this]


Architecture, basic pipeline model
compenent architecture diagram
interfaces
why python
infrastructure (hosting, docs, releases, trac, testing)
open collaborative development
international

Graph visualization of pipeline
Some examples: choose as you please 
`SPM FreeSurfer pipeline <http://dl.dropbox.com/u/363467/fs_spm_graph.dot.png>`
`SPM Level1 pipeline <http://dl.dropbox.com/u/363467/spm_graph.dot.png>`
`SPM detailed level1 pipeline <http://dl.dropbox.com/u/363467/spm_graph_detailed.dot.png>`

Parallel (ref Fernando)


Results
-------

Used at MIT BErkeley MGH
DTI?
Used on motor tasks, perception, PET, ...
avoidance of redundant expensive computation, reduces duplication in
parallel or nearly parallel pipelines
Encourages exploration of algorithm parameter changes



Very reproducible
easy to keep track of whats been done, and how



Conclusion
----------

Growing developer community
Future plans
(add afni,  ANTS, direct interface to nipy)
Good opportunity for comparative validation of tools and algorithms
Data more sematically annotated (go into detail)
query on data,
Web interface
running on large cluster with Large Scale studies
instituion wide stnadardized diagnostics

facilitates training
