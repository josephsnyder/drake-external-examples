# CMake Project with an Installed Drake

This uses the CMake `find_package(drake)` mechanism to find an installed instance of Drake.

# Instructions

These instructions are only supported for Ubuntu 18.04 (Bionic).

```shell
###############################################################
# Install Prerequisites
###############################################################
# Various system dependencies
sudo ../scripts/setup/linux/ubuntu/bionic/install_prereqs

# (Optionally) Install GTest
# You could also explicitly pull gtest into the CMake build directly:
#     https://github.com/google/googletest/tree/master/googletest
sudo apt-get install libgtest-dev
ls
mkdir ~/gtest && cd ~/gtest && cmake /usr/src/gtest && make
sudo cp *.a /usr/local/lib

###############################################################
# Install Drake to /opt/drake
###############################################################

# 1) A specific version (date-stamped)
# curl -O https://drake-packages.csail.mit.edu/drake/nightly/drake-20191015-bionic.tar.gz

# 2) The latest (usually last night's build)
curl -O https://drake-packages.csail.mit.edu/drake/nightly/drake-latest-bionic.tar.gz
sudo tar -xvzf drake-latest-bionic.tar.gz -C /opt

# 3) Manual Installation
# git clone https://github.com/RobotLocomotion/drake.git
# (mkdir drake-build && cd drake-build && cmake -DCMAKE_INSTALL_PREFIX=/opt/drake ../drake && make)

# 4) Manual Installation w/ Licensed Gurobi
# Install & setup gurobi (http://drake.mit.edu/bazel.html?highlight=gurobi#install-on-ubuntu)
# git clone https://github.com/RobotLocomotion/drake.git
# (mkdir drake-build && cd drake-build && cmake -DCMAKE_INSTALL_PREFIX=/opt/drake -DWITH_GUROBI=ON ../drake && make)

# Install AutoPyBind11
################################################################

Install the AutoPyBind11 program from:

 https://gitlab.kitware.com/autopybind11/autopybind11

* Optional: Create Python3 virtual environment 
* pip install AutoPyBind11
  * cd to autopybind11
  * python3 -m pip install .

# Configure and Build:

cd drake_cmake_bindings
mdkir build 
cd build 
cmake -D AutoPyBind11_DIR=<path/to>/autopybind11 ..



# Execute Tests:

Remove existing download's version of pydrake
  * mv /opt/drake/lib/python3.6/site-packages/pydrake /opt/drake/lib/python3.6/site-packages/pydrake.old
Symbolically link the build/pydrake directory to the above location
 * ln -s <path/to>/drake_cmake_bindings/build/pydrake /opt/drake/lib/python3.6/site-packages/pydrake

Add that directory to python path and execute tests
 * PYTHONPATH="/opt/drake/lib/python3.6/site-packages/" python3 <test_script>
