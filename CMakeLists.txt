cmake_minimum_required(VERSION 3.0.2)
include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.16.15.tar.gz"
    SHA1 "6974c2150fc0d3b09de3ad1efcbf15d360647ffa"
)
#set(pkg "SDL2")
set(pkg "freetype")
set(PKG "FREETYPE")
project(example_project)
hunter_add_package(${pkg})
message("${PKG}_VER=${${PKG}_VER}")
message("${PKG}_ROOT=${${PKG}_ROOT}")
message("Expected library: ${${PKG}_ROOT}/lib/lib${pkg}.a")
if (CMAKE_LIBRARY_OUTPUT_DIRECTORY)
  file(COPY ${${PKG}_ROOT}/lib/lib${pkg}.a DESTINATION ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})
endif()




