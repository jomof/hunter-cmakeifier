cmake_minimum_required(VERSION 3.0.2)
include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.16.15.tar.gz"
    SHA1 "6974c2150fc0d3b09de3ad1efcbf15d360647ffa"
)
project(example_project)
hunter_add_package(SDL2)
find_package(SDL2 CONFIG REQUIRED)
file(COPY ${SDL2_DIR}/lib/libSDL2.a DESTINATION ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})


