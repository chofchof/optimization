# Optimization Tools and Exercises

## [Google Optimization Tools](https://developers.google.com/optimization/)

Google Optimization Tools (OR-Tools) is a fast and portable software suite for solving combinatorial optimization problems.

  - [or-tools](https://github.com/google/or-tools) - Google's Operations Research tools in GitHub

    1. Install [Anaconda Python 3.6 or 3.7](https://www.anaconda.com/download/)
    2. Open a conda prompt
    3. Install or-tools 6.8 by running `pip install ortools`

## [SCIP Optimization Suite](http://scip.zib.de/)

SCIP is currently one of the fastest non-commercial solvers for mixed integer programming (MIP) and mixed integer nonlinear programming (MINLP). It is also a framework for constraint integer programming and branch-cut-and-price. It allows for total control of the solution process and the access of detailed information down to the guts of the solver.

  - Installation on Mac OS X 10.13.6
  
    1. Download [SCIPOptSuite-6.0.0-Darwin.dmg](http://scip.zib.de/download.php?fname=SCIPOptSuite-6.0.0-Darwin.dmg)
    2. Open `SCIPOptSuite-6.0.0-Darwin.dmg` and copy the three directories, `bin`, `include`, and `lib` into some place (e.g., `sudo mkdir -p /opt/scip` and then `sudo cp -R /Volumes/SCIPOptSuite-6.0.0-Darwin/bin /Volumes/SCIPOptSuite-6.0.0-Darwin/include /Volumes/SCIPOptSuite-6.0.0-Darwin/lib /opt/scip`)
    3. Assume Anaconda Python is already installed on `/opt/conda`
    4. Change the dyld path as follows: (Repeat the same process for `soplex` and `zimpl` as well as `/opt/scip/lib/libscip.6.0.0.0.dylib`)
```
    $ cd /opt/scip/bin
    $ otool -L scip (shows the current dyld path)
    scip:
            /usr/local/opt/gmp/lib/libgmp.10.dylib (...)
            /usr/local/opt/gmp/lib/libgmpxx.4.dylib (...)
            ...
    $ sudo install_name_tool -change /usr/local/opt/gmp/lib/libgmp.10.dylib /opt/conda/lib/libgmp.10.dylib scip
    $ sudo install_name_tool -change /usr/local/opt/gmp/lib/libgmpxx.4.dylib /opt/conda/lib/libgmpxx.4.dylib scip 
    $ otool -L scip (checks whether the dyld path was changed properly)
    scip:
            /opt/conda/lib/libgmp.10.dylib (...)
            /opt/conda/lib/libgmpxx.4.dylib (...)
            ...
    $ scip (checks whether it works)
    SCIP version 6.0.0 ...
```

  - Installation on Linux (e.g. openSUSE Leap 42 under Windows Subsystem for Linux)
  
    1. Download [SCIPOptSuite-6.0.0-Linux.sh](http://scip.zib.de/download.php?fname=SCIPOptSuite-6.0.0-Linux.sh)
    2. Install by running `sudo bash SCIPOptSuite-6.0.0-Linux.sh --prefix=/opt` and then `cd /opt && sudo ln -s SCIPOptSuite-6.0.0-Linux scip`
    3. Install the packages `liblapack3` and `libblas3` (in the case of openSUSE Leap 42, run `sudo zypper install liblapack3 libblas3`)
    
    > **Note:** In the case of Cent OS 7, you may need `patchelf` to adjust the ld path. You can install it by running `conda install patchelf` under Linux.

  - [PySCIPOpt](https://github.com/SCIP-Interfaces/PySCIPOpt) - Python interface for the SCIP Optimization Suite
  
    1. Install [Anaconda Python 3.6](https://www.anaconda.com/download/)
    2. Install [SCIP 6.0.0](http://scip.zib.de/#download)
    3. Open a conda prompt and run `conda activate`
    4. Check that `cython` is already installed by running `conda list | grep cython`. Otherwise, run `conda install cython`
    5. Set the environment variable `export SCIPOPTDIR=/opt/scip` (Linux & Mac OS X) (See [INSTALL.rst](https://github.com/SCIP-Interfaces/PySCIPOpt/blob/master/INSTALL.rst) for more details)
    6. Install PySCIPOpt 2.0.0 by running `pip install pyscipopt`
    7. How to check whether PySCIPOPt 2.0.0 is installed properly.
      - Mac OS X: `DYLD_LIBRARY_PATH=/opt/scip/lib; ipython -c 'import pyscipopt'` or `export DYLD_LIBRARY_PATH=/opt/scip/lib`
      - Linux: `LD_LIBRARY_PATH=/opt/scip/lib; ipython -c 'import pyscipopt'` or `export LD_LIBRARY_PATH=/opt/scip/lib`
    8. (**Optional:** Mac OS X) Change the dyld path directly:
```
    $ cd /opt/conda/lib/python3.6/site-packages/pyscipopt
    $ otool -L scip.cpython-36m-darwin.so (shows the current dyld path)
    scip.cpython-36m-darwin.so:
	          libscip.6.0.dylib (...)
            ...
    $ sudo install_name_tool -change libscip.6.0.dylib /opt/scip/lib/libscip.6.0.dylib scip.cpython-36m-darwin.so
    $ otool -L scip.cpython-36m-darwin.so (checks whether the dyld path was changed properly)
    scip.cpython-36m-darwin.so:
	          /opt/scip/lib/libscip.6.0.dylib (...)
            ...
    $ ipython -c 'import pyscipopt' (checks whether it works)
```
