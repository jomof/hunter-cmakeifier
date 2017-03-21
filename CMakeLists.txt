cmake_minimum_required(VERSION 3.0.2)
include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.16.15.tar.gz"
    SHA1 "6974c2150fc0d3b09de3ad1efcbf15d360647ffa"
)
#set(pkg "SDL2")
set(pkg "freetype")
project(example_project)
hunter_add_package(${pkg})
file(COPY ${${pkg}_ROOT}/lib/*.a DESTINATION ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})




