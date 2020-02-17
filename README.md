# Install-CGAL-Bindings-for-python
To introduce how to install cgal-swig-bindings for python and java

My computer is MacOS with python 3.7

## 1. Install CGAL Liabray
To do this, I highly recommend using Homebrew:https://brew.sh/  \
Firstly, open mac terminal and type in `brew install cgal`. 

## 2. Install CGAL-bindings
In this step, using the commands listed in the bottom of this page: https://github.com/CGAL/cgal-swig-bindings/wiki/Installation, but changed a little, which goes
  ```
  git clone https://github.com/cgal/cgal-swig-bindings
  cd cgal-swig-bindings
  mkdir build/CGAL-5.0_release -p
  cd build/CGAL-5.0_release
  cmake -DCGAL_DIR=/usr/lib/CGAL -DBUILD_JAVA=OFF -DPYTHON_OUTDIR_PREFIX=../../examples/python ../..
  make -j 4
  cd ../../examples/python
  python test.py
  ... output of the example test.py...`
  ```

__Note:__ for this line `mkdir build/CGAL-5.0_release -p` is used for create two folders: "CGAL-5.0_release" inside "build". But I couldn't create the folders so I create it manually. 

The above code is for __Python__ usage. If __Java__, you can just copy the code in that link.

## 3. If missing libraries
When installing CGAL, you may receive errors tell you what packages are needed, something like `You are missing gmp library`. In my case, four packages: boost, cgal, gmp, mpfr. To handle them, using `brew install <library name>`(e.g. `brew install gmp`)
