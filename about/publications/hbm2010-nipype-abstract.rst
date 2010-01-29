Possible titles
---------------

* Reproducible Brain Imaging Results with Nipype
* Why should I use Nipype to run my spm or fsl analysis?
* Nipype to run spm or FSL analysis

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
to existing neuroimaging software packages.  Second, to provide a
pipeline structure which allows for parallel processing, simple
parameter sweeping, interoperability between packages, reproducible
analyses, and easy pipeline visualization.

Nipype aims to: (1) encourage the scientific exploration of different
algorithms and associated parameters; (2) ease the development of
workflows within and between packages; (3) reduce the learning
curve associated with understanding the algorithms, APIs and user
interfaces of disparate packages; (4) provide a plugin like
environment for developers to create and test new cross-package
algorithms; and (5) provide a collaborative environment for
neuroimaging software development in a high-level language. These aims
address some limitations of existing neuroimaging pipeline
systems (e.g., LONIPipeline, CaMBA, MIPAV, BioImageSuite). 


Methods
-------

Nipype is an open-source project hosted SourceForge and written in the
Python programming language, a freely available, high-level language
that is accessible to both programmers and non-programmers.  Our
documentation is written in a light-weight markup language called
Restructured Text, from which print-quality HTML and PDF documentation
are generated using the Sphinx Python application.  The source code is
tested using the Nose Python testing framework to ensure robustness
and to allow for easier code mainenance. Using IPython, Nipype can be
used interactively or in a distributed computing mode. Nipype is
released frequently to provide users with prompt bug fixes and feature
updates, and has a release cycle of every two months. Figure 1 shows
the component architecture of nipype.

The interface component provides access to the individual programs and
functions from external packages, such as SPM, FSL, and Freesurfer.
Internally, each algorithm in the external package is wrapped in a
Python class with each algorithm parameter mapped to a class
attribute.  Researchers can get or set the parameter attributes and
call a run method to execute the algorithm with the supplied
parameters.

The pipeline component provides the framework for connecting interface
nodes to form a complete analysis workflow. The workflow is
represented in a directed acyclic graph (DAG), enabling efficient use
of existing scheduling algorithms and ensuring operational
consistency (see Fig. 2 for an example workflow). Provenance
information is stored during each stage of the pipeline, including
information about the working environment, the parameter values passed
to the algorithms and an md5 hash of the input state. The md5 hash
which is computed based on contents of files determines if a stage
needs re-execution or can safely be skipped.

The pipeline mechanism allows one to easily compare algorithms and the
influence of algorithms on an entire workflow. It allows users to use optimized
algorithms from different packages in the same workflow and to distribute
the computation across computers using IPython.

Results
-------

Nipype has been in use at UC Berkeley, University of Edinburgh, MGH,
MIT and University of Washington, Seattle on a wide range of
projects. These include: 1) large pediatric and psychiatric studies;
2) MRI, fMRI, DTI and PET studies; and 3) a variety of cognitive and
experimental paradigms. In all of these cases, the advantage of using
Nipype has been: a) to work through a single interface on different
software; b) to avoid redundant expensive computations; 3) to reduce
duplication of data in workflows; 4) to distribute computational
load across file-system sharing clusters; 5) to keep track of what has
been done; and 6) to visualize the workflow.

Furthermore, integrating interfaces to FSL and FreeSurfer allows SPM
workflows to leverage different volume- and surface-based structural
analysis components and provides a mechanism for integrating MRI, fMRI
and DTI data within a single workflow.


Conclusion
----------

Nipype provides an environment for interactive manipulation of data
through a python interface as well as performing reproducible,
distributed analysis using the pipeline system and has a growing
developer and user community. Future plans include adding: interfaces
to other analysis tools (e.g., Afni, ANTS), a direct interface to the
NIPy statistical analysis framework, the ability to query data and
workflows, a repository for workflows (cf. myExperiment.org),
infrastructure for using Nipype as a teaching tool. 

Future plans
(add afni,  ANTS, direct interface to nipy)
Good opportunity for comparative validation of tools and algorithms
Data more sematically annotated (go into detail)
query on data,
Web interface
running on large cluster with Large Scale studies
instituion wide stnadardized diagnostics

facilitates training
