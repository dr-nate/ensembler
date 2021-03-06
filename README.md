Ensembler
=========

[![Anaconda Cloud](https://anaconda.org/omnia/ensembler/badges/version.svg)](https://anaconda.org/omnia/ensembler)
[![Documentation Status](https://readthedocs.org/projects/ensembler/badge/?version=latest)](http://ensembler.readthedocs.org/en/latest/)
[![Build Status](https://travis-ci.org/choderalab/ensembler.svg?branch=master)](https://travis-ci.org/choderalab/ensembler)

Software pipeline for automating omics-scale protein modeling and simulation setup.

Online documentation
--------------------
* Go to the [official online documentation](http://ensembler.readthedocs.org/).
* Read a preprint of the paper [on bioRxiv](http://dx.doi.org/10.1101/018036).
* See the example dataset from [modeling all human tyrosine kinases](http://datadryad.org/review?doi=doi:10.5061/dryad.7fg32).

Authors
-------

* Daniel L. Parton | daniel.parton@choderalab.org
* John D. Chodera | john.chodera@choderalab.org
* Patrick B. Grinaway | patrick.grinaway@choderalab.org

Overview of pipeline
--------------------

1. Retrieve protein target sequences and template structures.
2. Build models by mapping each target sequence onto every available template structure, using [Modeller](http://salilab.org/modeller/).
3. Filter out non-unique models (based on a RMSD cutoff).
4. Refine models with implicit solvent molecular dynamics simulation.
5. Refine models with explicit solvent molecular dynamics simulation.
6. (_optional_) Package and/or compress the final models, ready for transfer or for set-up on other platforms such as [Folding@Home](http://folding.stanford.edu/).

Installation
------------

First go to the [Modeller website](http://salilab.org/modeller/) and get a license key (registration required; free for academic non-profit institutions).

Save the key as an environment variable:

```bash
export KEY_MODELLER=XXX
```
Then, using [`conda`](http://conda.pydata.org/docs/) (installs all dependencies except the optional dependency [Rosetta](https://www.rosettacommons.org/software)):
```bash
conda config --add channels omnia
conda config --add channels salilab
conda install ensembler
```
From source:
```bash
git clone https://github.com/choderalab/ensembler.git
cd ensembler
python setup.py install
```

Dependencies
------------

* OpenMM - https://simtk.org/home/openmm
* Modeller - http://salilab.org/modeller/
* mdtraj - http://mdtraj.org/
* MSMBuilder - http://msmbuilder.org/
* PDBFixer - https://github.com/pandegroup/pdbfixer
* BioPython
* NumPy
* lxml
* PyYAML
* docopt
* mock
* Optional:
  * Rosetta (optional, for template loop reconstruction) - https://www.rosettacommons.org/software
  * MPI4Py (allows many Ensembler functions to be run in parallel using MPI)
  * Pandas (required for certain analysis functions)
  * subprocess32 (if using Python 2)
  * PyMOL (optional, for model alignment/visualization) - http://www.pymol.org/

Recommended approach is to install using conda (https://store.continuum.io/cshop/anaconda/). This will install all dependencies except for the optional dependency Rosetta, which must be installed separately by the user.
