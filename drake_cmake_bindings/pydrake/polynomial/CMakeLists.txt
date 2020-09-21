autopybind11_add_module(polynomial_module
  YAML_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/wrapper_input.yml
  CONFIG_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/config.yml
  DESTINATION ${CMAKE_CURRENT_BINARY_DIR}
  LINK_LIBRARIES drake::drake common_module symbolic_module # autodiffutils_module
  C_STD_FLAG "-std=c++1z")

file(GENERATE
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/__init__.py
  CONTENT "from .polynomial_module import *")
