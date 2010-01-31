Possible titles
---------------

* Reproducible Brain Imaging Results with Nipype
* Why should I use Nipype to run my SPM or FSL analysis?
* Nipype to run SPM or FSL analysis
* Nipype: a platform for uniform interaction across neuroimaging
  software


Authors
-------

* Satrajit S. Ghosh, Ph.D., Research Laboratory of Electronics, Massachusetts
  Institute of Technology, Cambridge, MA, USA (satra at mit.edu) - no
  conflict of interest
* Christopher D. Burns, Helen Wills Neuroscience Institute, University
  of California, Berkeley, CA, USA
* Dav Clark
* Krzysztof Gorgolewski, School of Informatics, University of
  Edinburgh, UK
* Yaroslav O. Halchenko, Dartmouth College, NH, USA
* Cindee Madison
* Rosalia F. Tungaraza, Ph.D, Integrated Brain Imaging Center,
  University of Washington, Seattle, WA, USA
* K. Jarrod Millman


Introduction
------------

Current neuroimaging software offer users an incredible opportunity to
analyze their data in different ways, with different underlying
assumptions. However, this has resulted in a heterogeneous collection
of specialized applications without transparent interoperability or a
uniform operating interface. Nipype, a project under the umbrella of
Nipy, is an open-source, community-developed project that aims to
solve these issues by providing a uniform interface to existing
neuroimaging software and by facilitating interaction between these
packages within a single workflow.

To achieve these aims, Nipype provides a Python-based environment that
encourages interactive exploration of algorithms from different
packages (e.g., SPM, FSL), eases the design of workflows within and
between packages, and reduces the learning curve necessary to use a
variety of packages.  Nipype is creating a collaborative
platform for neuroimaging software development in a high-level
language and addressing limitations of existing pipeline systems.


Methods
-------

The Nipype architecture (Fig. 1) consists of a set of interfaces and a
pipeline framework that provide uniform access to and interoperability
between external software packages.

The interfaces encapsulate functional components (e.g., brain extraction, realignment)
from external packages (e.g., FSL, SPM) and provide a uniform access
mechanism to these components. Users can introspect individual
algorithms, query and set their parameters, and execute, retrieve and
visualize outputs interactively from a Python prompt. The pipeline
framework provides the mechanism to connect interfaces to form a
complete analysis workflow and execute it. The workflow is represented
in a directed acyclic graph (DAG), enabling orderly execution and
ensuring operational consistency (see Fig. 2 for an example
workflow).

The pipeline component enables distributed processing (on multicores,
clusters, and clouds), allows parameter sweeping across workflows,
provides interoperability between packages, and easy re-analysis and
visualization of workflows. When a workflow is re-analyzed, the
pipeline engine executes only nodes whose input parameters and/or data
files have changed from the previous run, eliminating redundant
execution.

Nipype is available on SourceForge (http://nipy.sf.net/nipype) and is
written in Python, a free high-level language accessible to both
programmers and non-programmers with extensive scientific computation
capabilities. Nipype is documented using a light-weight markup
language called RestructuredText, from which print-quality HTML and
PDF documentation are generated.
The source code is tested using the Nose Python testing
framework to ensure robustness and to allow for easier code
maintenance. Nipype is released frequently to provide users with
prompt bug fixes and feature updates, and is available as part of
NeuroDebian (http://www.neurodebian.org) and as part of any Debian
derivatives (e.g., Ubuntu).


* Fig 2: `SPM FreeSurfer pipeline <http://dl.dropbox.com/u/363467/fs_spm_graph.dot.png>`_


Results
-------

Nipype has been in use at UC Berkeley, University of Edinburgh, MGH,
MIT, and University of Washington, Seattle on a wide range of
projects. These include: 1) large pediatric and psychiatric studies;
2) MRI, fMRI, DTI and PET studies; and 3) a variety of cognitive and
experimental paradigms. In all of these cases, the advantages of using
Nipype have been: a) use of different software through a single
interface; b) avoidance of redundant expensive computations; 3)
reduction of duplication of data in workflows; 4) distribution of computational
load across file-system sharing clusters; 5) protocolization of the
exact parameters and components of the analyses; and 6) visualization of
the workflows.

The ability to interact with external programs from a single Python
prompt aids in learning about new tools and developing new
workflows. The pipeline mechanism allows easy comparisons of
algorithms and their influence on an entire workflow. It
allows researchers to use optimized algorithms from different packages
in the same workflow. As an example, integrating interfaces to FSL and
FreeSurfer allows SPM workflows to leverage different volume- and
surface-based structural analysis components (e.g., Fig 2). The
workflow in Figure 2 combines surface-based smoothing with an
SPM-based first-level analysis. The resultant contrast images were
then used for a FreeSurfer-based group-analysis using surface-based
spherical registration.

Nipype provides a plugin-like environment for developers to create and
test new cross-package algorithms and a collaborative environment for
neuroimaging software development in a high-level language. For
example, ArtifactDetect, a quality assurance tool maintained as a
Matlab-based SPM toolbox, is now available to FSL users and
appropriately modifies both SPM and FSL generated design matrices to
discard outliers.


Conclusion
----------

Nipype provides an environment for interactive manipulation of data
through a Python interface as well as for performing reproducible,
distributed analysis using the pipeline system and has a growing
developer and user community. Nipype has encouraged the scientific
exploration of different algorithms and associated parameters, eased
the development of workflows within and between packages and reduced
the learning curve associated with understanding the algorithms, APIs
and user interfaces of disparate packages. Future plans include
adding: interfaces to other analysis tools (e.g., AFNI, ANTS, Slicer),
a direct interface to the Nipy statistical analysis framework, the
ability to query data and workflows, a repository for workflows
(cf. myExperiment.org), and infrastructure for using Nipype as a
teaching tool.

