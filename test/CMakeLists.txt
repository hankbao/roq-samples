cmake_minimum_required(VERSION 3.0)

project(test)

add_executable(roq-samples-test
  main.cpp
)

set_target_properties(roq-samples-test PROPERTIES
  COMPILE_DEFINITIONS ROQ_SPDLOG
)

target_include_directories(roq-samples-test PUBLIC
  ${ROQ_INCLUDE_DIR}
  ${CROSSGUID_INCLUDE_DIR}
  ${FLATBUFFERS_INCLUDE_DIR}
  ${GFLAGS_INCLUDE_DIR}
  ${LIBEVENT_INCLUDE_DIR}
  ${LIBUNWIND_INCLUDE_DIR}
  ${SPDLOG_INCLUDE_DIR}
)

target_link_libraries(roq-samples-test
  ${CMAKE_THREAD_LIBS_INIT}
  ${ROQ_LIBS}
  ${CROSSGUID_LIBS}
  ${FLATBUFFERS_LIBS}
  ${GFLAGS_LIBS}
  ${LIBEVENT_LIBS}
  ${LIBUNWIND_LIBS}
  ${SPDLOG_LIBS}
  utilities
  gtest_main
)

add_test (NAME roq-samples-test COMMAND roq-samples-test)
