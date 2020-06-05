
autopybind11_add_module(common YAML_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/wrapper_input.json
                                  DESTINATION ${CMAKE_CURRENT_BINARY_DIR}
                                  LINK_LIBRARIES drake::drake
                       )
