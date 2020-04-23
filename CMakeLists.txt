if("x${CMAKE_SOURCE_DIR}" STREQUAL "x${CMAKE_BINARY_DIR}")
  message(FATAL_ERROR "\
In-source build is not a good practice.
Please use:
  mkdir build
  cd build
  cmake ..
to build this project"
  )
endif()

cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

project(k2)

option(BUILD_SHARED_LIBS "Whether to build shared or static lib" ON)

set(k2_THIRD_PARTY_DIR "${CMAKE_BINARY_DIR}/third_party" CACHE STRING
  "Directory to save & build downloaded third party libraries"
)

enable_testing()

list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake)
include(googletest)
include(cpplint)

add_subdirectory(k2)