# Optimization Tools and Exercises

## [Google Optimization Tools](https://developers.google.com/optimization/)

Google Optimization Tools (OR-Tools) is a fast and portable software suite for solving combinatorial optimization problems.

  - [or-tools](https://github.com/google/or-tools) - Google's Operations Research tools in GitHub

    1. Install [Anaconda Python 3.6 or 3.7](https://www.anaconda.com/download/)
    2. Open a conda prompt
    3. Install or-tools 6.8 by running `pip install ortools`

## [SCIP Optimization Suite](http://scip.zib.de/)

SCIP is currently one of the fastest non-commercial solvers for mixed integer programming (MIP) and mixed integer nonlinear programming (MINLP). It is also a framework for constraint integer programming and branch-cut-and-price. It allows for total control of the solution process and the access of detailed information down to the guts of the solver.

  - [PySCIPOpt](https://github.com/SCIP-Interfaces/PySCIPOpt) - Python interface for the SCIP Optimization Suite
  
    1. Install [Anaconda Python 3.6 or 3.7](https://www.anaconda.com/download/)
    2. Install [SCIP 6.0.0](http://scip.zib.de/#download)
    3. Open a conda prompt
    4. Set the environment variable `export SCIPOPTDIR=<path_to_install_dir>` (Linux & Mac OS X) (See [INSTALL.rst](https://github.com/SCIP-Interfaces/PySCIPOpt/blob/master/INSTALL.rst) for more details)
    5. Install PySCIPOpt 2.0.0 by running `pip install pyscipopt`
