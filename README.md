# Optimization Tools and Exercises

## [SCIP Optimization Suite](https://www.scipopt.org)

SCIP is currently one of the fastest non-commercial solvers for mixed integer programming (MIP) and mixed integer nonlinear programming (MINLP). It is also a framework for constraint integer programming and branch-cut-and-price. It allows for total control of the solution process and the access of detailed information down to the guts of the solver. (https://www.scipopt.org)

  - Installation on Windows 10 (64-bit only)

    1. Download [SCIPOptSuite-7.0.2-win64-VS15.exe](https://www.scipopt.org/download.php?fname=SCIPOptSuite-7.0.2-win64-VS15.exe).
    2. Install by double click the icon of the file.
    3. Open `Advanced system settings(고급 시스템 설정)` in Windows 10 and click `Environment variables(환경 변수)` to add `C:\Program Files\SCIPOptSuite 7.0.2\bin` in the `Path` variable.

    

  - Installation on macOS 10.15 (without Homebrew)

    1. Download [SCIPOptSuite-7.0.2-Darwin-no-Ipopt.sh](https://www.scipopt.org/download.php?fname=SCIPOptSuite-7.0.2-Darwin-no-Ipopt.sh).
    
    2. Install the file on `/opt/SCIPOptSuite-7.0.2` by running the following comand.
       ```bash
       $ sudo bash SCIPOptSuite-7.0.2-Darwin-no-Ipopt.sh --prefix=/opt
       ```
       
    3. Make `gcg` work by modifying the  `LC_LOAD_DYLIB` command.
       ```bash
       $ sudo install_name_tool -change libscip.7.0.dylib @executable_path/../lib/libscip.7.0.dylib /opt/SCIPOptSuite-7.0.2-Darwin/bin/gcg
       ```
       
    <div class="alert alert-block alert-warning">
    <b>Warning:</b> 1. Notice that this installation does not work with PySCIPOpt.<br/>
      2. Neither `SCIPOptSuite-7.0.2-Darwin-Ipopt-gcc7.sh` nor `SCIPOptSuite-7.0.2-Darwin-Ipopt-gcc10.sh` does not work if the exact libraries were not installed using Homebrew.
    </div>

   


  - Installation on Windows Subsystem for Linux (e.g. openSUSE Leap 42 under Windows Subsystem for Linux)

    1. Download [SCIPOptSuite-6.0.0-Linux.sh](http://scip.zib.de/download.php?fname=SCIPOptSuite-6.0.0-Linux.sh)
    2. Install by running `sudo bash SCIPOptSuite-6.0.0-Linux.sh --prefix=/opt` and then `cd /opt && sudo ln -s SCIPOptSuite-6.0.0-Linux scip`
    3. Install the packages `liblapack3` and `libblas3` (in the case of openSUSE Leap 42, run `sudo zypper install liblapack3 libblas3`)

    > **Note:** In the case of Cent OS 7, you may need `patchelf` to adjust the ld path. You can install it by running `conda install patchelf` under Linux.



## [PySCIPOpt](https://github.com/SCIP-Interfaces/PySCIPOpt)

Python interface for the SCIP Optimization Suite

- Installation on Windows 10 (64-bit only)
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
       > pip install .
       > pytest
       ```



- Installation on macOS 10.15 (without Homebrew)
    1. Requirements:
      
       - [Miniconda Python 3](https://docs.conda.io/en/latest/miniconda.html) (Python 3.8 or 3.9, 64-bit)
       
    3. Run the following commands.
       ```bash
       > conda create -n scip pyscipopt -c conda-forge
       > conda activate scip
       ```




## [Google OR-Tools](https://developers.google.com/optimization/)

Google OR-Tools is an open source software suite for optimization, tuned for tackling the world's toughest    problems in vehicle routing, flows, integer and linear programming, and constraint programming. (https://developers.google.com/optimization)

  - Google Optimization Tools in GitHub (https://github.com/google/or-tools)
    1. Install [Miniconda Python 3](https://docs.conda.io/en/latest/miniconda.html) (Python 3.8 or 3.9, 64-bit)
    2. Install or-tools by running
    
       ```bash
       $ conda install absl-py protobuf
       $ pip install ortools
       ```


