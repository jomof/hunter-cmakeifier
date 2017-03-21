cmake_minimum_required(VERSION 3.0.2)
set(CMAKE_VERBOSE_MAKEFILE on)
set(HUNTER_STATUS_DEBUG on)

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.16.15.tar.gz"
    SHA1 "6974c2150fc0d3b09de3ad1efcbf15d360647ffa"
)

set(pkg "freetype")
set(PKG "FREETYPE")
set(RELATIVE_INCLUDE "include/freetype2")

project(example_project)
hunter_add_package(${pkg})
find_package(freetype 2.6.2 CONFIG REQUIRED)
add_library(example SHARED example.cpp)
target_link_libraries(example freetype::freetype)

message("HUNTER_${pkg}_VERSION=${HUNTER_${pkg}_VERSION}")
message("${PKG}_ROOT=${${PKG}_ROOT}")
message("Expected library: ${${PKG}_ROOT}/lib/lib${pkg}.a")
if (CMAKE_LIBRARY_OUTPUT_DIRECTORY)
  file(COPY ${${PKG}_ROOT}/lib/lib${pkg}.a DESTINATION ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})
  file(COPY "${${PKG}_ROOT}/${RELATIVE_INCLUDE}/" DESTINATION ${CMAKEIFY_REDIST_INCLUDE_DIRECTORY})
else()
  get_cmake_property(_variableNames VARIABLES)
  foreach (_variableName ${_variableNames})
    message(STATUS "${_variableName}=${${_variableName}}")
  endforeach()
endif()
