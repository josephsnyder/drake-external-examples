autopybind11_add_module(symbolic_module
  YAML_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/wrapper_input.yml
  CONFIG_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/config.yml
  DESTINATION ${CMAKE_CURRENT_BINARY_DIR}
  LINK_LIBRARIES drake::drake
  C_STD_FLAG "-std=c++1z")

file(
  COPY _symbolic_extra.py
  DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
file(GENERATE
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/__init__.py
  CONTENT "from .symbolic_module import *
from ._symbolic_extra import *")
