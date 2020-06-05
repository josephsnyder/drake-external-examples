autopybind11_add_module(autodiffutils YAML_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/wrapper_input.json
                                  DESTINATION ${CMAKE_CURRENT_BINARY_DIR}
                                  CONFIG_INPUT ${CMAKE_CURRENT_SOURCE_DIR}/config.yml
                                  LINK_LIBRARIES drake::drake
                                  C_STD_FLAG "-std=c++1z"
                       )
#target_sources(autodiffutils PUBLIC autodiffutils_py.cc)
#pybind11_add_module(autodiffutils autodiffutils_py.cc)
#target_link_libraries(autodiffutils PUBLIC drake::drake)
#target_include_directories(autodiffutils PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

