# Intro

![GitHub](https://img.shields.io/github/license/guanhuaw/mirtorch) 
![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/guanhuaw/mirtorch?include_prereleases)
![Read the Docs](https://img.shields.io/readthedocs/mirtorch)

A Py***Torch***-based differentiable ***I***mage ***R***econstruction ***T***oolbox, developed at the University of ***M***ichigan.

The work is inspired by [MIRT](https://github.com/JeffFessler/mirt), a well-acclaimed toolbox for medical imaging reconstruction. 

The overarching goal is to provide fast iterative and data-driven image reconstruction across CPUs and GPUs. Researchers can rapidly develop new model-based and learning-based methods (i.e., unrolled neural networks) with its convenient abstraction layers. With the full support of auto-differentiation, one may optimize imaging protocols and image reconstruction parameters with gradient methods.

Documentation: https://readthedocs.org/projects/mirtorch/

### Installation

We recommend to pre-install `PyTorch` first.
To install the `MIRTorch` package, after cloning the repo, please try `pip install -e .` 

`requirements.txt` details the package dependencies. 

### Features

#### Linear maps

The `LinearMap` class overloads common matrix operations, such as `+, - , *`. It also supports an efficient backpropagation.

Instances include basic linear operations (like con\volution), classical imaging processing, and MRI system matrix (Cartesian and Non-Cartesian, sensitivity- and B0-informed system models). More is on the way...

Since the Jacobian matrix of a linear operator is itself, the toolbox may actively calculate such Jacobians during backpropagation, avoiding the large cache cost required by auto-differentiation.

#### Proximal operators

The toolbox contains common proximal operators such as soft thresholding. These operators also support the regularizers that involve multiplication with diagonal or unitary matrices, such as orthogonal wavelets.

#### Iterative reconstruction (IR) algorithms

Currently, the package includes the conjugate gradient (CG), FISTA, and POGM algorithms for image reconstruction.

#### Dictionary learning

For dictionary learning-based reconstruction, we implemented an efficient dictionary learning algorithm (SOUP-DIL) and orthogonal matching pursuit (OMP). Due to PyTorch’s limited support of sparse matrices, we use SciPy as the backend. 

### Basic usage

#### MRI reconstruction: 

`/example` includes SENSE, Non-Cartesian SENSE, and **B0**-informed reconstruction with penalized weighted least squares (*PWLS*), compressed sensing (CS), and dictionary learning (DL) methods.

#### MRI sampling pattern optimization:

`/example/demo_mri_traj.ipynb` contains MRI sampling pattern optimization examples. One may use the reconstruction loss as objective function to jointly optimize reconstruction algorithms and the sampling pattern.

### Acknowledgments

This work is inspired by (but not limited to):

SigPy: https://github.com/mikgroup/sigpy

MIRT/MIRT.jl: https://web.eecs.umich.edu/~fessler/code/index.html

PyLops: https://github.com/PyLops/pylops