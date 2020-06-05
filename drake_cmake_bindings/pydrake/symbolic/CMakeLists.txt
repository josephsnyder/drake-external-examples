
autopybind11_add_module(symbolic YAML_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/wrapper_input.json
                                  DESTINATION ${CMAKE_CURRENT_BINARY_DIR}
                                  LINK_LIBRARIES drake::drake
                                  C_STD_FLAG "-std=c++1z"
                       )
