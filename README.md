# Optimization Tools and Exercises



## [SCIP Optimization Suite](https://www.scipopt.org) and [PySCIPOpt](https://github.com/SCIP-Interfaces/PySCIPOpt)

**SCIP** is currently one of the fastest non-commercial solvers for mixed integer programming (MIP) and mixed integer nonlinear programming (MINLP). It is also a framework for constraint integer programming and branch-cut-and-price. It allows for total control of the solution process and the access of detailed information down to the guts of the solver. (https://www.scipopt.org)

**PySCIPOpt** is a Python interface for the SCIP Optimization Suite.



### Installation on Linux and macOS with Anaconda

1. Install [Miniconda Python 3](https://docs.conda.io/en/latest/miniconda.html) (Python 3.8 or 3.9, 64-bit).

2. Create a Python virtual environment and install `pyscipopt` and `scip`.
   ```bash
   $ conda create -n scip pyscipopt -c conda-forge
   $ conda activate scip
   $ conda config --add channels conda-forge --env
   ```
   It is also possible to install `soplex`, `zimpl`, and `gcg` using the conda-forge channel.



### Installation on Windows 10 (64-bit only)

#### A. SCIPOptSuite-7.0.2

1. Download [SCIPOptSuite-7.0.2-win64-VS15.exe](https://www.scipopt.org/download.php?fname=SCIPOptSuite-7.0.2-win64-VS15.exe).

2. Install by double click the icon of the file.

3. Open `Advanced system settings(고급 시스템 설정)` in Windows 10 and click `Environment variables(환경 변수)` to add `C:\Program Files\SCIPOptSuite 7.0.2\bin` in the `Path` variable.

#### B. PySCIPOpt-3.1.1

1. Requirements:
   - [Miniconda Python 3](https://docs.conda.io/en/latest/miniconda.html) (Python 3.8 or 3.9, 64-bit)

2. Download one of the following wheels.
   - [`PySCIPOpt-3.1.1-cp38-cp38-win_amd64.whl`](https://github.com/chofchof/optimization/raw/master/wheels/PySCIPOpt-3.1.1-cp38-cp38-win_amd64.whl) (Python 3.8)
   - [`PySCIPOpt-3.1.1-cp39-cp39-win_amd64.whl`](https://github.com/chofchof/optimization/raw/master/wheels/PySCIPOpt-3.1.1-cp39-cp39-win_amd64.whl) (Python 3.9)

3. Run the following commands from the command prompt.
   ```bash
   > conda create -n scip python=3.8 # or python=3.9
   > conda activate scip
   ```

#### C. (Optional) Make PySCIPOpt-3.1.1 wheel

1. Requirements:
   - [Miniconda Python 3](https://docs.conda.io/en/latest/miniconda.html) (Python 3.8 or 3.9, 64-bit)
   - `SCIPOptSuite-7.0.2` (see above)
   - [Build Tools for Visual Studio 2019](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) (Visual C++ build tools only)

2. Download [`PySCIPOpt-3.1.1.zip`](https://github.com/scipopt/PySCIPOpt/archive/refs/tags/v3.1.1.zip) (https://github.com/scipopt/PySCIPOpt/releases) and extract the file.

3. Run the following commands from the command prompt.
   ```bash
   > conda create -n scip cython pytest
   > conda activate scip
    
   > cd PySCIPOpt-3.1.1
   > set SCIPOPTDIR="C:\Program Files\SCIPOptSuite 7.0.2"
   > pip wheel . # or pip install .
   > pytest
   ```



## [Google OR-Tools](https://developers.google.com/optimization/)

Google OR-Tools is an open source software suite for optimization, tuned for tackling the world's toughest    problems in vehicle routing, flows, integer and linear programming, and constraint programming. (https://developers.google.com/optimization)

### Google Optimization Tools in GitHub (https://github.com/google/or-tools)

1. Install [Miniconda Python 3](https://docs.conda.io/en/latest/miniconda.html) (Python 3.8 or 3.9, 64-bit)

2. Install or-tools by running
   ```bash
   $ conda activate scip
   $ conda install absl-py protobuf
   $ pip install ortools
   ```
