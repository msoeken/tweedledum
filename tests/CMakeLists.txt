# Distributed under the MIT License (See accompanying file /LICENSE)
# Author(s): Bruno Schmitt
# CMake build : tweedledum library tests
add_compile_options(
  -fno-rtti
  -W
  -Wall
  -pedantic)

include_directories(catch2)

#  All Tests
#  =============================================================================
add_custom_target(tweedledum_tests COMMENT "Build all tests.")

set(tweedledum_tests_files
  "${CMAKE_CURRENT_SOURCE_DIR}/run_tests.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/decomposition/barenco.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/decomposition/dt.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/synthesis/cnot_patel.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/synthesis/dbs.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/synthesis/esop_phase_synth.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/synthesis/gray_synth.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/synthesis/linear_synth.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/synthesis/stg.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/algorithms/synthesis/tbs.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/gates/mcst_gate.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/io/qasm.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/io/quil.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/io/write_projectq.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/io/write_qpic.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/networks/gg_network.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/networks/netlist.cpp"
  )

add_executable(run_tests "${tweedledum_tests_files}")
target_link_libraries(run_tests tweedledum)
add_dependencies(tweedledum_tests run_tests)
