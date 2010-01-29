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
