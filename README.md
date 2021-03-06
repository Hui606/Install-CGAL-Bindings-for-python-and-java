# Install-CGAL-Bindings-for-python-and-java
To introduce how to install cgal-swig-bindings **WITHOUT** using `pip install cgal-bindings`

**PS:** Using `pip install cgal-bindings` to install cgal-bindings will fail as the current version of cgal is too new (CGAL 5.0.2) to support the binding from pip. Details in: https://github.com/CGAL/cgal-swig-bindings/issues/153#issuecomment-587064408

My computer is MacOS with python 2.7

## 1. Install CGAL liabray
I highly recommend using Homebrew:https://brew.sh/  \
Firstly, open mac terminal and type in `brew install cgal`. 

## 2. Install CGAL-bindings
CGAL is designed for __C++__. To use it in __Python__ or __Java__, we need CGAL-bindings to import CGAL in the programs.

In this step, using the commands listed in the bottom of this page: https://github.com/CGAL/cgal-swig-bindings/wiki/Installation, but changed a little, which goes
  ```
  git clone https://github.com/cgal/cgal-swig-bindings
  cd cgal-swig-bindings
  mkdir build
  mkdir build/CGAL-5.0_release
  cd build/CGAL-5.0_release
  cmake -DCGAL_DIR=/usr/lib/CGAL -DBUILD_JAVA=OFF -DPYTHON_OUTDIR_PREFIX=../../examples/python ../..
  make -j 4
  cd ../../examples/python
  python test.py
  ... output of the example test.py...`
  ```

The above code is for __Python__ usage. If __Java__, just copy the code in that link.

## 3. If missing library
When installing CGAL, you may receive errors indicating what packages are needed, something like `You are missing gmp library`. In my case, four packages: boost, cgal, gmp, mpfr. To handle them, using `brew install <library name>`(e.g. `brew install gmp`)

## 4. Customize project path
If you want to put the CGAL-bindings where rather than default path, here it is:
   - git clone 'link' 'path' (be sure the path is "brand new" (non-exist before))\
   __e.g.__ `git clone https://github.com/cgal/cgal-swig-bindings /Users/mike/Documents/CGAL-Project/cgal-bindings`
   
   - enter the folder\
   `cd /Users/mike/Documents/CGAL-Project/cgal-bindings` 
   
   - make 'build' folder and enter it\
   `mkdir build/CGAL-5.0_release`\
   `cd build/CGAL-5.0_release`
   
   - cmake\
   ```cmake -DCGAL_DIR=/usr/lib/CGAL -DBUILD_JAVA=OFF -DPYTHON_OUTDIR_PREFIX=../../examples/python/mike../..```\
   **Note:** for `-DPYTHON_OUTDIR_PREFIX=../../examples/python/mike../..` this path is where you put your python file. After this, you will also see a CGAL package in folder `mike`
   
   - make\
   `make -j 4`\
   Explaination for '-j': Specifies the number of jobs (commands) to run simultaneously. If there is more than one -j option, the last one is effective. If the -j option is given without an argument, make will not limit the number of jobs that can run simultaneously. https://www.tutorialspoint.com/unix_commands/make.htm
   
   - you can run your python file in `/Users/mike/Documents/CGAL-Project/cgal-bindings/examples/python/mike`
   
