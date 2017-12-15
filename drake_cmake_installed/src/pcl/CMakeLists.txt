# -*- mode: cmake -*-
# vi: set ft=cmake :

##############################################################################
# Copyright (c) 2017, Toyota Research Institute.
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
# * Redistributions of source code must retain the above copyright notice, this
#   list of conditions and the following disclaimer.
#
# * Redistributions in binary form must reproduce the above copyright notice,
#   this list of conditions and the following disclaimer in the documentation
#   and/or other materials provided with the distribution.
#
# * Neither the name of the Massachusetts Institute of Technology nor the names
#   of its contributors may be used to endorse or promote products derived from
#   this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE MASSACHUSETTS INSTITUTE OF TECHNOLOGY AND
# CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT
# NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
# PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE MASSACHUSETTS
# INSTITUTE OF TECHNOLOGY OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
# INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA,
# OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
# LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
# NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE,
# EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
##############################################################################

# Important Caveat: This must come after any call to
#   find_package(drake)
# so that Drake's version of the bundled Eigen will be used.
find_package(PCL CONFIG REQUIRED)
# Work around https://bugs.launchpad.net/ubuntu/+source/vtk6/+bug/1573234
# by removing the missing vtkproj4 library from the list of needed files.
# It's not actually needed for this example.
list(REMOVE_ITEM PCL_LIBRARIES "vtkproj4")

include_directories(${PCL_INCLUDE_DIRS})
add_executable(simple_pcl_example simple_pcl_example.cc)
target_link_libraries(simple_pcl_example drake::drake ${PCL_LIBRARIES})